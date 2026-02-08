For code optimization, it is recommended to separate the declaration and the definition of the function.

You will often see C programs that have function declaration above `main()`, and function definition below `main()`.

```
// **Function declaration**  
void myFunction();  
  
// The main method  
int main() {  
  myFunction();  // **call** the function  
  return 0;  
}  
  
// **Function definition**  
void myFunction() {  
  printf("I just got executed!");  
}
```
# What about parameters
```
**// Function declaration**  
int myFunction(int x, int y);  
  
// The main method  
int main() {  
  int result = myFunction(5, 3); **// call** the function  
  printf("Result is = %d", result);  
  return 0;  
}  
  
**// Function definition**  
int myFunction(int x, int y) {  
  return x + y;  
}
```
# Function calling other functions
As long as you declare functions first, it is also possible to use functions to call other functions:
```
// Declare two functions, myFunction and myOtherFunction  
void myFunction();  
void myOtherFunction();  
  
int main() {  
  myFunction(); // call myFunction (from main)  
  return 0;  
}  
  
// Define myFunction  
void myFunction() {  
  printf("Some text in myFunction\n");  
  myOtherFunction(); // call myOtherFunction (from myFunction)  
}  
  
// Define myOtherFunction  
void myOtherFunction() {  
  printf("Hey! Some text in myOtherFunction\n");  
}
```
