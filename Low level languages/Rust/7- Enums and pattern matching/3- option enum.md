this is defined by the standard library :

```
enum Option<T> {// the <t> is a generic type indicator
    None,
    Some(T),
}
```

usage :

```
fn find_port(service: &str) -> Option<u16> {
    if service == "http" {
        Some(80)   // ← "yes I found it, and the value is 80"
    } else {
        None       // ← "nothing found"
    }
}

match find_port("http") {
    Some(port) => println!("{}", port),  // ← port is now a plain u16, unwrapped
    None       => println!("not found"),
}
```

```
let some_number = Some(5);
let some_char = Some('e');
let absent_number: Option<i32> = None; // even for none the type shoud be specified
```

`Option` handles **the absence of a value** in general. That includes:

- **Not found** — searched for something and it doesn't exist
- **Not yet set** — a field that hasn't been initialized yet
- **Optional input** — a function parameter that may or may not be provided
- **Failed conversion** — parsing a string into a number that might not be valid
- **End of a sequence** — like reading the next item from an iterator that might be exhausted

The "null" comparison is just because in languages like C, `NULL` was the only tool people had for all of these situations. Rust replaces all of them with `Option` — but more importantly it makes the _possibility of absence_ visible in the type itself, so you're forced to handle it instead of forgetting and crashing.

This is the deepest point in that chapter. In C:

```c
int x = 5;
int y = null; // compiles fine
x + y;        // crashes at runtime
```

In Rust `Option<i8>` and `i8` are **completely different types**. The compiler refuses to let you treat them the same:

```rust
let x: i8 = 5;
let y: Option<i8> = Some(5);
x + y  // COMPILE ERROR — you must unwrap y first
```

The key rule: **if a variable's type is not `Option<T>`, it is guaranteed to never be null.** No checking needed. The possibility of absence is encoded in the type itself.

In other words, you have to convert an `Option<T>` to a `T` before you can perform `T` operations with it. Generally, this helps catch one of the most common issues with null: assuming that something isn’t null when it actually is. Then, when you use that value, you are required to explicitly handle the case when the value is null.

The `match` expression is a control flow construct that does just this when used with enums: It will run different code depending on which variant of the enum it has, and that code can use the data inside the matching value.