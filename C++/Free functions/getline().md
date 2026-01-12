used to read an entire line of text from an input stream (like the keyboard or a file) and store it in a string variable. Unlike the extraction operator (`>>`), `getline` includes whitespace (spaces and tabs) in the input, stopping only when it encounters a delimiter, which defaults to the newline character (`\n`).

```
#include <iostream>
#include <string>

std::getline(inputStream, str, delimiter);
```

- `inputStream`: An object of the `std::istream` class, such as `std::cin` for console input or an `std::ifstream` object for file input.
- `str`: A `std::string` object where the read line of text will be stored.
- `delimiter` (optional): The character that tells the function to stop reading input. If omitted, the newline character (`\n`) is used by default.