To define a function in the context of a struct we use the `impl` keyword followed the Struct name, Everything inside the `impl` is defined in the context of one Struct type. We then declare a function inside the `impl`.

Inside the function signature we use `self`, methods should have as first parameter `&self` short for `self: &Self`. Within an `impl` block, the type `Self` is an alias for the type that the `impl` block is for. (If we wanted to change the instance that we’ve called the method on as part of what the method does, we’d use `&mut self` as the first parameter.)

We then access the method using the `method syntax` : 

```
#[derive(Debug)]
struct Rectangle {
    width: u32,
    height: u32,
}

impl Rectangle {
    fn area(&self) -> u32 {
        self.width * self.height
    }
}

fn main() {
    let rect1 = Rectangle {
        width: 30,
        height: 50,
    };

    println!(
        "The area of the rectangle is {} square pixels.",
        rect1.area()
    );
}
```

### Getters

**The problem: you want controlled access to a field**

In Rust, struct fields can be either private (default, only accessible within the same module) or public (`pub`). Sometimes you want a field to be readable from outside the struct but not directly writable. If you make the field `pub`, anyone can both read _and_ write to it — no control.

**The solution: a getter method**

You keep the field _private_ but expose a _public method_ with the same name that just returns the value:

```rust
struct Rectangle {
    width: u32,  // private field
    height: u32,
}

impl Rectangle {
    pub fn width(&self) -> u32 {  // public getter
        self.width
    }
}
```

Now from outside the module, you can _read_ the width via `rect.width()`, but you can't do `rect.width = 10` because the field itself is private. **Read-only access** — exactly what you want.