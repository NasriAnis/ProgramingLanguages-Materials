the `#define` is a processor macro, this happens before the compiler sees the code. the processor literally replaces the text with the value you assigned with everywhere in the code like a copy paste. in addition it has no type because the compiler doesn't sees it as a variable so no memory allocation, no type checking and faster.

the const in the other hand creates a real variable stored in memory

| Feature              | `#define`          | `const`                                     |
| -------------------- | ------------------ | ------------------------------------------- |
| Type?                | ❌ None (text only) | ✔ Has a type (`int`, `float`, etc.)         |
| Allocates memory?    | ❌ No               | ✔ Yes                                       |
| Visible to debugger? | ❌ No               | ✔ Yes                                       |
| Checked by compiler? | ❌ No               | ✔ Yes                                       |
| Scope?               | Global everywhere  | Block/local/global depending on declaration |
| Can be modified?     | Not applicable     | Read-only (compiler-enforced)               |
| Safe?                | ❌ Many pitfalls    | ✔ Much safer                                |
### Use `#define` for:
- Header guards
- Conditional compilation
- Simple numeric constants for old C90 code
- Macros that must be expanded at compile time only
### Use `const` for:
- Any value that has a type
- Safer constante
- Local constants inside functions
- Variables that should be read-only
- Anything involving pointers