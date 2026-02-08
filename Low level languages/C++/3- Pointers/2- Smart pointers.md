A smart pointer is a class template that wraps around a raw pointer, it is used in memory management to clear the dynamically allocated memory automatically when it is no longer needed. T prevent memory leaks and dangling pointers.
## Types of smart pointers
we need to use the `<memory>` header to use smart pointers :
- `auto_ptr`
- `unique_ptr`
- `shared_ptr`
- `weak_ptr`
