When you know exactly how many times you want to loop through a block of code, use the `for` loop instead of a `while` loop:

### Syntax
```
for (expression 1; expression 2; expression 3) {  
  // code block to be executed
}
```

**Expression 1** is executed (one time) before the execution of the code block.

**Expression 2** defines the condition for executing the code block.

**Expression 3** is executed (every time) after the code block has been executed.

```
int i;  
  
for (i = 0; i < 5; i++) {  
  printf("%d\n", i);  
}
```