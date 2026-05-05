Vector : `Vec<t>` allows to store more than one value in a single data structure that puts all the values next to each other in memory. Vectors can only store values of the same type.

### Creating a new vector

```
let v: Vec<i32> = Vec::new(); // the type is specified since is not populated

let v = vec![1, 2, 3]; // macro, which will create a new vector 
					   // that holds the values you give it
```

### Updating a vector

```
let mut v = Vec::new();

v.push(5);
v.push(6);
v.push(7);
v.push(8);
```

### Reading elements of vectors

The two ways :
- indexing
- `get` method

```
let v = vec![1, 2, 3, 4, 5];

let third: &i32 = &v[2];
println!("The third element is {third}");


// When we use the `get` method with the index passed as an argument, we get an `Option<&T>` that we can use with `match`.

let third: Option<&i32> = v.get(2);
match third {
	Some(third) => println!("The third element is {third}"),
	None => println!("There is no third element."),
}
```

this wont work :

```
let mut v = vec![1, 2, 3, 4, 5];

let first = &v[0];

v.push(6);

println!("The first element is: {first}");
```

 Why should a reference to the first element care about changes at the end of the vector? This error is due to the way vectors work: Because vectors put the values next to each other in memory, adding a new element onto the end of the vector might require allocating new memory and copying the old elements to the new space, if there isn’t enough room to put all the elements next to each other where the vector is currently stored. In that case, the reference to the first element would be pointing to deallocated memory. The borrowing rules prevent programs from ending up in that situation.

https://doc.rust-lang.org/nomicon/vec/vec.html

### Iterating over a vector

```
let v = vec![100, 32, 57];
for i in &v {
	println!("{i}");
}
```

We can also iterate over mutable references to each element in a mutable vector in order to make changes to all the elements.

```
let mut v = vec![100, 32, 57];
for i in &mut v {
	*i += 50;
}
```

### Using enums to store multiple types

We can define an enum whose variants will hold the different value types, and all the enum variants will be considered the same type: that of the enum. Then, we can create a vector to hold that enum and so, ultimately, hold different types.

```
enum SpreadsheetCell {
	Int(i32),
	Float(f64),
	Text(String),
}

let row = vec![
	SpreadsheetCell::Int(3),
	SpreadsheetCell::Text(String::from("blue")),
	SpreadsheetCell::Float(10.12),
];
```

### APIs

https://doc.rust-lang.org/std/vec/struct.Vec.html