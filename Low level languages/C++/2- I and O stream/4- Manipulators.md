https://www.tutorialspoint.com/cplusplus/cpp_manipulators.htm
Manipulators in C++ are **special functions or objects** that are used with insertion **(<<)** and extraction **(>>)** operators **(cin/cout)** to control the input and output streams. You can change the format to display the output or how to read an input. The manipulators are declared in `<iostream>` and `<iomanip>` headers.
# Output stream manipulation

| Manipulators    | Definition                                                   | Syntax                                 |
| --------------- | ------------------------------------------------------------ | -------------------------------------- |
| **endl**        | It inserts a **newline** and **flushes** the output buffer.  | cout << "Tutorials" << endl;           |
| **setw(n)**     | It **sets the field width** for the next output operation.   | cout << setw(5) << 57;                 |
| **setfill()**   | It sets the **fill character**.                              | cout << setfill('*') << setw(5) << 42; |
| **showpoint**   | It displays **decimal point** for floating point numbers.    | cout << showpoint << 7.0;              |
| **noshowpoint** | It hides the decimal point.                                  | cout << noshowpoint << 7.0;            |
| **showpos**     | It is used for displaying **'+'** sign for positive numbers. | cout << showpos << 57;                 |
| **noshowpos**   | It hides **'+'** sign for positive numbers.                  | cout << noshowpos << 57;               |
| **flush**       | It **flushes** the output stream without newline.            | cout << "Data" << flush;               |
| **ends**        | It is used for inserting a null character and then flushes.  | cout << "String" << ends;              |
# Input stream manipulation
|Manipulators|Definition|Syntax|
|---|---|---|
|**ws**|It removes the whitespace character.|cin >> ws >> str;|
|**noskipws**|It avoids skipping whitespaces.|cin >> noskipws >> ch;|
# Alignment manipulators
| Manipulators | Definition                                               | Syntax                              |
| ------------ | -------------------------------------------------------- | ----------------------------------- |
| **left**     | It **left aligns** the output within field width.        | cout << left << setw(10) << "Hi";   |
| **right**    | It **right aligns** the output within field width.       | cout << right << setw(10) << "Hi";  |
| **internal** | It is used to **insert padding** between sign and value. | cout << internal << setw(6) << -57; |
# Floating point manipulators
| Manipulators        | Definition                                                                                               | Syntax                                 |
| ------------------- | -------------------------------------------------------------------------------------------------------- | -------------------------------------- |
| **setprecision(n)** | It sets the precision for decimal output. It specifies upto how many decimal points, we want the output. | cout << setprecision(2) << 1.41421356; |
| **fixed**           | It represents the given number in fixed-point notation.                                                  | cout << fixed << 1.41421356;           |
| **scientific**      | It represents the given number in scientific notation.                                                   | cout << scientific << 1234.5;          |
# Numeric base and case manipulators
|Manipulators|Definition|Syntax|
|---|---|---|
|**dec**|It sets the given value as **decimal output**.|cout << dec << 57;|
|**oct**|It sets the given value as **octal output**.|cout << oct << 57;|
|**hex**|It sets the given value as **hexadecimal output**.|cout << hex << 57;|
|**setbase**|It is used for setting the numeric base as decimal, octal, or hexadecimal in the output.|cout << setbase(16) << 42;|
|**showbase**|It is used to **display** the **base prefix** in the output.|cout << showbase << hex << 42;|
|**noshowbase**|It **hides base prefix** in the output.|cout << noshowbase << hex << 42;|
|**uppercase**|It represents hex and scientific in **uppercase** letters.|cout << uppercase << hex << 255;|
|**nouppercase**|It represents hex and scientific in **lowercase** letters.|cout << nouppercase << hex << 255;|
# Boolean manipulators

| Manipulators    | Definition                          | Syntax                       |
| --------------- | ----------------------------------- | ---------------------------- |
| **boolalpha**   | It displays booleans as true/false. | cout << boolalpha << true;   |
| **noboolalpha** | It displays booleans as 1/0.        | cout << noboolalpha << true; |
# Time and date manipulators
| Manipulators | Definition                                                    | Syntax                             |
| ------------ | ------------------------------------------------------------- | ---------------------------------- |
| **put_time** | It is used to format and output time in the specified format. | cout << put_time(&tm, "%Y-%m-%d"); |
| **get_time** | It is used for parsing the formatted time input.              | cin >> get_time(&tm, "%Y-%m-%d");  |