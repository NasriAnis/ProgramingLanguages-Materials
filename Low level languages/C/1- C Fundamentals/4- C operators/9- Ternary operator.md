The ternary operator (?:) in C is a type of conditional operator. The term "ternary" implies that the operator has three operands. The ternary operator is often used to put multiple conditional (if-else) statements in a more compact manner.

```
exp1 ? exp2 : exp3
```

- **exp1** − A Boolean expression evaluating to true or false
- **exp2** − Returned by the ? operator when exp1 is true
- **exp3** − Returned by the ? operator when exp1 is false

Example :
```
(a % 2 == 0) ? printf("%d is Even \n", a) : printf("%d is Odd \n", a);
/////////////////////////////////////////////////
c = (a >= b) ? a : b;
/////////////////////////////////////////////////
c = (a >= b) ? printf ("a is larger "), c = a : printf("b is larger "), c = b; //multiple statements in the true and/or false operand they must me separated by comas
```
### Nested ternary operator
```
exp1 ? (exp2 ? expr3 : expr4) : (exp5 ? expr6: expr7)
```