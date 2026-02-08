# C++ cin object functions
Below is a table of most commonly used functions of C++ cin object :

| Functions         | Definition                                                                                                                                                             |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **cin.get()**     | The cin.get() function **reads a single character** including whitespace from input stream.                                                                            |
| **cin.getline()** | It **reads a line of text** from user input **along with whitespaces** until it reaches end of the line or newline character. `cin.getline(variable, number be read);` |
| **cin.read()**    | You can specify the number of characters you want to read from input stream using cin.read() function.                                                                 |
| **cin.putback()** | The cin.putback() function puts a character back into the input stream that was removed after using get() function to read the character.                              |
| **cin.peek()**    | It looks at the next character in the input stream without removing it unlike **get() function** that removes the character.                                           |
| **cin.good()**    | It checks the state of input stream and **returns true** if the input stream is in a **good state** with no errors.                                                    |
| **cin.bad()**     | It checks the state of input stream and **returns true** if an **error occurs** in the stream that can not be recovered.                                               |
| **cin.fail()**    | It returns true for **failed operations** on the input stream.                                                                                                         |
| **cin.clear()**   | It **clears the error flags** of the stream and reset it to good state.                                                                                                |
| **cin.ignore()**  | The cin.ignore() function is used to **skip and discard** characters from the input buffer so they are not read by the next input operation.                           |
| **cin.gcount()**  | It **returns the count** of characters extracted by the last unformatted input operation including whitespaces.                                                        |
| **cin.seekg()**   | It is used in **file handling** to **set the position** of the get pointer in the input stream. It is generally used with file streams **(ifstream)**.                 |
| **cin.eof()**     | It returns true upon reaching end of file in the input stream.                                                                                                         |
| **cin.rdbuf()**   | It returns the stream buffer object of cin that can be used to read from or redirect the input stream directly.                                                        |
to see examples visit : https://www.tutorialspoint.com/cplusplus/cpp_cin.htm