you can also access the stack directly using the stack pointer.

On x86, the stack pointer is stored in the special register, `rsp`. `rsp` always stores the memory address of the top of the stack, i.e., the memory address of the last value pushed.

Similar to the memory levels, we can use `[rsp]` to access the value at the memory address in `rsp`.

example:
```
mov rbx, [rsp]        ; First value
mov rax, [rsp+0x8]    ; Second value
mov rdx, [rsp+0x10]   ; Third value (0x10 = 16)
mov rcx, [rsp+0x18]   ; Fourth value (0x18 = 24)

add rdx, rcx          ; Summing values...
add rdx, rbx
add rax, rdx          ; Final sum is now in RAX

; Preparation for division (RAX / 4)
mov rcx, 4            ; Move divisor into a register
xor rdx, rdx          ; Clear RDX (IMPORTANT: div uses RDX:RAX)
div rcx               ; RAX = RAX / RCX

push rax              ; Push result back to stack
```