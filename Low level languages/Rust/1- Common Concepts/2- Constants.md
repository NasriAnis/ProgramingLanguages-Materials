Constant are value that are bounded to a name. Constant are declared using the `const` keyword and the type of the value must be annotated.

```
const THREE_HOURS_IN_SECS: u32 = 60 * 60 * 3;
```

A constant is more like an alias for a value the name only exists in source code. By the time the program runs, the name is gone and the value is just baked in directly wherever you used it.

The value of a constant is known at compile time.