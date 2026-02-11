## Check if a number is odd or even
Using only the following instructions:
  and, or, xor

Implement the following logic:
```
  if x is even then
    y = 1
  else
    y = 0
```

where:
```
  x = rdi
  y = rax
```

```
---------------- CODE ----------------
0x400000:	xor   	rax, rax
0x400003:	or    	rax, rdi
0x400006:	and   	rax, 1
0x40000a:	xor   	rax, 1
```