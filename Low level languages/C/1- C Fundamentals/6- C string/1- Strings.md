String are used to store text and characters, unlike other programing language c doesn't have a string type instead we use the `char` type and create an array of characters.
```
char greetings[] = "Hello World!";  
printf("%s", greetings);
```

Since its an array you can choose to print a single character `%c`.

Beside we can modify characters in strings using indexes or even loop through the array.

```
char carName[] = "Volvo";  
int i;  
  
for (i = 0; i < 5; ++i) {  
  printf("%c\n", carName[i]);  
}
```

## Another Way Of Creating Strings

In the examples above, we used a "string literal" to create a string variable. This is the easiest way to create a string in C.

You should also note that you can create a string with a set of characters. This example will produce the same result as the example in the beginning of this page:

### Example
```
char greetings[] = {'H', 'e', 'l', 'l', 'o', ' ', 'W', 'o', 'r', 'l', 'd', '!', '\0'};  
printf("%s", greetings);
```

**Why do we include the `\0` character at the end?** This is known as the "null terminating character", and must be included when creating strings using this method. It tells C that this is the end of the string.