Boolean data type are either true or false, this data type is not build in, for that there is different way to use boolean in C :
## Boolean type with `stdbool.h`
```
#include <stdbool.h>
```

A Boolean variable is declared with the `bool` keyword :
```
bool isProgrammingFun = true;  
bool isFishTasty = false;
```

Boolean return as integers 1 for true and 0 for false therefor the `%d` format specifier must be used to print a Boolean value.

It is more common to return Boolean value by comparing values and variables.
## Using `enum` to implement Boolean type
The enum type assigns user-defined identifiers to integral constants. We can define an enumerated type with true and false as the identifiers with the values 1 and 0.

```
#include <stdio.h> 

int main (){ 
	enum bool {false, true}; 
	enum bool x = true; 
	enum bool y = false; 
	printf ("%d\n", x); 
	printf ("%d\n", y); 
}

1
0
```
## Type def enum as BOOL
To make it more concise, we can use the **typedef** keyword to call enum bool by the name BOOL.

```
#include <stdio.h> 

int main(){ 
	typedef enum {false, true} BOOL; 
	BOOL x = true; 
	BOOL y = false; 
	printf ("%d\n", x); 
	printf ("%d\n", y); 
}

1
0

///////////////////////////////////////////
#include <stdio.h> 

int main(){ 
	typedef enum {false, true} BOOL; 
	int i = 0; 
	
	while(true){ 
		i++; 
		printf("%d\n", i); 
		
		if(i >= 5) 
			break; 
	} 
	return 0;
}

1
2
3
4
5
```
## Boolean value with `#define`
The **#define** preprocessor directive is used to define constants. We can use this to define the Boolean constants, FALSE as 0 and TRUE as 1.
# Comparing values and variables
Using comparison operators :
```
printf("%d", 10 > 9);  // Returns 1 (true) because 10 is greater than 9

///////////////////////////////////////////
int x = 10;  
int y = 9;  
printf("%d", x > y);

///////////////////////////////////////////
printf("%d", 10 == 10); // Returns 1 (true), because 10 is equal to 10  
printf("%d", 10 == 15); // Returns 0 (false), because 10 is not equal to 15  
printf("%d", 5 == 55);  // Returns 0 (false) because 5 is not equal to 55

///////////////////////////////////////////
bool isHamburgerTasty = true;  
bool isPizzaTasty = true;  
  
// Find out if both hamburger and pizza is tasty  
printf("%d", isHamburgerTasty == isPizzaTasty);
```