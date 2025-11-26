# Initialize array of pointers using static keyword
You can also use the static keyword to initialize an array of pointers to store "0" in each subscript.

```
#include <stdio.h> 
int main(){ 
	static int *ptr[5]; 
	for (int i = 0; i < 5; i++){ 
		printf("ptr[%d] = %d\n", i, ptr[i]); 
		} 
	return 0;
}

ptr[0]= 0
ptr[1]= 0
ptr[2]= 0
ptr[3]= 0
ptr[4]= 0
```
# Initialize array of integer pointers
Here, we declare an array of integer pointers and store the addresses of three integer variables.
```
#include <stdio.h> 
int main(){ 
	int a = 10, b = 20, c = 30; 
	int *ptr[3] = {&a, &b, &c}; 
	for (int i = 0; i < 3; i++){ 
		printf("ptr[%d]: address: %d value: %d\n", i, ptr[i], *ptr[i]); 
	} 
	return 0; 
}

ptr[0]: address: 6422040 value: 10
ptr[1]: address: 6422036 value: 20
ptr[2]: address: 6422032 value: 30
```
# Initialize array of pointer by direct addresses
We can store the address of each element of a normal array in the corresponding element of a pointer array.
```
#include <stdio.h> 

int main(){ 
	int arr[] = {10, 20, 30}; 
	int *ptr[3] = {&arr[0], &arr[1], &arr[2]}; 
	for (int i = 0; i < 3; i++){
		 printf("ptr[%d]: address: %d value: %d\n", i, ptr[i], *ptr[i]);
		  } 
		return 0; 
}

ptr[0]: address: 6422032 value: 10
ptr[1]: address: 6422036 value: 20
ptr[2]: address: 6422040 value: 30
```

finish from : https://www.tutorialspoint.com/cprogramming/c_initialization_of_pointer_arrays.htm