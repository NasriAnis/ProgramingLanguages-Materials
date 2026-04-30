A reference is like a pointer, we use the `&` operator to create a reference that doesn't on the original one :

```
fn main() {
    let s1 = String::from("hello");

    let len = calculate_length(&s1); // pass a reference

    println!("The length of '{s1}' is {len}."); // can be used there
}

fn calculate_length(s: &String) -> usize { // function signature takes a reference
    s.len()
} // Here, s goes out of scope. But because s does not have ownership of what
  // it refers to, the String is not dropped.
```

A diagram of `&String` `s` pointing at `String` `s1` :

![](../../../../zzDocument/Pasted%20image%2020260430082424.png)

We call the action of creating a reference _borrowing_ in addition Just as variables are immutable by default, so are references. We’re not allowed to modify something we have a reference to. (unless we use mutable references)