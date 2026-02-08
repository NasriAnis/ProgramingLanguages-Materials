Format specifiers are used together with the `printf()` to tell the compiler what type pf data the variable is storing.
#### int input
we use the format specifier "%d" inside the printf()
```
int myNum = 15;  
printf("%d", myNum);  // Outputs 15
```
#### char input
we use the format specifier "%c"
#### float input
we use the format specifier "%f"
### Writing ways
```
int myNum = 15;  
printf("My favorite number is: %d", myNum);
```

```
int myNum = 15;  
char myLetter = 'D';  
printf("My number is %d and my letter is %c", myNum, myLetter);
```

Printing value without a variable :
```
printf("My favorite number is: %d", 15);  
printf("My favorite letter is: %c", 'D');
```

**Note**: "sizeof" returns "size_t". The type of unsigned integer of "size_t" can vary depending on platform. And, it may not be long unsigned int everywhere. In such cases, we use "%zu" for the format string instead of "%d".