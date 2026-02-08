## 1. What happens when you pass a variable normally?

When you pass a variable **by value**, the function gets a **copy**.

```
void change(int x) {     
	x = 10; 
}  

int main() {     
	int a = 5;     
	change(a);     
	// a is still 5 
}
```

➡️ `a` does **not** change, because `x` is just a copy.
## 2. Why pass a pointer?

When you pass a **pointer**, you pass the **address** of the variable.  
This allows the function to work on the **original variable**.

```
void change(int *x) {     
	*x = 10; 
}  

int main() {     
	int a = 5;     
	change(&a);     
	// a is now 10 
}
```

➡️ The function can now **modify `a` directly**.