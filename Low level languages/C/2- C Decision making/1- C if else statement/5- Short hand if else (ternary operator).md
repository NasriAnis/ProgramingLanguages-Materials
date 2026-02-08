There is also a short-hand if else, which is known as the **ternary operator** because it consists of three operands. It can be used to replace multiple lines of code with a single line. It is often used to replace simple if else statements:

```
variable = (condition) ? expressionTrue : expressionFalse;
```

# Example
```
int time = 20;  
if (time < 18) {  
  printf("Good day.");  
} else {  
  printf("Good evening.");  
}


//////////////////////////////////////////////
int time = 20;  
(time < 18) ? printf("Good day.") : printf("Good evening.");
```