In C, variables are only accessible inside the region they are created. This is called **scope**.
# Local scope
A variable created inside a function belongs to the _local scope_ of that function, and can only be used inside that function.
# Global scope
A variable created outside of a function, is called a **global variable** and belongs to the _global scope_.
### Naming variables
If you operate with the same variable name inside and outside of a function, C will treat them as two separate variables; One available in the global scope (outside the function) and one available in the local scope (inside the function):
```
// Global variable x  
int x = 5;  
  
void myFunction() {  
  // Local variable with the same name as the global variable (x)  
  int x = 22;  
  printf("%d\n", x); // Refers to the local variable x  
}  
  
int main() {  
  myFunction();  
  
  printf("%d\n", x); // Refers to the global variable x  
  return 0;  
}
```

