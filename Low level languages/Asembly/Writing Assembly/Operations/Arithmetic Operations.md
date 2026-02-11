## Note
this:
```
RAX:EDX
```
mean that one is the higher bit and the other the lower bit.
## Multiplication
in multiplication for x86-64:
```
mul
imul
```
### `mul` unsigned multiply
`mul` takes only one operand and multiply it with the value in `al / ax / eax / rax`

| Instruction | Actual operation | Result stored in |
| ----------- | ---------------- | ---------------- |
| `mul r/m8`  | `AL × r/m8`      | `AX`             |
| `mul r/m16` | `AX × r/m16`     | `DX:AX`          |
| `mul r/m32` | `EAX × r/m32`    | `EDX:EAX`        |
| `mul r/m64` | `RAX × r/m64`    | `RDX:RAX`        |
### `imul` signed multiply
takes 2 operands or even 3

|Operand size|Multiply|Result stored in|
|---|---|---|
|8-bit|AL × r/m8|AX|
|16-bit|AX × r/m16|DX:AX|
|32-bit|EAX × r/m32|EDX:EAX|
|64-bit|RAX × r/m64|RDX:RAX|
## Division
`div` is a special instruction that can divide a 128-bit dividend by a 64-bit divisor while storing both the quotient and the remainder, using only one register as an operand.

The relevant instructions for this level are:
- `mov rax, reg1`
- `div reg2`

For the instruction `div reg2`, the following happens:
- `rax = rdx:rax / reg2`
- `rdx = remainder`

`rdx:rax` means that `rdx` will be the upper 64-bits of the 128-bit dividend and `rax` will be the lower 64-bits of the 128-bit dividend.

You must be careful about what is in `rdx` and `rax` before you call `div`. Note that distance will be at most a 64-bit value, so `rdx` should be 0 when dividing.

example:
- `speed = distance / time`, where:
    - `distance = rdi`
    - `time = rsi`
    - `speed = rax`

```
.intel_syntax noprefix
.global _start
_start:
mov rax, rdi
mov rdx, 0
div rsi
```
### Modulo
`x86` allows you to get the remainder after a `div` operation.
For instance: `10 / 3` results in a remainder of `1`. from `rdx` in using the `div` operator.
## Efficient modulo
It turns out that using the `div` operator to compute the modulo operation is slow!

We can use a math trick to optimize the modulo operator (`%`). Compilers use this trick a lot.

If we have `x % y`, and `y` is a power of 2, such as `2^n`, the result will be the lower `n` bits of `x`.

Therefore, we can use the lower register byte access to efficiently implement modulo!