# Get size
To get the size of an array in bites we use the `sizeof` operator.
```c
int myNumbers[] = {10, 25, 50, 75, 100};

printf("%zu", sizeof(myNumbers));  // Prints 20
```
# Get number of elements
Using this formula :
```c
int myNumbers[] = {10, 25, 50, 75, 100};
int length = sizeof(myNumbers) / sizeof(myNumbers[0]);

printf("%d", length);  // Prints 5
```
