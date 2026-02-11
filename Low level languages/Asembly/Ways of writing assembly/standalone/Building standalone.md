#### `asm` format
First we need to specify the type of `asm` that we are using and that by placing for example `.intel_syntax noprefix` at the head of our program
#### `asm` to an object file
To assemble the code we use the `as` assembler : `as -o program.o program.s`
This object file has actual assembled binary code, but it is not yet ready to be run. First, we need to _link_ it.
#### Linking object file to an executable
In a typical development workflow, source code is compiled and assembly is assembled to object files, and there are typically many of these (generally, each source code file in a program compiles into its own object file). These are then _linked_ together into a single executable. Even if there is only one file, we still need to link it, to prepare the final executable. This is done with the `ld` (stemming from the term "**l**ink e**d**itor") command.

`ld -o program program.o`

This creates an `program` file that we can then run! Here it is:
```console
hacker@dojo:~$ ./program
hacker@dojo:~$ echo $?
42
hacker@dojo:~$
```

In the shell, `$?` holds the exit code of the last executed command.
#### `_start`
The `_start` symbol is, essentially, a note to `ld` about where in your program execution should begin when the ELF is executed.

```
hacker@dojo:~$ cat program.s 
.intel_syntax noprefix 
.global _start 
_start: 
mov rdi, 42 
mov rax, 60 
syscall 
hacker@dojo:~$ as -o program.o program.s 
hacker@dojo:~$ ld -o program program.o 
hacker@dojo:~$ ./program 
hacker@dojo:~$ echo $? 42 
hacker@dojo:~$
```

 The second, `_start:`, adds a _label_ called start, pointing to the beginning of your code. The first, `.global _start`, directs `as` to make the `_start` label _globally visible_ at the linker level, instead of just locally visible at the object file level. As `ld` is the linker, this directive is necessary for the `_start` label to be seen. 