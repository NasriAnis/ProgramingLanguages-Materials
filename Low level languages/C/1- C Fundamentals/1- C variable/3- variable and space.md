when a variable is initialized space is reserved for the variable in memory that even if no value have been assigned to the variable, the space is equivalent to the data type.

however there is ways to delay memory usage and that by :
### using a pointer and allocate memory after
for example :
```
int *p = NULL;  // does not allocate space for an int
p = malloc(sizeof(int)); 
*p = 10;
```
### use arrays allocated later
```
int *arr = NULL;   // no array memory yet
arr = malloc(100 * sizeof(int));   // now memory exists
```
### Use struct pointer
```
struct Data *d = NULL;  // no memory yet
d = malloc(sizeof(struct Data));  // now memory is allocated
```