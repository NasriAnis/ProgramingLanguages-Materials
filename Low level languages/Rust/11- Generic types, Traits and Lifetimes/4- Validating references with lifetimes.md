Lifetimes are another kind of generic that we’ve already been using. Rather than ensuring that a type has the behavior we want, lifetimes ensure that references are valid as long as we need them to be.

### Dangling References
The main aim of lifetimes is to prevent dangling references, which, if they were allowed to exist, would cause a program to reference data other than the data it’s intended to reference.

```
fn main() {
    let r;

    {
        let x = 5;
        r = &x;
    }

    println!("r: {r}");
} //  this will result into an error
```

### The Borrow checker
The Rust compiler has a _borrow checker_ that compares scopes to determine whether all borrows are valid.

```rust
fn main() {
    let r;                // ---------+-- 'a
                          //          |
    {                     //          |
        let x = 5;        // -+-- 'b  |
        r = &x;           //  |       |
    }                     // -+       |
                          //          |
    println!("r: {r}");   //          |
}                         // ---------+
```

### Generic lifetimes in Functions

looking at this function :

```rust
fn main() {
    let string1 = String::from("abcd");
    let string2 = "xyz";

    let result = longest(string1.as_str(), string2);
    println!("The longest string is {result}");
}

fn longest(x: &str, y: &str) -> &str { // complain about lifetime anotation
    if x.len() > y.len() { x } else { y }
}
```

Rust will complain The compiler doesn't know **which reference** the returned `&str` comes from — `x` or `y`. And since the function can return either depending on runtime logic, it can't figure out how long the returned reference is valid. It's essentially asking: _"If I return this `&str`, whose lifetime does it borrow from?"_ 

so it cant know how to check for lifetime (either for x or y) so the fix is :

### Lifetime Annotation

the syntax is : The names of lifetime parameters must start with an apostrophe (`'`) and are usually all lowercase and very short, like generic types. Most people use the name `'a` for the first lifetime annotation. We place lifetime parameter annotations after the `&` of a reference, using a space to separate the annotation from the reference’s type.
```rust
&i32        // a reference
&'a i32     // a reference with an explicit lifetime
&'a mut i32 // a mutable reference with an explicit lifetime
```

in function signature it would look like this :
```rust
fn main() {
    let string1 = String::from("abcd");
    let string2 = "xyz";

    let result = longest(string1.as_str(), string2);
    println!("The longest string is {result}");
}

fn longest<'a>(x: &'a str, y: &'a str) -> &'a str {
    if x.len() > y.len() { x } else { y }
}
```

We want the signature to express the following constraint: The returned reference will be valid as long as both of the parameters are valid. This is the relationship between lifetimes of the parameters and the return value. We’ll name the lifetime `'a` and then add it to each reference.

in short : `'a` means: _"the returned reference will live at least as long as the shorter of `x` and `y`."_

This is invalid :
```rust
let result;
{
    let string2 = String::from("xyz");
    result = longest("abcd", string2.as_str());
    // string2 dropped here
}
println!("{result}"); // DANGER: result might point to freed memory
```

