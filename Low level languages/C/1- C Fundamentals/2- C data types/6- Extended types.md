Besides the basic types (`int`, `float`, `double`, `char`), C also gives you **extended keywords** (`short`, `long`, `unsigned`) to control how large the number is, or whether it can be negative:

|Type|Size*|Range (commonly)|Format Specifier|
|---|---|---|---|
|`short int`|2 bytes|-32,768 to 32,767|`%hd`|
|`unsigned int`|2 or 4 bytes|0 to 65,535 (2 bytes)  <br>0 to 4,294,967,295 (4 bytes)|`%u`|
|`long int`|4 or 8 bytes|-2,147,483,648 to 2,147,483,647 (4 bytes)  <br>-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 (8 bytes)|`%ld`|
|`long long int`|8 bytes|-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807|`%lld`|
|`unsigned long int`|4 or 8 bytes|0 to 4,294,967,295 (4 bytes)  <br>0 to 18,446,744,073,709,551,615 (8 bytes)|`%lu`|
|`unsigned long long int`|8 bytes|0 to 18,446,744,073,709,551,615|`%llu`|
|`long double`|8, 12, or 16 bytes|Implementation-dependent, but more precision than `double`|`%Lf`|

`unsigned` means the type can only store non negative values from 0 to infinity

Example :
```
int normalInt = 1000;                       // standard int 
double normalDouble = 3.14;                 // standard double

short int small = -100;                     // smaller int
unsigned int count = 25;                    // only positive int
long int big = 1234567890;                  // larger int
long long int veryBig = 9223372036854775807; // very large int
unsigned long long int huge = 18446744073709551615U; // very large, only positive
long double precise = 3.141592653589793238L; // extended precision

printf("Normal int: %d\n", normalInt);
printf("Normal double: %lf\n", normalDouble);
printf("Small: %hd\n", small);
printf("Count: %u\n", count);
printf("Big: %ld\n", big);
printf("Very Big: %lld\n", veryBig);
printf("Huge: %llu\n", huge);
printf("Precise: %Lf\n", precise);
```

These extended types are mostly used when you need very specific control over memory usage or number ranges.

```
printf("Size of int: %zu bytes\n", sizeof(int));
printf("Size of double: %zu bytes\n", sizeof(double));
printf("Size of short int: %zu bytes\n", sizeof(short int));
printf("Size of unsigned int: %zu bytes\n", sizeof(unsigned int));
printf("Size of long int: %zu bytes\n", sizeof(long int));
printf("Size of long long int: %zu bytes\n", sizeof(long long int));
printf("Size of unsigned long long int: %zu bytes\n", sizeof(unsigned long long int));
printf("Size of long double: %zu bytes\n", sizeof(long double));

Size of int: 4 bytes
Size of double: 8 bytes
Size of short int: 2 bytes
Size of unsigned int: 4 bytes
Size of long int: 4 bytes
Size of long long int: 8 bytes
Size of unsigned long long int: 8 bytes
Size of long double: 16 bytes
```

note : fixed width types for exact control