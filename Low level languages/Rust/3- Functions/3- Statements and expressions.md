The difference between a statement and an expression is that, a statement is an instruction that perform some action but doesn't return something. where as expressions evaluate to a resultant value.

this are statements :
```
let y = 6;
------------------------
fn main() { 
	let y = 6; 
} // functions definitions are also statements.
```

these are expressions :
```
4 + 3 //math operations
```

Expressions can be part of a statement : `let x = 6;` there 6 is an expression that evaluate to the value 6. Calling a function is an expression. Calling a macro is an expression.

A new scope block created with curly brackets is an expression, for example:
```
fn main() { 
	let y = { // the block is an expression
		let x = 3; 
		x + 1 
	}; 
	
	println!("The value of y is: {y}"); 
}
```

# Note :
Note the `x + 1` line without a semicolon at the end. Expressions do not include ending semicolons. If you add a semicolon to the end of an expression, you turn it into a statement, and it will then not return a value.