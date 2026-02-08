it is also possible to place a loop inside another loop and it is called a nested for loop

```
int i, j;  
  
// Outer loop  
for (i = 1; i <= 2; ++i) {  
  printf("Outer: %d\n", i);  // Executes 2 times  
  
  // Inner loop  
  for (j = 1; j <= 3; ++j) {  
    printf(" Inner: %d\n", j);  // Executes 6 times (2 * 3)  
  }  
}
```

