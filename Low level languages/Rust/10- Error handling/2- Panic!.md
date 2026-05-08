When bad things happen in code Rust where the code stop execution directly but also if we want to make the code panic the `panic!` macro handles that.

By default, these panics will print a failure message, unwind, clean up the stack, and quit. Via an environment variable, you can also have Rust display the call stack when a panic occurs to make it easier to track down the source of the panic.

---
### Unwinding the Stack or Aborting in Response to a Panic

By default, when a panic occurs, the program starts _unwinding_, which means Rust walks back up the stack and cleans up the data from each function it encounters. However, walking back and cleaning up is a lot of work. Rust therefore allows you to choose the alternative of immediately _aborting_, which ends the program without cleaning up.

Memory that the program was using will then need to be cleaned up by the operating system. If in your project you need to make the resultant binary as small as possible, you can switch from unwinding to aborting upon a panic by adding `panic = 'abort'` to the appropriate `[profile]` sections in your _Cargo.toml_ file. For example, if you want to abort on panic in release mode, add this:

```
[profile.release] 
panic = 'abort'
```

---

To make code panic in certain circumstances :

```
fn main() {
    panic!("crash and burn");
}
```

When we get a panic (for example when reading an array past its size) we can run :

```
$ RUST_BACKTRACE=1 cargo run
```

to get what happened before the panic.