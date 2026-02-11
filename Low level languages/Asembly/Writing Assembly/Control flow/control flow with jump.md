This involves using instructions to both indirectly and directly control the special register `rip`, the instruction pointer. using instructions such as `jmp`, `call`, `cmp`, and their alternatives to implement the requested behavior.

There are two major ways to manipulate control flow:
- Through a jump
- Through a call
## jump
There are two types of jumps:
- Unconditional jumps
- Conditional jumps
#### Unconditional
Unconditional jumps always trigger and are not based on the results of earlier instructions.

For all jumps, there are three types:
- Relative jumps: jump + or - the next instruction.
- Absolute jumps: jump to a specific address.
- Indirect jumps: jump to the memory address specified in a register.
##### Absolute
In x86, absolute jumps (jump to a specific address) are accomplished by first loading the target address into a general-purpose register (we'll call this placeholder `reg`), then doing `jmp reg`
