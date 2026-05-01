Fr debugging purpose :

```
#[derive(Debug)] // specify functionality to print out debugging information
                 // make that functionality available for our struct
                 // we add the attribute befre the struct
struct Rectangle {
    width: u32,
    height: u32,
}

fn main() {
    let rect1 = Rectangle {
        width: 30,
        height: 50,
    };

    println!("rect1 is {rect1:?}"); // :? specifier tells pruintln to use an
                                    //  output format called Debug
}
```

output :

```
rect1 is Rectangle { width: 30, height: 50 }
```

The `Debug` trait enables us to print our struct in a way that is useful for developers so that we can see its value while we’re debugging our code.

we can also use the following  `{:#?}` instead of `{:?}`, the output :

```
rect1 is Rectangle { 
	width: 30, 
	height: 50, 
}
```

## `dbg` macro usage

Another way to print out a value using the `Debug` format is to use the [`dbg!` macro](https://doc.rust-lang.org/std/macro.dbg.html), which takes ownership of an expression (as opposed to `println!`, which takes a reference), prints the file and line number of where that `dbg!` macro call occurs in your code along with the resultant value of that expression, and returns ownership of the value.

```
#[derive(Debug)]
struct Rectangle {
    width: u32,
    height: u32,
}

fn main() {
    let scale = 2;
    let rect1 = Rectangle {
        width: dbg!(30 * scale),
        height: 50,
    };

    dbg!(&rect1);
}
```

We can put `dbg!` around the expression `30 * scale` and, because `dbg!` returns ownership of the expression’s value, the `width` field will get the same value as if we didn’t have the `dbg!` call there. We don’t want `dbg!` to take ownership of `rect1`, so we use a reference to `rect1` in the next call. Here’s what the output of this example looks like:

```
[src/main.rs:10:16] 30 * scale = 60
[src/main.rs:14:5] &rect1 = Rectangle {
    width: 60,
    height: 50,
}
```

In addition to the `Debug` trait, Rust has provided a number of traits for us to use with the `derive` attribute that can add useful behavior to our custom types. Those traits and their behaviors are listed in [Appendix C](https://doc.rust-lang.org/book/appendix-03-derivable-traits.html).