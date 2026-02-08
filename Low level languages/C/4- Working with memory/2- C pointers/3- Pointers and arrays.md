It is possible to access arrays using pointers this is more efficient, faster and easier especially working with multidimensional arrays.
# How are pointers related to arrays
in C, the **name of an array**, is actually a **pointer** to the **first element** of the array The **memory address** of the **first element** is the same as the **name of the array**:
```
int myNumbers[4] = {25, 50, 75, 100};  
  
// Get the memory address of the myNumbers array  
printf("%p\n", myNumbers);  
  
// Get the memory address of the first array element  
printf("%p\n", &myNumbers[0]); 

`0x7ffe70f9d8f0   0x7ffe70f9d8f0`
```

So we can work with arrays using pointers, using the `*` we can access to the first element.

To access the rest of the elements in myNumbers, you can increment the pointer/array (+1, +2, etc).

```
int myNumbers[4] = {25, 50, 75, 100};  
  
// Get the value of the first element in myNumbers  
printf("%d", *myNumbers);

// Get the value of the second element in myNumbers  
printf("%d\n", *(myNumbers + 1));  
  
// Get the value of the third element in myNumbers  
printf("%d", *(myNumbers + 2));
```

It is also possible to change the value of array elements with pointers.
```
int myNumbers[4] = {25, 50, 75, 100};  
  
// Change the value of the first element to 13  
*myNumbers = 13;  
  
// Change the value of the second element to 17  
*(myNumbers +1) = 17;  
  
// Get the value of the first element  
printf("%d\n", *myNumbers);  
  
// Get the value of the second element  
printf("%d\n", *(myNumbers + 1));
```
