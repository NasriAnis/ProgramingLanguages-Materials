`.as_bytes()` =  convert a `String` to an array of bytes.
`.iter()` = create an iterator over an array of bytes : `for (i, &item) in bytes.iter().enumerate()`
`.enumerate()` = wraps the result of `iter` and returns each element as part of a tuple instead. The first element of the tuple returned from `enumerate` is the index, and the second element is a reference to the element.