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

