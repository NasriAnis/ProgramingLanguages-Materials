C has many string functions which used to perform various operations on strings to use them we must include `<string.h>`.
# String length
To get the length of a string the `strlen()` is used.
```
char alphabet[] = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";  
printf("%zu", strlen(alphabet));
```
# Concatenate strings
To concatenate (combine) two strings we use the `strcat()` function.
```
char str1[20] = "Hello ";  
char str2[] = "World!";  
  
// Concatenate str2 to str1 (result is stored in str1)  
strcat(str1, str2);  
  
// Print str1  
printf("%s", str1);
```
# Copy strings
we use the `strcpy()`.
```
char str1[20] = "Hello World!";  
char str2[20];  
  
// Copy str1 to str2  
strcpy(str2, str1);  
  
// Print str2  
printf("%s", str2);
```
# Compare strings
we use the `strcmp()`, it returns 0 if the two strings are equal otherwise the value is not 0.
```
char str1[] = "Hello";  
char str2[] = "Hello";  
char str3[] = "Hi";  
  
// Compare str1 and str2, and print the result  
printf("%d\n", strcmp(str1, str2));  // Returns 0 (the strings are equal)  
  
// Compare str1 and str3, and print the result  
printf("%d\n", strcmp(str1, str3));  // Returns -4 (the strings are not equal)
```
