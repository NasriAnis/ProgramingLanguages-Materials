All functions defined within an `impl` block are called _associated functions_ because they’re associated with the type named after the `impl`.

We can define associated functions that don’t have `self` as their first parameter (and thus are not methods) because they don’t need an instance of the type to work with.

We’ve already used one function like this: the `String::from` function that’s defined on the `String` type.

Associated functions that aren’t methods are often used for constructors that will return a new instance of the struct.

```
#[derive(Debug)]
struct Rectangle {
    width: u32,
    height: u32,
}

impl Rectangle {
    fn square(size: u32) -> Self {
        Self {
            width: size,
            height: size,
        }
    }
}

fn main() {
    let sq = Rectangle::square(3);
}
```

that makes it easier to create a square `Rectangle` rather than having to specify the same value twice.

To call this associated function, we use the `::` syntax with the struct name; `let sq = Rectangle::square(3);` is an example. This function is namespaces by the struct: The `::` syntax is used for both associated functions and namespaces created by modules.