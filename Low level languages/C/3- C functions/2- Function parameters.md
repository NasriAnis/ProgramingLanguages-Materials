Information can be passed to functions as a parameter. Parameters act as variables inside the function.

Parameters are specified after the function name, inside the parentheses. You can add as many parameters as you want, just separate them with a comma:
```
_returnType_ _functionName_(_parameter1_, _parameter2_, _parameter3_) {  
  // code to be executed  
}
```
# Return values
The `void` keyword, used in the previous examples, indicates that the function should not return a value. If you want the function to return a value, you can use a data type (such as `int` or `float`, etc.) instead of `void`, and use the `return` keyword inside the function:
```
int myFunction(int x) {  
  return 5 + x;  
}  
  
int main() {  
  printf("Result is: %d", myFunction(3));  
  return 0;  
}  
  
// Outputs 8 (5 + 3)
```

```
int myFunction(int x, int y) {  
  return x + y;  
}  
  
int main() {  
  printf("Result is: %d", myFunction(5, 3));  
  return 0;  
}  
  
// Outputs 8 (5 + 3)
```

**Tip:** If you have many "result variables", it is better to store the results in an array:

```
int calculateSum(int x, int y) {  
  return x + y;  
}  
  
int main() {  
  // Create an array  
  int resultArr[6];  
  
  // Call the function with different arguments and store the results in the array  
  resultArr[0] = calculateSum(5, 3);  
  resultArr[1] = calculateSum(8, 2);  
  resultArr[2] = calculateSum(15, 15);  
  resultArr[3] = calculateSum(9, 1);  
  resultArr[4] = calculateSum(7, 7);  
  resultArr[5] = calculateSum(1, 1);  
  
  for (int i = 0; i < 6; i++) {  
    printf("Result%d is = %d\n", i + 1, resultArr[i]);  
  }  
  
  return 0;  
}
```