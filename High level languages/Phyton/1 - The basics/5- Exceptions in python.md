# The Raise and Assert keyword :
## Raising an exception :
There are scenarios where you might want to stop your program by raising an exception if a condition occurs. You can do this with the `raise` keyword during the production of the code.
example :
```
number = 10
if number > 5:
    raise Exception(f"The number should not exceed 5. ({number=})")
print(number)
```

```
```
When run this code will show a custom message (The number should not exceed 5. ({number=})
## Debugging with the `assertion` keyword :
As the `raise` keyword the `assert` is used without conditional statement and not used in production.
example :
```
number = 10
assert (number < 5), f"The number should not exceed 5. ({number=})"
print(number)
```

# Handling exception with `try`, `exept`,`else` and `finally`  block :
In Python, you use the `try` and `except` block to catch and handle exceptions. Python executes code following the `try` statement as a normal part of the program. The code that follows the `except` statement is the program’s response to any exceptions in the preceding `try` clause. The `else` statement is not obligatory and put at the end of the `try exept` clause and executes only when no `exept` is run.
![](../../../zzDocument/try_except_else_finally.a7fac6c36c55.avif)
example:
```
x = input("Choose a number : ")
try:
result = 5/x
except ZeroDivisionError:
x = input("you cant devise by 0, choose another number : ")
else:
print(result)
print("operation finished sucesfully")
```

# Creating custom exceptions :
