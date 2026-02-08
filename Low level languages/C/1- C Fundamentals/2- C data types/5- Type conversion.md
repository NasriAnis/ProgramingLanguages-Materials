We sometimes need to convert the value of one data type to another. 

There is two types of conversion in C :
- **Implicit Conversion** (automatically)  
- **Explicit Conversion** (manually)
# Implicit Conversion
This is done automatically by the compiler when a value of one data type is assigned to another.

for example storing a int in a float will result to a float so storing 9 as a float will result to storing 9.000000 and the opposite is right.

As for another example dividing two integer will result to an integer so 5 / 2 is normally equal to 2.5 but storing them in a form of int will result to a int 2
```
int x = 5;  
int y = 2;
float sum = 5 / 2;  
  
printf("%f", sum); // 2.000000
```
# Usual type conversion
Usual arithmetic conversions are implicitly performed to cast their values to a common type. The compiler first performs integer promotion; if the operands still have different types, then they are converted to the type that appears highest in the following hierarchy.

![[Pasted image 20251128052850.jpg]]

# Explicit Conversion
This is done manually by placing the type in parentheses () in front of the value. this is done when you need to convert a data type with higher byte size to another data type with lower byte size.

```
type2 var2 = (type1) var1;
```

Note that if type1 is smaller in length than type2, then you dont need such explicit casting. It is only when type1 is greater in length than type2 that you should use the typecast operator.

```
// Manual conversion: int to float  
float sum = (float) 5 / 2;  
  
printf("%f", sum); // 2.500000
```

```
int num1 = 5;  
int num2 = 2;  
float sum = (float) num1 / num2;  
  
printf("%f", sum); // 2.500000
```

```
int num1 = 5;  
int num2 = 2;  
float sum = (float) num1 / num2;  
  
printf("%.1f", sum); // 2.5
```
# Typecasting functions
The standard C library includes a number of functions that perform typecasting.
### The `atoi()` function
The `atoi()` function converts a string of characters to an integer value. The function is declared in the **stdlib.h** header file.

```
#include <stdio.h>
#include <stdlib.h>

int main(){
	char str[]= "123";
	int num = atoi(str);
	
	printf("%d\n", num);
	
	return 0;
}

123
```
### The `itoa()` function
You can use the itoa() function to convert an integer to a null terminated string of characters. The function is declared in the **stdlib.h** header file.

```
#include <stdio.h>
#unclude <stdlib.h>

int main(){
	int num = 123;
	char str[10];
	
	itoa(num,str,10);
	
	printf("%s\n", str);
	
	return 0;
}

123
```