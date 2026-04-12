First lets talk about the difference between signed and unsigned integer, an unsigned type only stores non negatives whole numbers where as signed stores both negative and positive ones. Negative value are stored in a [twos complement][https://en.wikipedia.org/wiki/Two%27s_complement#Procedure] way.

Now look at this code :

```
int main(){
	int size;
	char buf[16];
	scanf("%i", size);
	if (size > 16) { exit 0; }
	read(0, buff, size);
}
```

we can spot a vulnerability, the `int` is an signed integer so entering `-1` will result into bypassing the `if` statement that protects against buffer overflow `-1<16` this is because it is computed using the twos complement way in reality it is stored as `0xffff` (if in a 32 bit system), however the `size` type in the `read` function is `size_t` which makes `size` being computed as an unsigned value this makes the stored value being read as an unsigned value thus `0xffff` that is equal to `65535`.

this part is `if (size > 16) { exit 0; }` treated as a signed comparison which result into different assembly instruction :
![](../../../zzDocument/Pasted%20image%2020260409150846.png)

we can see it in the disassembly :
![](../../../zzDocument/Pasted%20image%2020260409151204.png)