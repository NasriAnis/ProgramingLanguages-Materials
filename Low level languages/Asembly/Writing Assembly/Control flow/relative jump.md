Here, we are focusing on relative jumps. This means you will tell the CPU to “jump forward a certain number of bytes from where you are currently executing.” This is useful because your code can move in memory and the jump will still reach the correct target.

To implement a relative jump, you will need a few tools:
- `labels`: Instead of calculating addresses manually, you can use labels as placeholders. The assembler will automatically calculate the offset from your jump instruction to the label.
- `nop` (No Operation): A single-byte instruction that does nothing. It is predictable in size and can be used as filler to create an exact distance for your jump.
- `.rept` (Repeat Directive): A directive that tells the assembler to repeat a given instruction multiple times: [GNU Assembler Manual](https://ftp.gnu.org/old-gnu/Manuals/gas-2.9.1/html_chapter/as_7.html) This is perfect for generating a block of `nop` instructions without typing each one individually.

[site](https://ftp.gnu.org/old-gnu/Manuals/gas-2.9.1/html_chapter/as_toc.html#TOC116)

Repeat the sequence of lines between the `.rept` directive and the next `.endr` directive count times.

For example, assembling
```
.rept   3
.long   0
.endr
```

is equivalent to assembling
```
.long   0
.long   0
.long   0
```
