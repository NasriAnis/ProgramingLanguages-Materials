# Loop through an array
```
#include <stdio.h>
int main(){

    int myarray[] = {1, 2, 3, 4};
    int i;

    for (i=0; i < sizeof(myarray) / sizeof(myarray[0]); i++) {
        printf("%d\n", myarray[i]);
    }
    return 0;

}
```

