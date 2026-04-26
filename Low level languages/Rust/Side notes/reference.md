the `&` indicates that this argument is a _reference_, which gives you a way to let multiple parts of your code access one piece of data without needing to copy that data into memory multiple times.

```
io::stdin()
	.read_line(&mut guess)
```

references are immutable by default. Hence, you need to write `&mut guess` rather than `&guess` to make it mutable.