To get user input we use the `scanf()` functions.

```
// Create an integer variable that will store the number we get from the user  
int myNum;  
  
// Ask the user to type a number  
printf("Type a number: \n");  
  
// Get and save the number the user types  
**scanf**("%d", &myNum);  
  
// Output the number the user typed  
printf("Your number is: %d", myNum);
```

The `scanf()` function takes two arguments: the format specifier of the variable (`%d` in the example above) and the reference operator (`&myNum`), which stores the memory address of the variable.
# Multiple inputs
The `scanf()` function also allow multiple inputs.
```
int myNum;  
char myChar;

scanf("%d %c", &mynum, &mychar)
```

note : The `&` is used to give the address of the variable if you didn't allocate the variable use the & otherwise its not necessary.
# Take string input
```
char firstname[30];

scanf("%s", firstname);
```

note : When working with strings in `scanf()`, you must specify the size of the string/array

note :  the `scanf()` function has some limitations: it considers space (whitespace, tabs, etc) as a terminating character, which means that it can only display a single word (even if you type many words).

That's why, when working with strings, we often use the `fgets()` function to **read a line of text**. Note that you must include the following arguments: the name of the string variable, `sizeof`(_string_name_), and `stdin`:
```
char fullName[30];  
  
printf("Type your full name: \n");  
fgets(fullName, sizeof(fullName), stdin);  
  
printf("Hello %s", fullName);  
  
// Type your full name: John Doe  
// Hello John Doe
```
