can also be called literals this refers to a fixed value that the program may not alter.

# integer literals

85 // decimal 
0213 // octal 
0x4b // hexadecimal 
30 // int 
30u // unsigned int 
30l // long 
30ul // unsigned long
# Floating point literal
A floating-point literal has an integer part, a decimal point, a fractional part, and an exponent part. While representing using decimal form, you must include the decimal point, the exponent, or both and while representing using exponential form, you must include the integer part, the fractional part, or both. The signed exponent is introduced by **e** or **E**.
# Boolean literals
There are two Boolean literals and they are part of standard C++ keywords :
- A value of **true** representing true.
- A value of **false** representing false.
# Character literals
|Escape sequence|Meaning|
|---|---|
|\\|\ character|
|\'|' character|
|\"|" character|
|\?|? character|
|\a|Alert or bell|
|\b|Backspace|
|\f|Form feed|
|\n|Newline|
|\r|Carriage return|
|\t|Horizontal tab|
|\v|Vertical tab|
|\ooo|Octal number of one to three digits|
|\xhh . . .|Hexadecimal number of one or more digits|
# Defining constant
Following is the form to use `#define` preprocessor to define a constant −

`#define identifier value`

and the const keyword as C ...