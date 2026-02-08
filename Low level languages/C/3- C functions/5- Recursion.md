Recursion is the technique of making a function call itself. This technique provides a way to break complicated problems down into simple problems which are easier to solve.

```c
#include <stdio.h>

int sum(int k);

int main() {
  int result = sum(10);
  printf("%d", result);
  return 0;
}

int sum(int k) {
  if (k > 0) {
    return k + sum(k - 1);
  } else {
    return 0;
  }
}
```

```c
#include <stdio.h>

void countdown(int n);

int main() {
  countdown(5);
  return 0;
}

void countdown(int n) {
  if (n > 0) {
    printf("%d ", n);
    countdown(n - 1);
  }
}
```
