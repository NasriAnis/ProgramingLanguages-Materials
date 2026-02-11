A function stack frame is a set of pointers and values pushed onto the stack to save things for later use and allocate space on the stack for function variables.

First, let's talk about the special register `rbp`, the Stack Base Pointer.

The `rbp` register is used to tell where our stack frame first started. As an example, say we want to construct some list (a contiguous space of memory) that is only used in our function. The list is 5 elements long, and each element is a `dword`. A list of 5 elements would already take 5 registers, so instead, we can make space on the stack!

The assembly would look like:

```assembly
; setup the base of the stack as the current top
mov rbp, rsp
; move the stack 0x14 bytes (5 * 4) down
; acts as an allocation
sub rsp, 0x14
; assign list[2] = 1337
mov eax, 1337
mov [rbp-0xc], eax
; do more operations on the list ...
; restore the allocated space
mov rsp, rbp
ret
```

Notice how `rbp` is always used to restore the stack to where it originally was. If we don't restore the stack after use, we will eventually run out. In addition, notice how we subtracted from `rsp`, because the stack grows down. To make the stack have more space, we subtract the space we need. The `ret` and `call` still work the same.

Consider the fact that to assign a value to `list[2]` we subtract 12 bytes (3 dwords). That is because the stack grows down and when we moved `rsp` our stack contains addresses <`rsp`, `rbp`.