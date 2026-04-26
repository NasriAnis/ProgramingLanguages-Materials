All elements has to have the same type, and in rust arrays have fixed size.

```
let a = [1, 2, 3, 4, 5];
```

Data inside arrays are allocated in the stack (as the other previous types) rather than the heap.

(A vector is a similar collection type provided by the standard library that _is_ allowed to grow or shrink in size because its contents live on the heap.)

we can write array types this way :

```
let a: [i32; 5] = [1, 2, 3, 4, 5];
```

we can initialize an array by specifying the initial value, followed by a semicolon, and then the length of the array in square brackets :

```
let a = [3; 5];
// same as : let a = [3, 3, 3, 3, 3];
```

## Array element access

```
let a = [1, 2, 3, 4, 5]; 

let first = a[0]; 
let second = a[1];
```

## Invalid array element access

When you attempt to access an element using indexing, Rust will check that the index you’ve specified is less than the array length. If the index is greater than or equal to the length, Rust will panic. This check has to happen at runtime, especially in this case, because the compiler can’t possibly know what value a user will enter when they run the code later.