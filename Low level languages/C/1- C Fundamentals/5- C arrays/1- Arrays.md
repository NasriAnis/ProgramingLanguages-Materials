Arrays are used to store multiple values instead of declaring separate variables for each value, to create an array we define first the data type and specify the name of the array followed by square brackets.
```
int myNumbers[] = {25, 50, 75, 100};
```

# Access element 
To access element of an array we refer to its index number.
```
int myNumbers[] = {25, 50, 75, 100};  
printf("%d", myNumbers[0]);  
  
// Outputs 25
```
# Change array element
To change a specific element we refer to its index.
```
myNumbers[0] = 33;
```
# Set array size
```
// Declare an array of four integers:  
int myNumbers[4];  
  
// Add elements  
myNumbers[0] = 25;  
myNumbers[1] = 50;  
myNumbers[2] = 75;  
myNumbers[3] = 100;
```


Element inside arrays must be the same data type!