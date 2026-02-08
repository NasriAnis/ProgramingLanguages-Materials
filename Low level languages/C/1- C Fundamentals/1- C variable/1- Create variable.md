# Types
- Integers - whole numbers which can be either positive or negative. Defined using `char`, `int`, `short`, `long` or `long long`.

- Unsigned integers - whole numbers which can only be positive. Defined using `unsigned char`, `unsigned int`, `unsigned short`, `unsigned long` or `unsigned long long`.

- Floating point numbers - real numbers (numbers with fractions). Defined using `float` and `double`.

- Structures - will be explained later, in the Structures section.

Note : C does not have a Boolean type, it is defined using :
```
#define BOOL char
#define FALSE 0
#define TRUE 1
```
# Declaring a variable
Syntax :
```
type variableName = value ;
```
or :
```
// Declare a variable  
int myNum;  
  
// Assign a value to the variable  
myNum = 15;
```
#### Declare multiple variable
```
int x = 5, y = 6, z = 50;  
printf("%d", x + y + z);
```
#### Print multiple variable
```
printf("%d %d %d", x, y, z);
```

