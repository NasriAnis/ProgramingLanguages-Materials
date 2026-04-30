Note : A **dangling pointer** is a pointer that still holds the address of memory that is no longer valid — meaning the memory it points to has been freed, deallocated, or gone out of scope, but the pointer itself wasn't set to `NULL` afterward. or in rust a pointer that references a location in memory that may have been given to someone else.

The compiler does check for that in rust :

```
fn main() {
    let reference_to_nothing = dangle();
}

fn dangle() -> &String { // dangle returns a reference to a String

    let s = String::from("hello"); // s is a new String

    &s // we return a reference to the String, s
} // Here, s goes out of scope and is dropped, so its memory goes away.
  // Danger!
```

to solve this we return the value itself :

```
fn no_dangle() -> String {
    let s = String::from("hello");

    s
}
```