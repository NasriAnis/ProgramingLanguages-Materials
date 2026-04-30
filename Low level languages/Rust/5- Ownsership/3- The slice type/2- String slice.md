A _string slice_ is a reference to a contiguous sequence of the elements of a `String`, and it looks like this:

```
let s = String::from("hello world");

let hello = &s[0..5];
let world = &s[6..11];
```

![](../../../../zzDocument/Pasted%20image%2020260430094930.png)

