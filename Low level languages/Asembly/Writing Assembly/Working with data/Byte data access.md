## Load upper byte
Each register in x86_64 is 64 bits in size, and in the previous levels, we have accessed the full register using `rax`, `rdi`, or `rsi`.

We can also access the lower bytes of each register using different register names.

For example, the lower 32 bits of `rax` can be accessed using `eax`, the lower 16 bits using `ax`, and the lower 8 bits using `al`.

![Pasted image 20260111084813](../../../../zfiles/Pasted%20image%2020260111084813.png)
## Byte extraction
x86 allows you to 'shift' bits around in a register.
Take, for instance, `al`, the lowest 8 (or _least significant_ 8) bits of `rax`.

The value in `al` (in bits) is:
```
al = 10001010
```

If we shift once to the left using the `shl` instruction:
```
shl al, 1
```

The new value is:
```
al = 00010100
```

Everything shifted to the left, and the highest (or _most significant_) bit fell off while a new 0 was added to the right side.

Shifting has the nice side effect of doing quick multiplication (by 2) or division (by 2), and can also be used to compute modulo.

Recall that registers in x86_64 are 64 bits wide, meaning they can store 64 bits. Similarly, each memory location can be treated as a 64-bit value. We refer to something that is 64 bits (8 bytes) as a quad word.
# Loading appropriate amount of data to register
Here is the breakdown of the names of memory sizes:

- Quad Word = 8 Bytes = 64 bits
- Double Word = 4 bytes = 32 bits
- Word = 2 bytes = 16 bits
- Byte = 1 byte = 8 bits

In x86_64, you can access each of these sizes when dereferencing an address, just like using bigger or smaller register accesses:

- `mov al, [address]` <=> moves the least significant byte from address to `rax`
- `mov ax, [address]` <=> moves the least significant word from address to `rax`
- `mov eax, [address]` <=> moves the least significant double word from address to `rax`
- `mov rax, [address]` <=> moves the full quad word from address to `rax`

Remember that moving into `al` does not fully clear the upper bytes.
# Memory sum (offset)
Recall that memory is stored linearly.

What does that mean?

Say we access the quad word at `0x1337`:

```
[0x1337] = 0x00000000deadbeef
```

The real way memory is laid out is byte by byte, little endian:

```
[0x1337] = 0xef
[0x1337 + 1] = 0xbe
[0x1337 + 2] = 0xad
...
[0x1337 + 7] = 0x00
```

What does this do for us?

Well, it means that we can access things next to each other using offsets, similar to what was shown above.

Say you want the 5th _byte_ from an address, you can access it like:

```
mov al, [address+4]
```

Remember, offsets start at 0.

#### example:
Perform the following:
- Load two consecutive quad words from the address stored in `rdi`.
- Calculate the sum of the previous steps' quad words.
- Store the sum at the address in `rsi`.

```
We will now set the following in preparation for your code:
  [0x4042f0] = 0xe385a
  [0x4042f8] = 0x90f6e
  rdi = 0x4042f0
  rsi = 0x4046c0

Extracting binary code from provided ELF file...
Executing your code...
---------------- CODE ----------------
0x400000:	mov   	rax, qword ptr [rdi]
0x400003:	add   	rax, qword ptr [rdi + 8]
0x400007:	mov   	qword ptr [rsi], rax
--------------------------------------
```
