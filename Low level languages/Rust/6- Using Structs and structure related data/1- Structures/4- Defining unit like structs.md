We can have structures that don't have any field, these are called unit type structs because they behave similarly to `()` mentioned in tuples.

```
struct AlwaysEqual;

fn main() {
    let subject = AlwaysEqual;
}
```

Unit-like structs can be useful when you need to implement a trait on some type but don’t have any data that you want to store in the type itself.

Traits will be discussed later.