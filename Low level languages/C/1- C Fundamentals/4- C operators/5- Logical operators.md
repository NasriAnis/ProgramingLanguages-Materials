Logical operators are used to determine the logic between variables or values, by combining multiple conditions.

| Operator | Name | Example            | Description                                      |
| -------- | ---- | ------------------ | ------------------------------------------------ |
| &&       | AND  | x < 5 &&  x < 10   | Returns 1 if both statements are true            |
| \|       | OR   | x < 5 \| x < 4     | Returns 1 if one of the statements is true       |
| !        | NOT  | !(x < 5 && x < 10) | Reverse the result, returns 0 if the result is 1 |
# example
```c
bool isLoggedIn = true;
bool isAdmin = false;

printf("Regular user: %s\n", (isLoggedIn && !isAdmin) ? "true" : "false");
printf("Has access: %s\n", (isLoggedIn || isAdmin) ? "true" : "false");
printf("Not logged in: %s\n", (!isLoggedIn) ? "true" : "false");

Regular user: true  
Has access: true  
Not logged in: false
```

it print after checking conditions the `?` is a ternary operator which is like a short `if-else`.