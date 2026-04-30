```
fn main() {
    let mut s = String::from("hello");

    change(&mut s);
}

fn change(some_string: &mut String) {
    some_string.push_str(", world");
}
```

this way we the `chnage` function can mutate the data pointed by the reference.

Mutable references have one big restriction: If you have a mutable reference to a value, you can have no other references to that value as we can see there : 
```
let mut s = String::from("hello");

let r1 = &mut s;
let r2 = &mut s;

// or

let r1 = &s; // no problem 
let r2 = &s; // no problem 
let r3 = &mut s; // BIG PROBLEM

println!("{r1}, {r2}");
```

we can use curly brackets to create a new scope, allowing for multiple mutable references, just not _simultaneous_ ones.

```
let mut s = String::from("hello");

{
	let r1 = &mut s;
} // r1 goes out of scope here, so we can make a new reference with no problems.

let r2 = &mut s;
```

Users of an immutable reference don’t expect the value to suddenly change out from under them. However, multiple immutable references are allowed because no one who is just reading the data has the ability to affect anyone else’s reading of the data. (this makes the code mitigate data races bug only one reference can modify something).

Note that a reference’s scope starts from where it is introduced and continues through the last time that reference is used. So after the last usage of a `reference` a mutable `reference` can be declared and later used.