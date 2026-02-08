# C++ cout object functions
Below is a table of most commonly used functions of C++ cout object :

| Functions            | Definition                                                                                                                                      |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| **cout.put()**       | The cout.put() function **writes a single character** to the output stream.                                                                     |
| **cout.write()**     | It **writes a specified number of characters** from a character array or string to the output stream. `cout.write(text, 7);`                    |
| **cout.flush()**     | The flush() function displays all pending output by **forcing the output buffer to empty** immediately.                                         |
| **cout.good()**      | It checks the state of output stream and **returns true** if the output stream is in a **good state** with no errors.                           |
| **cout.bad()**       | It checks the state of output stream and **returns true** if an **error occurs** in the stream that can not be recovered.                       |
| **cout.fail()**      | It returns true for both recoverable and non-recoverable errors in the output stream.                                                           |
| **cout.clear()**     | It **clears the error flags** of the stream and reset it to good state. The clear() function is also used to set error states of output stream. |
| **cout.width()**     | The cout.width() function is used to **set the minimum field width** for the next output operation.                                             |
| **cout.precision()** | It **sets the precision** for floating-point numbers displayed in the output stream.                                                            |
| **cout.fill()**      | It **sets the fill character** that is used to pad output when the width is greater than the number of characters to be displayed.              |
| **cout.seekp()**     | It is used to **set the position** of the put pointer in the output stream. It is generally used with file streams **(ofstream)**.              |
| **cout.tellp()**     | It returns the current position of the put pointer in the output stream. It is generally used with file streams **(ofstream)**.                 |
| **cout.eof()**       | It returns true upon reaching end of file in the output stream.                                                                                 |
| **cout.rdbuf()**     | It returns the stream buffer object of cout that can be used to write to or redirect the output stream directly.                                |
for examples visit : https://www.tutorialspoint.com/cplusplus/cpp_cout.htm