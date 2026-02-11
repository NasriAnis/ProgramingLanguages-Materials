![](../../../../../zzDocument/Pasted%20image%2020251223131729.png)

example:
```
#include <stdio.h>
void main(){
    long long myVar = 0x00112233aabbccdd;
    asm("nop");
    // value into register from C variable
    asm("mv t0, %0" : : "r" (myVar));
    // it's a surprise ;)
    asm(".word 0x12328293");
    // value into C variable from register
    asm("mv %0, t0" : "=r" (myVar));
    asm("nop");
    printf("myVar = %llx\n", myVar);
}
```

![](../../../../../zzDocument/Pasted%20image%2020251223131843.png)

