despite using const to make constant variable, const can be used in different context :
### pointer to constant
this points to a constant value which cannot be modified however the pointer itself can change because its a variable and it can point somewhere else

```
const type* name;
// or
typeconst* name;
```

A "pointer to a constant" means the pointer can point to different variables, but the value of the object being pointed to cannot be changed through this pointer.

example pointer to constant with an integer :
```
#include <stdio.h>

int main (){
    int x = 30;
    int z = 10;

    const int* y = &x;

    //*y = 20; // this is not possible
    y = &z; // this is possible

    printf("%i", *y); //returns 10

    // the * means the value of where the variable points to

    // for example *y means the value where y points

    // here y points to the address of z &z

}
```

example pointer to constant with an array :
```
#include <stdio.h> 

int main() { 
	int arr[] = {1, 2, 3}; 
	
	// Pointer to constant integer (array base address) 
	const int *ptr = arr; //we dont use & here because an array name is a pointer to the first element
	printf("First element: %d\n", *ptr); //1
	
	// *ptr = 5; // not allowed (cannot change array element via ptr) 
	ptr++; // Allowed (can move pointer to next element) 
	printf("Second element: %d\n", *ptr); //2
return 0; 
}
```
### Const pointer to variable
this means the pointer itself is a constant variable, thus we cannot alter the pointer to point to another variable.

```
int* const ptr;
```

example :
```
#include <stdio.h>

int main (){
    int x = 30;
    int z = 10;

    int* const y = &x;

    *y = 20; // this is possible
    //y = &z; // // pointer cannot point to another variable

    printf("%i", *y); //returns 20

      // the * means the value of where the variable points to

    // for example *y means the value where y points

    // here y points to the address of z &z
}
```
this example is the opposite of the example above.
### constant pointer to constant 
this is a combination of the two above, which means we cannot alter the value pointed to by the pointer, also the pointer cannot point to other variables.

```
const int* const ptr;
```

example:
```
#include <stdio.h>

int main (){
    int x = 30;
    int z = 10;

    const int* const y = &x;

    //*y = 20; // this is not possible
    //y = &z; // this is not possible

    printf("%i", *y); //returns 20

    // the * means the value of where the variable points to
    // for example *y means the value where y points
    // here y points to the address of z &z
}
```