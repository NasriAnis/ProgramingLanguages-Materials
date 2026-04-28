basic syntax :

```
fn main() {
    let a = [10, 20, 30, 40, 50];

    for element in a {
        println!("the value is: {element}");
    }
}
```

we can also loop through ranges :

```
fn main() {
    for number in (1..4).rev() { // rev() for reverse range
        println!("{number}!");
    }
    println!("LIFTOFF!!!");
}
```

using the `Range` provided in the standard library.