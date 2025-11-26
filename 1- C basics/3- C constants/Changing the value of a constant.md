note: this is not a good practice, this can cause crashes and more !

By definition a constant cant be changed however there is a way to change a const variable and that using a pointer variable. A Pointer is a variable that stores the address of another variable. Since it is a variable, its value can be changed. Moreover, this change reflects in the original variable.

```
#include <stdio.h> 
int main(){
 
const int x = 10; 
printf("Initial Value of Constant: %d\n", x);

// y is a pointer to constant x 
int* y = &x; 

// assign new value 
*y = 100; 

printf("Value of Constant after change: %d", x); 

return 0; 
}

Initial Value of Constant: 10
Value of Constant after change: 100
```

Note that this technique is effective only for those **constants** which are defined using the **const** qualifier.

If you have defined your constant using the **#define** directive, then you cannot apply this process. This is because the pointer has a data type, and it must be of the same type whose address is to be stored. On the other hand, the constant defined using the **#define** directive doesn't really have a data type. It is in fact a macro whose value is substituted during the runtime.