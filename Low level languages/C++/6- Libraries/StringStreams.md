https://www.geeksforgeeks.org/cpp/stringstream-c-applications/
https://cplusplus.com/reference/sstream/stringstream/

using string streams through the `<sstream>` library help in storing input to a stream then extracting data with `>>` to a variable or file (the data will not be available on the stream) and with `<<` it stores it to the steam.

it could also help transform different data type.

example:
```
#include <iostream>   
#include <sstream>    

using namespace std;

int main() {
    string str = "123";   
    int num;              
    // Create a stringstream object initialized with 'str'
    stringstream ss(str);                     
    // Extract an integer from the stringstream and store it in 'num'
    ss >> num;            
    cout << "Integer: " << num << endl;  

    return 0;             
}
```

```
#include <iostream>
#include <sstream>
using namespace std;

int main() {
    stringstream ss;

    // Put some data into the stringstream
    ss << "Hello, world!";
    cout << "Before clearing: " << ss.str() << endl;

    // Clear the contents of the stringstream
    ss.str("");     

    // Reset the stringstream's state flags (like eof, fail)
    ss.clear();      

    // Now we can reuse the stringstream for new data
    ss << "New data here!";
    cout << "After clearing and reuse: " << ss.str() << endl;

    return 0;
}
```

```
#include <iostream>
#include <vector>
#include <sstream>
using namespace std;

int main(){
	std::string s;
	std::cin >> s;

	stringstream ss;
	ss.str(s);

	vector<int> numbers;
	int value;
	char buffer;

	while (ss >> value) {
		numbers.push_back(value);
		ss >> buffer;
	}

	for (int n : numbers){
		cout << n << endl;
	}
	
	return 0;
}
```