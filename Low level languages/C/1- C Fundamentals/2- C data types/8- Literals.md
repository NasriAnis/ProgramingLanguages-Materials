 literals are values of a certain data type represented directly into the source code. 

## Integer literals
for example `int x = 10` here 10 is an integer literal. A positive or negative whole number represented with digits 0 to 9, without a fractional part is a **decimal integer literal**. It must be within the acceptable range for the given OS platform.

An integer litteral can also have a suffix that is a combination of "U" and "L" for "unsigned" and "long", respectively. The suffix can be uppercase or lowercase and can be in any order.

```
int c = 89U;
long int = 99998L
```

C allows you to represent an integer in octal and hexadecimal number systems. For a literal representation of an octal, prefix the number with 0 (ensure that the number uses octal digits only, from 0 to 7).

For a hexadecimal literal, prefix the number with 0x or 0X. The hexadecimal number must have 0 to 9, and A to F (or a to f) symbols.

```
#include <stdio.h> 

int main(){ 
	int oct = 025; 
	int hex = 0xa1; 
	printf("Octal to decimal: %d\n", oct); 
	printf("Hexadecimal to decimal: %d\n", hex); 
}

Octal to decimal: 21
Hexadecimal to decimal: 161
```

Modern C compilers also let you represent an integer as a binary number, for which you need to add a **0b** prefix.

```
#include <stdio.h> 

int main(){ 
	int x = 0b00010000; 
	printf("binary to decimal: %d", x); 
}

binary to decimal: 16
```

Here are some examples of integer literals −
- 212  valid 
- 215u  valid 
- 0xFeeL  valid  
- 078  invalid: 8 is not an octal digit 
- 032UU invalid: cannot repeat a suffix

Here are some other examples of various types of integer literals −
- 85 decimal  
- 0213  octal  
- 0x4b hexadecimal  
- 30 int
- 30u unsigned int 
- 30l  long
- 0ul  unsigned long
## Floating-Point literals
A floating-point literal in C is a real number with an integer part and a fractional part within the range acceptable to the compiler in use, and represented in digits, decimal point with an optional exponent symbol (e or E).

A floating point literal is generally used for initializing or setting the value of a float or a double variable in C.

Floating point literals with a high degree of precision can be stated with the exponentiation symbol "e" or "E". This is called the **scientific notation of a float literal**.

While representing decimal form, you must include the decimal point, the exponent, or both. While representing exponential form, you must include the integer part, the fractional part, or both

Here are some examples of floating-point literals −
- 3.14159 valid  
- 314159E-5L valid 
- 510E invalid: incomplete exponent 
- 210f  invalid: no decimal or exponent 
- .e55  invalid: missing integer or fraction 
## Character literals
Character literals are generally assigned to a char variable that occupies a single byte. Using the **%c** format specifier outputs the character. Use **%d** and youll obtain the ASCII value of the character.

## String literal
A sequence of characters put inside double quotation symbols forms a string literal. C doesnt provide a string variable. Instead, we need to use an array of char type to store a string.