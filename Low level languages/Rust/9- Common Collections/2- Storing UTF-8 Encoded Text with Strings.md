Similar to a `Vect<t>` Strings can grow in size and many other things.

```
let mut s1 = String::from("foo");
let s2 = "bar";
s1.push_str(s2);
println!("s2 is {s2}");
```

```
let mut s = String::from("lo");
s.push('l');
```

```
let s1 = String::from("Hello, ");
let s2 = String::from("world!");
let s3 = s1 + &s2; // note s1 has been moved here and can no longer be used
```

The reason `s1` is no longer valid after the addition, and the reason we used a reference to `s2`, has to do with the signature of the method that’s called when we use the `+` operator. The `+` operator uses the `add` method, whose signature looks something like this: `fn add(self, s: &str) -> String {`

### Indexing

Rust strings don’t support indexing. but why ? A `String` is a wrapper over a `Vec<u8>`, when stored not all language encode 1 letter to 1 byte so to prevent bugs rust doesn't support `String` indexing.

### Bytes, Scalar Values, and Grapheme Clusters

https://doc.rust-lang.org/book/ch08-02-strings.html#bytes-scalar-values-and-grapheme-clusters

### Slicing Strings

Indexing into a string is often a bad idea because it’s not clear what the return type of the string-indexing operation should be: a byte value, a character, a grapheme cluster, or a string slice. If you really need to use indices to create string slices, therefore, Rust asks you to be more specific.

Rather than indexing using `[]` with a single number, you can use `[]` with a range to create a string slice containing particular bytes:

`let hello = "Здравствуйте";  let s = &hello[0..4];`

Here, `s` will be a `&str` that contains the first 4 bytes of the string. Earlier, we mentioned that each of these characters was 2 bytes, which means `s` will be `Зд`.

If we were to try to slice only part of a character’s bytes with something like `&hello[0..1]`, Rust would panic at runtime in the same way as if an invalid index were accessed in a vector.

### iterating over Strings

```
for c in "Зд".chars() {
    println!("{c}");
}

-----------------------------

for b in "Зд".bytes() {
    println!("{b}");
}
```