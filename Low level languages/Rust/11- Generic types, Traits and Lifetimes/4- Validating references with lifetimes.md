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

```
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
