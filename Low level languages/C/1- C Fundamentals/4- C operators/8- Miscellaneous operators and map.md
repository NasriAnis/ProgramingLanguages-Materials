| Operator | Description                                      | Example                                           |
| -------- | ------------------------------------------------ | ------------------------------------------------- |
| sizeof() | Returns the size of a variable.                  | sizeof(a), where a is integer, will return 4.     |
| &        | Returns the address of a variable.               | &a; returns the actual address of the variable.   |
| *        | Pointer to a variable.                           | *a;                                               |
| ?:       | Conditional Expression.                          | If Condition is true ? then value X, else value Y |
| .        | Member access operator                           | var.member                                        |
| −>       | Access members of a struct variable with pointer | ptr −> member;                                    |
# The `.` operator
The dot operator is a **member selection operator,** when used with the struct or union variable. The dot (.) operator has the **highest operator precedence in C** Language and its associativity is from left to right.

```
var.member;
```

Here, var is a variable of a certain struct or a union type, and member is one of the elements defined while creating structure or union.

```
#include <stdio.h> 

struct book{ 
	char title[10]; 
	double price; int pages; 
}; 

int main(){ 
	struct book b1 = {"Learn C", 675.50, 325}; 
	printf("Title: %s\n", b1.title); 
	printf("Price: %lf\n", b1.price); 
	printf("No of Pages: %d\n", b1.pages); 
	printf("size of book struct: %d", sizeof(struct book)); 
	
	return 0; 
}

Title: Learn C
Price: 675.500000
No of Pages: 325
size of book struct: 32
```