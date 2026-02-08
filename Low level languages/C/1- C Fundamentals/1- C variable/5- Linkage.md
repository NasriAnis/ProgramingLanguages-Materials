First a translation unit is the result of taking a c source file with the .c extension and passing it through the processor, which expends all the `#include` files, replaces macros, removes comments, and applies conditional compilation. 

It is the complete source text that the compiler **actually compiles** into an object file.

in short a translation unit is one .c file after processing.

when compiling c files of the same project every file is compiled sequentially then linked.

linkage is a property that describes how variables should be linked by the linker.

the linked is a program that handles multiple machine code to produce an executable object.
## Variable linkage in c
In C, the **linkage** can control whether a variable can be used only in the file where it is declared or it can also be used in other files of the program.

Linkage tells us if a variable's name is **limited to one file** or can be **shared across multiple files**, helping us manage how variables are connected in a program.
### Types of linkage
#### Internal linkage
 an internal linkage refers to everything in the scope of a translation unit. an identifier with internal linkage can be only accessed within the same file where it is declared.

internal linkage is implemented using the `static` keyword and its value is stored on the RAM either in the initialized or unidealized.

```
Static int items = 10;
```

the only way to the variable to be accessed in another file is by calling `#include` with the file name where the static variable is placed.

```
#include "filename.c"
```
#### External linkage
An identifier implementing **external** **linkage** exists beyond a particular translation unit and is accessible throughout the entire program, which is the combination of all translation units (or object files). It is the **default** **linkage** **for globally scoped variables** (without static) and functions

The **extern** keyword is used to implement external linkage. When we use the 'extern' keyword, we tell the compiler that the variable is defined in another file. Thus, the declaration of an external identifier doesn't use any **memory space**.

Extern identifiers are stored in **RAM's** data (initialized/uninitialized) or code (text) segments.

example :
variable.c
```
#include <stdio.h>
int items = 10 //variable with external linkage
```

display.c
```
#include <stdio.h> 

// tells the compiler that the variable 
// have external linkage 

extern int items; 

int main(){ 
	printf("total item is: %d", items); //10
	return 0; 
	}
```