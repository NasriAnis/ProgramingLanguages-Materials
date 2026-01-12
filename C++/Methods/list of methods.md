| **Function**            | **Used With**                                  | **Utilization / What It Does**                       |
| ----------------------- | ---------------------------------------------- | ---------------------------------------------------- |
| `.find(key)`            | `map`, `set`, `unordered_map`, `unordered_set` | Find element by key; returns iterator or `end()`     |
| `.at(key)`              | `map`, `unordered_map`, `vector`, `array`      | Access element with bounds checking                  |
| `.operator[]`           | `map`, `unordered_map`, `vector`, `array`      | Access or insert element (maps insert default value) |
| `.insert(value)`        | Most containers                                | Insert element into container                        |
| `.emplace(args…)`       | Most containers                                | Construct element in-place (more efficient)          |
| `.erase(pos / key)`     | Most containers                                | Remove element(s)                                    |
| `.clear()`              | All containers                                 | Remove all elements                                  |
| `.size()`               | All containers                                 | Get number of elements                               |
| `.empty()`              | All containers                                 | Check if container is empty                          |
| `.begin()`              | All containers                                 | Iterator to first element                            |
| `.end()`                | All containers                                 | Iterator past last element                           |
| `.cbegin()` / `.cend()` | All containers                                 | Const iterators                                      |
| `.push_back(value)`     | `vector`, `deque`, `list`                      | Insert at end                                        |
| `.pop_back()`           | `vector`, `deque`, `list`                      | Remove last element                                  |
| `.push_front(value)`    | `deque`, `list`, `forward_list`                | Insert at front                                      |
| `.pop_front()`          | `deque`, `list`, `forward_list`                | Remove first element                                 |
| `.front()`              | Sequence containers                            | Access first element                                 |
| `.back()`               | Sequence containers                            | Access last element                                  |
| `.data()`               | `vector`, `array`, `string`                    | Get raw pointer to data                              |
| `.reserve(n)`           | `vector`, `string`                             | Pre-allocate memory                                  |
| `.resize(n)`            | `vector`, `deque`, `string`                    | Change container size                                |
| `.capacity()`           | `vector`, `string`                             | Get allocated capacity                               |
| `.count(key)`           | `set`, `map`, unordered versions               | Check existence / count duplicates                   |
| `.lower_bound(key)`     | `map`, `set`                                   | First element ≥ key                                  |
| `.upper_bound(key)`     | `map`, `set`                                   | First element > key                                  |
| `.equal_range(key)`     | `map`, `set`                                   | Get range of equivalent keys                         |
| `.bucket_count()`       | `unordered_*`                                  | Number of hash buckets                               |
| `.load_factor()`        | `unordered_*`                                  | Hash table load factor                               |
| `.rehash(n)`            | `unordered_*`                                  | Rebuild hash table                                   |