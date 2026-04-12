When accessing memory the CPU fetches more data from the area where the intended data is fetched this all is stored into the cache of the CPU that is much faster than RAM.

When accessing memory this parameter is important to take into consideration looking at this program : 

```
#include <stdio.h>
#include <time.h>
#include <stdlib.h>

typedef struct {
  int rows, col;
  float* data;
} matrix;

#define SIZE 3000

float sum1(matrix *a){
  float sum = 0.0f;

  for (int rows = 0; rows < a->rows; rows++){
    for (int columns = 0; columns < a->col; columns++){
      sum += a->data[columns + rows * a->col];
    }
  }
  return sum;
}

float sum2(matrix *a){
  float sum = 0.0f;

  for (int columns = 0; columns < a->col; columns++){
    for (int rows = 0; rows < a->rows; rows++){
      sum += a->data[columns + rows * a->col];
    }
  }
  return sum;
}

int main(){
  matrix a = {SIZE, SIZE};
  a.data = (float*)malloc(SIZE * SIZE * sizeof(float));

  for (int i = 0; i < SIZE * SIZE; i++){
    a.data[i] = (float)rand() / (float)RAND_MAX;
  }

  clock_t t1 = clock();
  for (int i = 0; i < 100; i++) sum1(&a);
  printf("sum1 (friendly):   %.3fs\n", (double)(clock()-t1)/CLOCKS_PER_SEC);

  clock_t t2 = clock();
  for (int i = 0; i < 100; i++) sum2(&a);
  printf("sum2 (unfriendly): %.3fs\n", (double)(clock()-t2)/CLOCKS_PER_SEC);

  free(a.data);
  return 0;
}
```

there we have two functions that accesses a matrix in memory in 2 different way, the first one accesses it by rows and the other by columns (recall that matrices are stored linearly in memory). when accessing it by rows the functions access memory in order from right to left so it encounter the less cache misses since the data it try to fetches is always cache, but in the case of `sum2` it accesses memory a bit out of order it does some jumps so it encounter every time a cache miss the cache fetched from memory is not used.

After running this program we can see the differences :
![](../../zzDocument/Pasted%20image%2020260412150146.png)