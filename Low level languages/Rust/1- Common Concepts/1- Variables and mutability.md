To define a variable in rust we use the `let` command. By default variables are immutable until we specify the `mut` keyword.

```
let x = 5; // cant be modified until certain conditions are met
let mut x = 5; // can be modifiyed
```

The point of mutability is that it is easier to maintains and easier for future readers.

the value of an immutable variable is known at runtime and lives at memory.