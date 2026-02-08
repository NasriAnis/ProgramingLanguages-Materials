Data types specifies the size and type of information the variable will store.

| Sr.No. | Types & Description                                                                                                                                                            |
| ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 1      | **Basic Types**<br><br>They are arithmetic types and are further classified into: (a) integer types and (b) floating-point types.                                              |
| 2      | **Enumerated types**<br><br>They are again arithmetic types and they are used to define variables that can only assign certain discrete integer values throughout the program. |
| 3      | **The type void**<br><br>The type specifier _void_ indicates that no value is available.                                                                                       |
| 4      | **Derived types**<br><br>They include (a) Pointer types, (b) Array types, (c) Structure types, (d) Union types and (e) Function types.                                         |
### Integer data types
| Type           | Storage size | Value range                                          |
| -------------- | ------------ | ---------------------------------------------------- |
| char           | 1 byte       | -128 to 127 or 0 to 255                              |
| unsigned char  | 1 byte       | 0 to 255                                             |
| signed char    | 1 byte       | -128 to 127                                          |
| int            | 2 or 4 bytes | -32,768 to 32,767 or -2,147,483,648 to 2,147,483,647 |
| unsigned int   | 2 or 4 bytes | 0 to 65,535 or 0 to 4,294,967,295                    |
| short          | 2 bytes      | -32,768 to 32,767                                    |
| unsigned short | 2 bytes      | 0 to 65,535                                          |
| long           | 8 bytes      | -9223372036854775808 to 9223372036854775807          |
| unsigned long  | 8 bytes      | 0 to 18446744073709551615                            |
### Floating-Point data types
| Type        | Storage size | Value range            | Precision         |
| ----------- | ------------ | ---------------------- | ----------------- |
| float       | 4 byte       | 1.2E-38 to 3.4E+38     | 6 decimal places  |
| double      | 8 byte       | 2.3E-308 to 1.7E+308   | 15 decimal places |
| long double | 10 byte      | 3.4E-4932 to 1.1E+4932 | 19 decimal places |
### User defined data type
there are 4 user defined data types in C struct, union, enum, typedef
#### Struct
struct let you store different data types in one variable.
```
struct student { 
	char name[20]; 
	int marks, age; 
};
```
#### Union
a union is a special case of struct where the size of union variable is not the sum of sizes of individual elements as in struct but it corresponds to the largest size among individual elemenets. Hence only one of elemenets can be used at a time.
```
union ab { 
	int a; 
	float b; 
};
```
#### enum
Used to create a type with a set of **named integer constants**.
```
enum Day { MON, TUE, WED, THU, FRI, SAT, SUN };
```
#### typedef
Used to create a **new name** (alias) for an existing type.
`typedef unsigned long ulong;`
Now you can write:
`ulong x = 20;`
### Void data type
| Sr.No | Types & Description                                                                                                                                                                                                                                    |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 1     | **Function returns as void**<br><br>There are various functions in C that do not return any value or you can say they return **void**. A function with no return value has the return type as **void**. For example, **void exit (int status);**       |
| 2     | **Function arguments as void**<br><br>There are various functions in C which do not accept any parameter. A function with no parameter can accept a void. For example, **int rand(void);**                                                             |
| 3     | **Pointers to void**<br><br>A pointer of type void * represents the address of an object, but not its type. For example, a memory allocation function void ***malloc( size_t size );** returns a pointer to void which can be casted to any data type. |
### Array data type
An array is a collection of multiple values of same data type stored in consecutive memory locations. The size of array is mentioned in square brackets []. For example,
`int marks[5];`

Arrays can be initialized at the time of declaration. The values to be assigned are put in parentheses.
`int marks[ ]={50,56,76,67,43};`

C also supports multi-dimensional arrays.
### Pointer data type
 pointer is a special variable that stores address or reference of another variable/object in the memory. The name of pointer variable is prefixed by asterisk (*). The type of the pointer variable and the variable/object to be pointed must be same.

int x;  
int *y;  
y = &x;

Here, "y" is a pointer variable that stores the address of variable "x" which is of "int" type.