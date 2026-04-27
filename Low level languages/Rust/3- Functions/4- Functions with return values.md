In rust functions can return a value, this is declared using the `->` operator (note that return values doesn't have a name.)

```
fn five() -> i32 { // return type specified
	5 // expression (no semi colone) as seen previously
} 

fn main() { 
	let x = five(); 
	println!("The value of x is: {x}"); 
}
```

the return value of a function is synonymous with the value of the final expression. we can also use the `return` to return from a function (earlier) and specify a value.

another example :

```
fn main() {
    let x = plus_one(5);

    println!("The value of x is: {x}");
}

fn plus_one(x: i32) -> i32 {
    x + 1
}
```