# while loop :
The while loop repeat a block of code an unlimited amount of time as the condition is meat.
Example :
```
>>> number = 5

>>> while number > 0:
...     print(number)
...     number -= 1
...
5
4
3
2
1
```

You can also add an else clause in while loops that executes when the while loop finish naturally without break sentence. example :
```
while condition:
    <body>
else:
    <body>
```

# For loop :
For loops executes a block of code a fixed amount of  time.
syntax :
```
for variable in iterable:
    <body>
```
example :
```
>>> colors = ["red", "green", "blue", "yellow"]

>>> for color in colors:
...     print(color)
...
red
green
blue
yellow
```
Else clause can be used to execute a block of code if the for loop terminate normally without break statement :
```
>>> numbers = [1, 3, 5, 7, 9]
>>> target = 42

>>> for number in numbers:
...     print(f"Processing {number}...")
...     if number == target:
...         print(f"Target found {target}!")
...         break
... else:
...     print(f"Target not found {target}")
...
Processing 1...
Processing 3...
Processing 5...
Processing 7...
Processing 9...
Target not found 42
```

Another example :
```
>>> fruits = ["orange", "apple", "mango", "lemon"]

>>> for index in range(len(fruits)):
...     fruit = fruits[index]
...     print(index, fruit)
...
0 orange
1 apple
2 mango
3 lemon
```
## Nested for loops :
Nested for loop is a for loop inside a for loop :
```
>>> for number in range(1, 11):
...     for product in range(number, number * 11, number):
...         print(f"{product:>4d}", end="")
...     print()
...
   1   2   3   4   5   6   7   8   9  10
   2   4   6   8  10  12  14  16  18  20
   3   6   9  12  15  18  21  24  27  30
   4   8  12  16  20  24  28  32  36  40
   5  10  15  20  25  30  35  40  45  50
   6  12  18  24  30  36  42  48  54  60
   7  14  21  28  35  42  49  56  63  70
   8  16  24  32  40  48  56  64  72  80
   9  18  27  36  45  54  63  72  81  90
  10  20  30  40  50  60  70  80  90 100
```
