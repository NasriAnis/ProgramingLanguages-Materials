a tuple is a way to group different variables (of different types) into a compound type that cant grow or shrink :

```
let tup: (i32, f64, u8) = (500, 6.4, 1); // we explecitly declared the types
```

the variable `tup` binds into the entire tuple. to get variable out we can use pattern matching :

```
let tup = (500, 6.4, 1); // implicit type declaration
let (x, y, z) = tup;// destructuring
println!("The value of y is: {y}");
```

We can also access a tuple element directly by using a period (`.`) followed by the index of the value we want to access :

```
let x: (i32, f64, u8) = (500, 6.4, 1); 
let five_hundred = x.0; 
let six_point_four = x.1; 
let one = x.2;
```

## `unit` tuples

```
let x: () = ();  // () on the left is the TYPE, () on the right is the VALUE
```

In Rust, `()` is called the **unit type**, and it serves as the "nothing meaningful to return" value. It's a zero-sized type it carries no data and takes up no memory.

Here's the core reason it needs to exist: Rust requires every expression to have a type

The type system has no concept of "nothing". Every function must return _something_, every expression must evaluate to _something_. So when there's genuinely nothing meaningful to return, `()` fills that slot.