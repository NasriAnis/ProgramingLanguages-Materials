instead of writing many if else statement switch can be used. it selects one of many code blocks to be executed :

syntax
```
switch (_expression_) {  
  case x:  
    _// code block_  
    break;  
  case y:  
    _// code block_  
    break;  
  default:  
    _// code block_  
}
```

This is how it works:
- The `switch` expression is evaluated once
- The value of the expression is compared with the values of each `case`
- If there is a match, the associated block of code is executed
- The `break` statement breaks out of the switch block and stops the execution
- The `default` statement is optional, and specifies some code to run if there is no case match

Here, the switch case checks exact matches only. But sometimes, we want to check if a value falls within a range, like **1-5** or **'A'-'Z'**. Instead of writing a separate case for each value, we can define a range of values in a single case. This is called **a switch case with ranges**. For example −
```
switch(num) { 
	case 1 ... 5: printf("Between 1 and 5"); break; 
	case 6 ... 10: printf("Between 6 and 10"); break; 
	default: printf("Other"); 
}
```