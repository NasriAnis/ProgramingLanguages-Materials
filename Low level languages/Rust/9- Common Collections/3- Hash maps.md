 The type `HashMap<K, V>` stores a mapping of keys of type `K` to values of type `V` using a _hashing function_, which determines how it places these keys and values into memory.

### Hash map creation

```
use std::collections::HashMap;

let mut scores = HashMap::new(); // new empty hash map

scores.insert(String::from("Blue"), 10); // inserting a key and value
scores.insert(String::from("Yellow"), 50);
```

Just like vectors, hash maps store their data on the heap. This `HashMap` has keys of type `String` and values of type `i32`. Like vectors, hash maps are homogeneous: All of the keys must have the same type, and all of the values must have the same type.

### Accessing values 

We can get a value out of the hash map by providing its key to the `get` method

```
use std::collections::HashMap;

let mut scores = HashMap::new();

scores.insert(String::from("Blue"), 10);
scores.insert(String::from("Yellow"), 50);

let team_name = String::from("Blue");
let score = scores.get(&team_name).copied().unwrap_or(0);
```

The `get` method returns an `Option<&V>`; if there’s no value for that key in the hash map, `get` will return `None`. This program handles the `Option` by calling `copied` to get an `Option<i32>` rather than an `Option<&i32>`, then `unwrap_or` to set `score` to zero if `scores` doesn’t have an entry for the key.

we can iterate through the value :

```
use std::collections::HashMap;

let mut scores = HashMap::new();

scores.insert(String::from("Blue"), 10);
scores.insert(String::from("Yellow"), 50);

for (key, value) in &scores {
	println!("{key}: {value}");
}
```

### Ownership in hash maps

For types that implement the `Copy` trait, like `i32`, the values are copied into the hash map. for owned values like String ownership is taken. If we insert references to values into the hash map, the values won’t be moved into the hash map. The values that the references point to must be valid for at least as long as the hash map is valid.

### Updating a hash map

Overwriting a value : If we insert a key and a value into a hash map and then insert that same key with a different value, the value associated with that key will be replaced.

Adding a Key and Value Only If a Key Isn’t Present : 
```
use std::collections::HashMap;

let mut scores = HashMap::new();
scores.insert(String::from("Blue"), 10);

scores.entry(String::from("Yellow")).or_insert(50);
scores.entry(String::from("Blue")).or_insert(50);

println!("{scores:?}");
```

Updating a value based on the old one : 
```
use std::collections::HashMap;

let text = "hello world wonderful world";

let mut map = HashMap::new();

for word in text.split_whitespace() {
	let count = map.entry(word).or_insert(0);
	*count += 1;
}

println!("{map:?}");
```

This code will print `{"world": 2, "hello": 1, "wonderful": 1}`.