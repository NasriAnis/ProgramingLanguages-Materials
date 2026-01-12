https://cplusplus.com/reference/vector/vector/

```
#include <stdio.h>
#include <iostream>
#include <vector>
using namespace std;

int main(){
	int n, q, l, size_sub, _n, k;
	
	scanf("%d %d", &n, &q);
	
	vector<vector<int>> arr(n); // create array of subarrays
	
	for (int i = 0; i < n; i++){ // create subarrays of lenght k[0]
		if (!(std::cin >> size_sub)) return 1;
	
		std::vector<int> numbers(size_sub);
	
		for (int j = 0; j < size_sub; ++j) {
			std::cin >> numbers[j];
		}
	
	arr[i] = numbers;
	}
	
	vector<int> result(q + 1);
	
	for (int z = 0; z < q; z++){
		scanf("%d %d", &_n, &k);
		//printf("%d\n", arr[_n][k]);
		result[z] = arr[_n][k];
	}
	
	for (int w = 0; w < q; w++){
		printf("%d\n", result[w]);
	}
	
	return 0;
}
```