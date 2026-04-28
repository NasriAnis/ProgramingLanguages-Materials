the `loop` keyword tells rust to execute a block of code an infinite amount of time. until we tell it to using the `break` keyword. We can also use the `continue` keyword to skip an iteration.

basic syntax :
```
fn main() {
    loop {
        println!("again!");
    }
}
```

### Returning value from a loop
We can add the value we wanna return after the `break` statement :

```
fn main() {
    let mut counter = 0;

    let result = loop {
        counter += 1;

        if counter == 10 {
            break counter * 2; // we can laos use return to exit the whole function
        }
    }; // the semi colone end the let statement.

    println!("The result is {result}");
}
```

### Loop labels
When having nested loops the `break` and `continue` only work for the inner loop. We can specify a label for a loop that we can use for these keywords (this will make the effect on the specified loop label).

loops label begin with a single `'` :

```
fn main() {
    let mut count = 0;
    'counting_up: loop { // specified the labl
        println!("count = {count}");
        let mut remaining = 10;

        loop {
            println!("remaining = {remaining}");
            if remaining == 9 {
                break;
            }
            if count == 2 {
                break 'counting_up; // label usage
            }
            remaining -= 1;
        }

        count += 1;
    }
    println!("End count = {count}");
}
```