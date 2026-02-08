The `continue` statement breaks one iteration (in the loop), if a specified condition occurs, and continues with the next iteration in the loop.

```
#include <stdio.h>

int main() {
  int i;
  
  for (i = 0; i < 10; i++) {
    if (i == 4) {
      continue;
    }
    printf("%d\n", i);
  }   
  
  return 0;
}
```

0  
1  
2  
3  
5  
6  
7
8
9