the most basic form is: am("instructions separated by \n");

![](../../../../../zzDocument/Pasted%20image%2020251223130025.png)

how to use c variables:
![](../../../../../zzDocument/Pasted%20image%2020251223130225.png)

example:
```
#include <stdio.h>
void main(){
    long long myVar = 0x00112233aabbccdd;
    asm("nop");
    // value into register from C variable
    asm("mv t0, %0" : : "r" (myVar)); // That's not valid RISC-V asm!!! // r is for register specifier
    // change value
    asm("addi t0, t0, 0x123");
    // value into C variable from register
    asm("mv %0, t0" : "=r" (myVar)); // That's not valid RISC-V asm!!!
    asm("nop");
    printf("myVar = %llx\n", myVar);
}
```

![](../../../../../zzDocument/Pasted%20image%2020251223130744.png)

```
#include <stdio.h>
void main(){
    long long myVar = 0x00112233aabbccdd;
    asm("nop");
    // alt value into register from C variable
    asm("ld t0, %0" : : "m" (myVar)); // m for memory value
    // change value
    asm("addi t0, t0, 0x123");
    // alt value into C variable from register
    asm("sd t0, %0" : "=m" (myVar));
    asm("nop");
    printf("myVar = %llx\n", myVar);
}
```

![](../../../../../zzDocument/Pasted%20image%2020251223131011.png)

note: The `%llx` format specifier in C is used to print an **`unsigned long long int`** in **hexadecimal** format


```
#include <stdio.h>
#include <stdlib.h>
void main(int argc, char ** argv){
    long long myVar = strtoll(argv[1], NULL, 16);
    asm("nop");
    // alt way to get value into register from C variable
    asm("ld t0, %0" : : "m" (myVar));
    asm("bgtz t0, target1"); // target for he jump
    printf("myVar = %llx is less than or equal zero\n", myVar);
    asm("j target2");
    asm("target1:");
    printf("myVar = %llx is greater than zero\n", myVar);
    asm("target2:");
    asm("nop");
}
```

![](../../../../../zzDocument/Pasted%20image%2020251223131421.png)
