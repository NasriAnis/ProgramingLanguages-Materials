### Variable scope

A _scope_ is the range within a program for which an item is valid, for example :

```
{                      // s is not valid here, since it's not yet declared
	let s = "hello";   // s is valid from this point forward

	// do stuff with s
}                      // this scope is now over, and s is no longer valid
```

there the variable `s` is a string literal and the value `hello` is hard-coded into the `.text` section of the program, this is inconvenient when we don't know what string we could use when running the problem (user input for example). it is more convenient to use the `String` type

### The string type

contrary to other type that are stored into the stack (poped in and poped out when their scope is over since they re known in size) the `String` type is stored into the heap. To explore how Rust knows when to clean up data stored into the heap the `String` type is perfect.

This type manages data allocated on the heap and as such is able to store an amount of text that is unknown to us at compile time.

```
let mut s = String::from("hello");

s.push_str(", world!"); // push_str() appends a literal to a String

println!("{s}"); // this will print `hello, world!`
```

---

In the case of a string literal, we know the contents at compile time, so the text is hardcoded directly into the final executable. This is why string literals are fast and efficient. But these properties only come from the string literal’s immutability.

With the `String` type, in order to support a mutable, growable piece of text, we need to allocate an amount of memory on the heap, unknown at compile time, to hold the contents. This means:

- The memory must be requested from the memory allocator at runtime.
- We need a way of returning this memory to the allocator when we’re done with our `String`.

That first part is done by us: When we call `String::from`, its implementation requests the memory it needs.

The memory is automatically returned once the variable that owns it goes out of scope.
```
{
	let s = String::from("hello"); // s is valid from this point forward

	// do stuff with s
}                                  // this scope is now over, and s is no
								   // longer valid
```

When a variable goes out of scope, Rust calls a special function for us. This function is called `drop`, and it’s where the author of `String` can put the code to return the memory. Rust calls `drop` automatically at the closing curly bracket.