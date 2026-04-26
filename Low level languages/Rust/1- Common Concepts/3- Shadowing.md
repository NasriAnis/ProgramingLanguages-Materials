In rust we can declare a variable with the name of another variable (this is called shadowing).

to shadow a variable we use the same variable name as well as the `let` keyword :

```
let x = 5; // imutable
let x = x + 2 // chnaged the imutable variable
```

if we shadow a variable inside a scope and the scope closes the variable retake its previous value :

```
let x = 3

{
	let x = x * 2 // there x == 6
}

// there x == 3
```

# Difference between shadowing and making a variable immutable :

First when using mutable variable the variable content can be modified whiteout us knowing, however when shadowing we are sure that we did it since we used the `let` keyword.

Second when we shadow a variable we create a complete new one this way we can change the variable type easily contrary to mutable variables.