A multidimensional array is basically an array of array.
# 2D arrays

```
int matrix[2][3] = { {1, 4, 2}, {3, 6, 8} };  
```

The first dimension represents the number of rows **[2]**, while the second dimension represents the number of columns **[3]**. The values are placed in row-order, and can be visualized like this:

![](https://www.w3schools.com/c/col-row.png)

### Access
```
int matrix[2][3] = { {1, 4, 2}, {3, 6, 8} };  
  
printf("%d", matrix[0][2]);  // Outputs 2
```
### Make modifications
```
int matrix[2][3] = { {1, 4, 2}, {3, 6, 8} };  
matrix[0][0] = 9;  
  
printf("%d", matrix[0][0]);  // Now outputs 9 instead of 1
```
### Loop into a 2D array
```
int matrix[2][3] = { {1, 4, 2}, {3, 6, 8} };  
  
int i, j;  
for (i = 0; i < 2; i++) {  
  for (j = 0; j < 3; j++) {  
    printf("%d\n", matrix[i][j]);  
  }  
}
```


We can also make as much dimensions with arrays like 4D...