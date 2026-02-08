# Functions for dynamic MM
These function can be found inside the `<stdlib.h>` header file.

| Function                                  | Description                                                                                |
| ----------------------------------------- | ------------------------------------------------------------------------------------------ |
| void calloc(int num, int size);           | This function allocates an array of num elements each of which size in bytes will be size. |
| void free(void *address);                 | This function releases a block of memory block specified by address.                       |
| void malloc(size_t size);                 | This function allocates an array of num bytes and leave them uninitialized.                |
| void realloc(void *address, int newsize); | This function re-allocates memory extending it up to newsize.                              |
why allocate memory dynamically for example we take `char name[100]` if the array name takes less than 100 characters then the space is wasted however is it takes more this will lead to unwanted behavior.

in this kind of situation we need to use the dynamic memory allocation methods.

### `malloc()`
this function is defined in the `<stdlib.h>` header file, it allocates a block of memory of the required size and returns a void pointer that will be stored to a pointer.

`void *malloc (size)`

example :
```
#include <stdlib.h>

int main(){
	int *p = malloc(sizeof(int));
}
```

a way to dynamically allocate by the user input:
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main() {
    // allocate temp on the heap
    char *temp = malloc(100);  
    if (temp == NULL) {
        printf("Temp allocation failed!\n");
        return 1;
    }

    printf("Enter your name: ");
    scanf("%99s", temp);

    // allocate memory for final string
    char *name = malloc(strlen(temp) + 1);
    if (name == NULL) {
        printf("Name allocation failed!\n");
        free(temp);
        return 1;
    }

    // copy contents BEFORE freeing temp
    strcpy(name, temp);

    // NOW you can free temp safely
    free(temp);

    printf("Hello %s!\n", name);

    free(name);
    return 0;
}

```

to free a maloc() we use free()
### calloc()
this stands for contiguous allocation allocates the requested memory and return a pointer to it.

`void *calloc(n, size);`

here n is the number of elements to be allocated and size is the byte size of each element.

example :
```
#include <stdio.h> 
#include <stdlib.h> 
#include <string.h> 
int main() { 
	char *name; 
	name = (char *) calloc(strlen("TutorialsPoint"), sizeof(char)); 
	strcpy(name, "TutorialsPoint"); 
	
	if(name == NULL) { 
		fprintf(stderr, "Error - unable to allocate required memory\n"); 
	} else { 
		printf("Name = %s\n", name); 
	}
}
```

## Resizing and releasing memory
When your program comes out, the operating system automatically releases all the memory allocated by your program. However, it is a good practice to release the allocated memory explicitly by calling the **free()** function, when you are not in need of using the allocated memory anymore.

### realloc()
The realloc() (re-allocation) function in C is used to dynamically change the memory allocation of a previously allocated memory. You can increase or decrease the size of an allocated memory block by calling the realloc() function.

`void *realloc(*ptr, size);`

Here, the first parameter "**ptr**" is the pointer to a memory block previously allocated with malloc, calloc or realloc to be reallocated. If this is NULL, a new block is allocated and a pointer to it is returned by the function.

The second parameter "**size**" is the new size for the memory block, in bytes. If it is "0" and ptr points to an existing block of memory, the memory block pointed by ptr is deallocated and a NULL pointer is returned.

example :
```
#include <stdio.h> 
#include <stdlib.h> 
#include <string.h> 

int main() { 
	char *name; 
	name = (char *) calloc(strlen("TutorialsPoint"), sizeof(char)); 
	strcpy(name, "TutorialsPoint"); 
	name = (char *) realloc(name, strlen(" India Private Limited")); 
	strcat(name, " India Private Limited"); 
	
	if(name == NULL) { 
		fprintf(stderr, "Error - unable to allocate required memory\n"); 
	} else { 
		printf("Name = %s\n", name); 
	} 
}
```
### free()
The free() function in C is used to dynamically de-allocate the memory allocated using functions such as malloc() and calloc(), since it is not freed on their own.

In C programming, any reference to unused memory creates a garbage deposition, which may lead to problems like program crashing. Hence, it is wise to use the free() function to perform a manual cleaning operation of the allocated memory.

`void free(void *ptr);`