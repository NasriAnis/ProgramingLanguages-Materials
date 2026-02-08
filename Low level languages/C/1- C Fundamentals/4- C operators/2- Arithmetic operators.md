| Operator | Name           | Description                            | Example |
| -------- | -------------- | -------------------------------------- | ------- |
| +        | Addition       | Adds together two values               | x + y   |
| -        | Subtraction    | Subtracts one value from another       | x - y   |
| *        | Multiplication | Multiplies two values                  | x * y   |
| /        | Division       | Divides one value by another           | x / y   |
| %        | Modulus        | Returns the division remainder         | x % y   |
| ++       | Increment      | Increases the value of a variable by 1 | ++x     |
| --       | Decrement      | Decreases the value of a variable by 1 | --x     |
# Incrementing and Decrementing
The `++` operator increases a value by 1, while the `--` operator decreases a value by 1:
```
int x = 5;

++x; // Increment x by 1
printf("%d\n", x); // 6

--x; // Decrement x by 1
printf("%d\n", x); // 5
```

using the ++ as a prefix or suffix can change how the code behaves for example `printf("%d", x++)` will print the value of x then increment it the opposite is true `printf("%d", ++x)` this will increment then print the incremented x. 

this is also the case in assignment `z = x++` is not equal to `z = ++x`.

```
#include <stdio.h>

int main(){
	int x  = 5, y = 5, z;
	z = x++ + ++y;
	// z = 5 + 6 then x = x + 1
	
	printf("x: %d y: %d z: %d\n", x, y, z);
	
	return 0;
}

x: 6 y:6 z: 11
```