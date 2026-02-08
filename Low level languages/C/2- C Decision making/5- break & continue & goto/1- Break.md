The break statement is used to break out of a loop.
```
#include <stdio.h>

int main() {
  int i;
  
  for (i = 0; i < 10; i++) {
    if (i == 4) {
      break;
    }
    printf("%d\n", i);
  }
   
  return 0;
}
```
