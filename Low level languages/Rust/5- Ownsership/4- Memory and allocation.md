when we copy a normal stack variable into another the data is copied and the two find themselves into the stack :

```
let x = 4;
let y = x
```

x and y both have the same value, there the value is duplicated, but when its a `String` type or any heap data allocation :

```
let x = String::from("hello");
let y = x
```

the data is not copied into a new place into the heap, the data information as pointer, size, length are given to y, after that x is no longer valid. (because when the scope end we cant free the same place pointed by two different variables its like freeing a freed memory location) :

![](../../../zzDocument/Pasted%20image%2020260429112256.png)

In addition, there’s a design choice that’s implied by this: Rust will never automatically create “deep” copies of your data. Therefore, any _automatic_ copying can be assumed to be inexpensive in terms of runtime performance.

---

The inverse of this is true for the relationship between scoping, ownership, and memory being freed via the `drop` function as well. When you assign a completely new value to an existing variable, Rust will call `drop` and free the original value’s memory immediately. Consider this code, for example:

```
    let mut s = String::from("hello");
    s = String::from("ahoy");

    println!("{s}, world!");
```

![](../../../zzDocument/Pasted%20image%2020260429112931.png)