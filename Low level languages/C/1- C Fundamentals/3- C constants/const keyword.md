With the `constant` keyword a variable can be made unchangeable once declared.

```
const type NAME = val;
```

A good practice is to declare a const variable with upper case.

```
const float PI; 
PI = 3.14159265359;

error: assignment of read-only variable 'PI'
```
this cant be done,  you must initialize the constant value at the time of the declaration. this is because the compiler assigns a random cabbage value at the time of declaration here.