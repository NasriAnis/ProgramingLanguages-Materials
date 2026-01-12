https://www.geeksforgeeks.org/cpp/map-associative-containers-the-c-standard-template-library-stl/

A map is a container that stores a key with its value

```
std::map<Typeley, TypeValuer> name_map // creating a map

// add a value to a key
map[key] = value;

// add a value and a key
map.insert({key, value});

// access
map[key]
map.at(key)

// research
map.find(key)

// erase
map.erase(key);
```