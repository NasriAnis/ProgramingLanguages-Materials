# Basic syntax :
example : 
```
def function_name([parameters]):
    <block>
```
# Calling functions :
## Positional Arguments :
The quickest way to call a function with arguments is to rely on the specific position of each argument. In this case, you’ll be using what’s known as **positional arguments**.
example :
```
def calculate_cost(item, quantity, price):

print(f"{quantity} {item} cost ${quantity * price:.2f}")

x = input("Choose item : ")
y = int(input("Choose the quantity : "))
z = float(input("Choose the price : "))

calculate_cost(x, y, z)
```
## Key word arguments :
When calling a function, you can specify arguments in the form `argument=value`.
example : 
```
def calculate_cost(item, quantity, price):

print(f"{quantity} {item} cost ${quantity * price:.2f}")

x = input("Choose item : ")
y = int(input("Choose the quantity : "))
z = float(input("Choose the price : "))

calculate_cost(price = z, quantity = y, item = x)
```
# Side effects of functions :
## Producing a side effect :
This by modifying a global variable within the function.
example : this function produce a side effect on global variable `numbers`.
```
def double(numbers):
     for i, _ in enumerate(numbers):
         numbers[i] *= 2

numbers = [1, 2, 3, 4, 5]
double(numbers)
print(numbers)
```
To avoid this side effect the function can be written in another way :
```
def double(numbers):
     result = []
     for number in numbers:
         result.append(number * 2)
     return result

numbers = [1, 2, 3, 4, 5]
double_numbers = double(numbers)

print(numbers)
print(double_numbers)
```
Here the doubles are stocked in a specific variable other than the `numbers` variable.
## Returning a value :
1 - The `return` statement is used only inside a function and returns back a certain value, the `return` statement can be followed by 0, 1, 2 etc. expressions separates by comas.
example :
```
def create_point(x, y):
     return x, y
     
print(create_point(2, 4))
```
If you specify multiple comma-separated expressions in a `return` statement, then they’re packed and returned as a `tuple` object, as shown in the example above.
2 - The `return` statement can also be used to return another function.
example : 
```
def as_dict():
    return dict(one=1, two=2, three=3)
    
print(as_dict())
print(as_dict()["two"])
```
other example :
```
user_list = [ {"username" : "anis", "email" : "anisnasri322@gmail.com"},
             {"username" : "asma", "email" : "asmanasri322@gmail.com"} ]

def user_serarch(username, users):
    for user in users:
     if username == user["username"]:
        print(user)
        return user
    return None
    
user_serarch("anis", user_list)
```
- other way to return a none value :
```
user_list = [ {"username" : "anis", "email" : "anisnasri322@gmail.com"},
             {"username" : "asma", "email" : "asmanasri322@gmail.com"} ]

def user_serarch(username, users):
    for user in users:
     if username == user["username"]:
        print(user)
        return user
    return None

if user_serarch("anis", user_list) is not None:
     print("succesful operation")
elif user_serarch("anis", user_list) is None:
     print("anis is unavailable")

if user_serarch("rafik", user_list) is not None:
     print("succesful operation")
elif user_serarch("rafik", user_list) is None:
     print("rafik is unavailable")
```
## Exiting function early :
Using the `return` function to exit a function as an example :
```
from pathlib import Path

def read_file_contents(file_path):
    path = Path(file_path)
    
    if not path.exists():
        print(f"Error: The file '{file_path}' does not exist.")
        return
    
    if not path.is_file():
        print(f"Error: '{file_path}' is not a file.")
        return
        
    return path.read_text(encoding="utf-8")
```
for example when the first if statement is executed do to the absence of the file, the return at the end of the if statement terminate the function.
## Return Boolean value :
With the `return` function you can return a Boolean value.
example :
```
def is_even(number):
     return number % 2 == 0

print(is_even(5))
#False

print(is_even(4))
#True
```
## Returning Generator Iterators, The `yield` function :
using the `yield` in a function make it more memory efficient because it computes on demand and one at a time. The yield is used in for loops or with the next() because the `yield` executes the next pieces of data on by one.
example :
```
def cumulative_average(numbers):
     total = 0

     for items, number in enumerate(numbers, 1):
         total += number
         yield total / items

values = [5, 3, 8, 2, 5]  # Simulates a large data set

for cum_average in cumulative_average(values):
 print(f"Cumulative average: {cum_average:.2f}")
```
or :
```
def compte_jusqua_3():
    yield 1
    yield 2
    yield 3

gen = compte_jusqua_3()
print(next(gen))  # Affiche 1
print(next(gen))  # Affiche 2
print(next(gen))  # Affiche 3
```
When the data is finished in the yield it leads to an error when demanding the next() another time so we use the try and except with the `StopIteration` error.
## Creating closures :
This is a function inside a function that remembers the data from the outer function variable even when finished executing and called latter.
example :
```
def make_multiplier(x):
    def multiplier(n):
        return x * n
    return multiplier

times3 = make_multiplier(3)
times5 = make_multiplier(5)

print(times3(10))  # 30
print(times5(10))  # 50
```
here even when `make_multiplier` has finished times3 still remembers the value x=3.
another example :
```
def make_logger(prefix):
    def log(msg):
        print(f"[{prefix}] {msg}")
    return log

info_log = make_logger("INFO")
error_log = make_logger("ERROR")

info_log("System started.")   # [INFO] System started.
error_log("Something went wrong.")  # [ERROR] Something went wrong.
```
in the `info_log` INFO is saved and used latter.
Simple use case :
```
def function(x):
    def function2(y):
        return y**x
    return function2

square = function(2)
print(square(5)) #25 because 5**2 = 25

cube = function(3)
print(cube(5)) #123 because 5**5 = 125
```
# Defining and calling functions : (Advanced features)
## Default argument value :
You can set a default argument to functions, if nothing is specified the default argument will be used.
Simple example :
```
def greet(name="World"):
    print(f"Hello, {name}")

print(greet()) #Hello, World
print(greet("anis")) #Hello, anis
```
here when nothing is specified the Hello, World default argument is used but when anis was specified it was used.
Another example :
```
def login_greeting(defusername = "guest", loged_in = False):
    if loged_in:
        print(f"welcome {defusername} !")
    else:
        print("Hello guest, please try to register after !")

print("do you want to register yes \ no ?")
register = input()
register = register.upper()
  
if register == "YES":
    username = input("choose a username : ")
    login_greeting(username, loged_in = True)
else:
    login_greeting()
```
example :
```
def append_to(item, target = None):
    if target is None:
        target = []
        target.append(item)
    else:
        target.append(item)
    return target

print(append_to(1)) #[1]
print(append_to(2)) #[2]

grocerystore = []
print(append_to('banana', grocerystore)) #['banana']
print(append_to('apple', grocerystore)) #['banana', 'apple']

##############################################################################

def append_to(item, target = []):
    target.append(item)
    return target

print(append_to(1)) #[1]
print(append_to(2)) #[1, 2]

grocerystore = []
print(append_to('banana', grocerystore)) #['banana']
print(append_to('apple', grocerystore)) #['banana', 'apple']
```
here it is visible how the `target = []` and `target = None` run and behave differently.
## Variable Number of Positional Arguments: `*args`
When adding an `*` to the function argument name this syntax pass an arbitrary number of positional arguments to the function in the form of a tuple.
example :
```
def fun2(num):
    print(num)
    return num

def fun(*num):
    print(num)
    return num

fun2(1) #1
#fun2(1, 2, 3, 4, 5, 6, 7, 8) Error

fun(1, 2, 3, 4, 5, 6, 7, 8) #(1, 2, 3, 4, 5, 6, 7, 8) return a tupple
fun('anis', 'asma', 'rafik') #('anis', 'asma', 'rafik')
```
where the `fun2` fail the `fun(*num)` work to deliver and pack everything in a tuple.
Useful example :
```
def average(*args):
    return sum(args) / len(args)

print(average(1, 2, 3, 4, 5, 6)) #(1+2+3+4+5+6)/6 = 3.5
```
### Unpacking an iterable Into Positional Arguments using the `*args` :
When a iterable is proceeded in a function call with an Asterix `*` this performs an unpacking operation that unpack all inside it into independent value that become positional argument. This can be used in list, tuples or sets just be careful about unordered containers.
example :
```
def function(x, y, z):
    print(f"{x = }")
    print(f"{y = }")
    print(f"{z = }")

numbers = [1, 2, 3]
function(*numbers)

# x = 1
# y = 2
# z = 3
```

```
numbers = [1, 2, 3, 4, 5]
letters = ("a", "b", "b", "c")

function(*numbers, *letters)
```
here used multiple times.
## Variable Number of Keyword Arguments: `**kwargs`
Placing a double asterisk (`**`) before a parameter name in a function definition tells Python to pack the provided keyword arguments into a dictionary :
```
def function(**kwargs):
    print(kwargs)
    return kwargs

function(one=1, two=2, three=3) #{'one': 1, 'two': 2, 'three': 3}
```
simple use case :
```
def report(**kwargs):
     print("Report:")
     for key, value in kwargs.items():
         print(f" - {key.capitalize()}: {value}")

report(name="Keyboard", price=19.99, quantity=5, category="PC Components")
```
### Unpacking keyword arguments with `*kwargs` :
When the argument is proceeded with the the dictionary unpacking operator `**` in a function call that specifies that the argument is dictionary should be unpacked to keyword arguments.
example :
```
def function(one, two, three):
    print(f"{one = }")
    print(f"{two = }")
    print(f"{three = }")


numbers = {"one": 1, "two": 2, "three": 3}
function(**numbers)
# one = 1
# two = 2
# three = 3
```

```
def function(**kwargs):
    for key, value in kwargs.items():
        print(key, "=", value)


numbers = {"one": 1, "two": 2, "three": 3}
letters = {"a": "A", "b": "B", "c": "C"}

function(**numbers, **letters)
# one = 1
# two = 2
# three = 3
# a = A
# b = B
# c = C
```
## Positional and Keywords Combined: `*args` and `**kwargs`
`*args` and `**kwargs` can be combined in one Python function definition but i has to be specified in order and it can also be combined with regular positional argument.
example 1 :
```
def function(*args, **kwargs):
    print(args)
    print(kwargs)
    return args, kwargs

function(1, 2, 3, one=1, two=2, three=3)
#(1, 2, 3)
#{'one': 1, 'two': 2, 'three': 3}
```
example 2 :
```
def function(a, b, *args, **kwargs):
    print(a)
    print(b)
    print(args)
    print(kwargs)

function("A", "B", 1, 2, 3, one=1, two=2, three=3)
# A
# B
# (1, 2, 3)
# {'one': 1, 'two': 2, 'three': 3}
```
Note : to combine these types of arguments, they must be defined them in order. The positional arguments first, then `*args`, and finally `**kwargs`.
## Positional-Only Arguments :
In function definition when the bar slash `/` is used what's o the left has always to be positional argument and on the right keyboard argument.
```
def fullname(nom ,prenom , classe_social = False):
    if classe_social is False:
        print(f'{nom} {prenom}')
    else:
        print(f'{classe_social} {nom} {prenom}')

fullname(nom = 'nasri', prenom = 'anis', classe_social='dr') # dr nasri anis

###################################################################################

def fullname(nom ,prenom , /,classe_social = False):
    if classe_social is False:
        print(f'{nom} {prenom}')
    else:
        print(f'{classe_social} {nom} {prenom}')

#fullname(nom = 'nasri', prenom = 'anis', classe_social='dr') Cant write that returns an error

fullname('nasri', 'anis', classe_social='dr') # dr nasri anis
```
Adding the `/` at the end makes sure that all the argument are positional only.
## Keyword-Only Arguments :
Adding an Asterix `*` make sure that the rest of the arguments are keyword only.
```
def fullname(*, nom ,prenom ,classe_social = False):
    if classe_social is False:
        print(f'{nom} {prenom}')
    else:
        print(f'{classe_social} {nom} {prenom}')

fullname(nom = 'nasri', prenom = 'anis', classe_social='dr') # dr nasri anis
#fullname('nasri', 'anis', classe_social='dr') error
```
we can also use `*args` because of the Asterix in the beginning but look :
```
def price(*prices , number_of_items):
    print(sum(prices) + number_of_items)

price(12, 34, 100, number_of_items = 12)
```
the `*` can also be used in the middle of the function definition to make sur that what's after is a keyword argument.

NOTE : you can use both `/` and `*` in the same function definition :
```
def function(x, y, /, z, w, *, a, b):
    print(x, y, z, w, a, b)
```
here x and y are positional only argument, a and b are keyword only argument but z and w can be the two.
# Optional features of functions :
1. Docstrings : Docstrings are strings that you add at the beginning of a function to provide built-in documentation. They explain what a function does, what arguments it expects, and what it returns.
2. Annotations : let you optionally specify the expected types of arguments and return values.
## Docstrings :
Docstring can contain information about the function’s purpose, arguments, raised exceptions, and return values. It can also include basic examples of using the function and any other relevant information.
example :
```
def average(*args):
    """Calculate the average of given numbers.

    Args:
        *args (float or int): One or more numeric values.

    Returns:
        float: The arithmetic mean of the provided values.

    Raises:
        ZeroDivisionError: If no arguments are provided.

    Examples:
        >>> average(10, 20, 30)
        20.0
        >>> average(5, 15)
        10.0
        >>> average(7)
        7.0
    """
    return sum(args) / len(args)
```
here the triple quotation mark is used `"""` .
When a docstring is defined, Python assigns it to a special function attribute called `print(function name.__doc__)` or `help(function name)` that access a function’s docstring.
```
print(average.__doc__)

# Calculate the average of given numbers.

#    Args:
#        *args (float or int): One or more numeric values.
#
#    Returns:
#        float: The arithmetic mean of the provided values.

#    Raises:
#        ZeroDivisionError: If no arguments are provided.

#    Examples:
#        >>> average(10, 20, 30)
#        20.0
#        >>> average(5, 15)
#        10.0
#        >>> average(7)
#        7.0
```
## Annotations :
General syntax :
```
def function(arg_0: <type>, arg_1: <type>, ..., arg_n: <type>) -> <type>:
    <block>
```
To add annotations to a function’s arguments, you use a colon (`:`) followed by the desired metadata after the argument in the function definition. Similarly, to provide annotations for the return value, add the arrow characters (`->`) and the desired metadata between the closing parentheses and the colon that terminates the function header.
The `print(type(argument))` is used to print the argument annotation. example :
```
def function(a: int, b: str) -> float:
    print(type(a), type(b))
    return 1, 2, 3


function("Hello!", 123)
# <class 'str'> <class 'int'>
```
Annotations are metadata attached to the function through a dictionary called `.__annotations__`
```
print(function.__annotations__)
```
To prevent typing error like using a string instead of a int or float you can force the utilization of the necessary data type using the `type` :
```
type Number = int | float

def add(a: Number, b: Number) -> Number:
    return a + b
```
or :
```
def add(a: int | float, b: int | float) -> int | float:
    return a + b

add(3, 4)
```
NOTE : its necessary to have `mypy` and run it in the script `$ mypy your_script.py` to show an error message if the right data type is not used.
# Asynchronous Functions :
 Including the `asyncio` module and the `async`and `await` keywords. Asynchronous code allows to handle multiple tasks concurrently without blocking the execution of the main program.
 ```
 import asyncio
 async def function_name([parameters]):
    <block>
```
to show the result of a function we use :
```
asyncio.run(function name())
```
example :
```
import asyncio

async def fetch_data():
    print("Fetching data from the server...")
    await asyncio.sleep(1)  # Simulate network delay
    print("Data received!")
    return {"user": "john", "status": "active"}


async def main():
    data = await fetch_data()
    print(f"Received data: {data}")


asyncio.run(main())

# Fetching data from the server...
# Data received!
# Received data: {'user': 'john', 'status': 'active'}
```
here when the main is called when arrived to `data = await fetch_data()` it wait for the functions `fetch_data()` to run and when it finishes the main continue.