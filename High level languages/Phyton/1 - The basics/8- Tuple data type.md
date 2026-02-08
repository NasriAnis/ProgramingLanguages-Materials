`Tuples` data type are immutable and can store a fixed number of items everything is kept ordered. they are commonly called containers or collections.
Some of the most relevant characteristics of `tuple` objects include the following:

- **Ordered**: They contain elements that are sequentially arranged according to their specific insertion order.
- **Lightweight**: They consume relatively small amounts of memory compared to other sequences like lists.
- **Indexable through a zero-based index**: They allow you to access their elements by integer indices that start from zero.
- **Immutable**: They don’t support in-place mutations or changes to their contained elements. They don’t support growing or shrinking operations.
- **Heterogeneous**: They can store objects of different data types and domains, including mutable objects.
- **Nestable**: They can contain other tuples, so you can have tuples of tuples.
- **Iterable**: They support iteration, so you can traverse them using a loop or comprehension while you perform operations with each of their elements.
- **Sliceable**: They support slicing operations, meaning that you can extract a series of elements from a tuple.
- **Combinable**: They support concatenation operations, so you can combine two or more tuples using the concatenation operators, which creates a new tuple.
- **Hashable**: They can work as keys in [dictionaries](https://realpython.com/python-dicts/) when all the tuple items are immutable.
# Constructing `tuples` in python
A tuple is a sequence of comma-separated objects. To store objects in a tuple, you need to create the tuple object with all its content at one time.
some of the way to create `tuples` :
- Tuple [literals](https://en.wikipedia.org/wiki/Literal_\(computer_programming\))
- The [[https://docs.python.org/3/library/stdtypes.html#tuple]] constructor
## Creating `tuples` through literals
This method is straightforward its consist of a series of objects separated by comas inside parenthesis. The parenthesis are optional in metaobject tuples and single objects (but in this case the single object has to be followed by a coma) but in empty tuples its necessary. note that single object are not tuples unless you add a come at the end.
example :
```
x = (1)
print(type(x))  # <class 'int'> ❌ Not a tuple!

x = (1,) or x = 1,
print(type(x))  # <class 'tuple'> ✅ It's a tuple!

empty = ()
print(type(empty)) # <class 'tuple'>
```
note that empty tuples cant be populated with new data as we can do for list.
## Using the tuple constructor
the general syntax :
```
tuple([iterable])
```
from that we can create tuples from different iterable.
examples :
```
>>> tuple(["Jane Doe", 25, 1.75, "Canada"])
('Jane Doe', 25, 1.75, 'Canada')

>>> tuple("Pythonista")
('P', 'y', 't', 'h', 'o', 'n', 'i', 's', 't', 'a')

>>> tuple({
...     "manufacturer": "Boeing",
...     "model": "747",
...     "passengers": 416,
... }.values())
('Boeing', '747', 416)

>>> tuple()
()
```
Calling a tuple without an argument returns an empty tuple and note that the square brackets around `iterable` mean that the argument is optional.
# Accessing items in a tuple : indexing
To access an item through its index, you can use the following syntax:
```
tuple_object[index]
```
In any Python tuple, the index of the first item is `0`, the index of the second item is `1`, and so on. The index of the last item is the number of items minus `1`. The length of a tuple can be accessed with the `len()` function. 
NOTE : INDEXING WORK THE SAME IN TUPLES AS LIST OR ANY OTHER ITERABLE.
# Retrieving multiple items from a tuple : Slicing
syntax:
```
tuple_object[start:stop:step]
```
NOTE : SLICING WORK THE SAME IN TUPLES AS LIST OR ANY OTHER ITERABLE.
# Exploring tuple immutability
Tuples are immutable which mean that once created it is not possible to update it. Therefore when storing mutable data in a tuple as dictionaries or lists you can only update inside of the mutable data type.
```
>>> student_info = ("Linda", 18, ["Math", "Physics", "History"])
>>> student_info[2][2] = "Computer science"
>>> student_info
('Linda', 22, ['Math', 'Physics', 'Computer science'])
```
As you can conclude from this example, you can change the content of mutable objects even if they’re nested in a tuple. This behavior of tuples may have further implications. For example, because tuples are immutable, you can use them as keys in a dictionary.
# Packing and unpacking tuples
In python you can pack and unpack variable to values and vise versa. For example, when you write an assignment statement like `point = x, y, z`, you’re _packing_ the values of `x`, `y`, and `z` in `point`. That’s how you create new tuple objects.
You can also do the inverse operation and _unpack_ the values of a tuple into an appropriate number of variables.
```
>>> point = (7, 14, 21)

>>> x, y, z = point
>>> x
7
>>> y
14
>>> z
21
```
Python also has a packing and unpacking operator (`*`) that you can use to make your unpacking statements more flexible. For example, you can use this operator to collect multiple values in a single variable when the number of variables on the left doesn’t match the number of items in the tuple on the right:
```
>>> numbers = (1, 2, 3, 4, 5)

>>> *head, last = numbers
>>> head
[1, 2, 3, 4]
>>> last
5

>>> first, *middle, last = numbers
>>> first
1
>>> middle
[2, 3, 4]
>>> last
5

>>> first, second, *tail = numbers
>>> first
1
>>> second
2
>>> tail
[3, 4, 5]

>>> first, *_ = numbers
>>> first
1
```
Note that the `*` operator collects the values in a new `list` object rather than in a tuple.
Another interesting use case of the packing and unpacking operator is when you need to merge a few tuples together to build a new one:
```
>>> name = ("John", "Doe")
>>> contact = ("john@example.com", "55-555-5555")

>>> (*name, *contact)
John Doe john@example.com 55-555-5555
>>> (name, contact)
('John', 'Doe') ('john@example.com', '55-555-5555')
```
# Returning Tuples From Functions
In some situations, you’ll need to return multiple values from a function or method. To do that, you can build a `return` statement with a comma-separated series of arguments. Yes, that’s a tuple. As a result, whenever you call the function, you’ll get a tuple of values.
# Creating copies of Tuple
Because tuples are immutable data types, there’s no way to mutate their items in place. So, creating copies of an existing tuple isn’t really necessary. The usual shallow copying techniques that you use with lists, such as the slicing operator or the `copy.copy()` function, create aliases instead of copies (changing the aliases or the original copy doesn't change the other).
```
>>> student_info = ("Linda", 18, ["Math", "Physics", "History"])

>>> student_profile = student_info[:]
>>> id(student_info) == id(student_profile)
True
>>> id(student_info[0]) == id(student_profile[0])
True
>>> id(student_info[1]) == id(student_profile[1])
True
>>> id(student_info[2]) == id(student_profile[2])
True
```

```
>>> from copy import copy

>>> student_info = ("Linda", 18, ["Math", "Physics", "History"])

>>> student_profile = copy(student_info)
>>> id(student_info) == id(student_profile)
True
>>> id(student_info[0]) == id(student_profile[0])
True
>>> id(student_info[1]) == id(student_profile[1])
True
>>> id(student_info[2]) == id(student_profile[2])
True
```
in this example when something change in the list inside the tuple it also change the original data we need here to use the deep copy.
# Concatenating and repeating tuples
Like lists and strings, tuples also support concatenation and repetition. You can use the plus operator (`+`) to concatenate tuples together and the star operator (`*`) to repeat the content of an existing tuple.
## Concatenating Tuples Together
**Concatenation** consists of joining two things together. To concatenate two tuples in Python, you can use the plus operator (`+`). In this context, this operator is known as the **concatenation operator**.
The concatenation operator has an augmented variation, which uses the `+=` operator. Here’s how this operator works:
```
>>> profile = ("John", 35)
>>> id(profile)
4420700928

>>> profile += ("Computer science", ("Python", "Django", "Flask"))
>>> id(profile)
4406635200

>>> profile
('John', 35, 'Computer science', ('Python', 'Django', 'Flask'))
```
The **augmented concatenation operator** works on an existing tuple, like `profile` in this example. It takes a second tuple and creates a new one containing all the items from the two original tuples. The augmented concatenation operator is a shortcut to an assignment like `x = x + y`, where `x` and `y` are tuples.
## Repeating the Content of a Tuple
**Repetition** is all about cloning the content of a given container a specific number of times. Tuples support this feature with the repetition operator (`*`), which takes two operands:

1. The tuple whose content you want to repeat
2. The number of times that you need to repeat the content
```
>>> numbers = (1, 2, 3)

>>> numbers * 3
(1, 2, 3, 1, 2, 3, 1, 2, 3)

>>> 4 * numbers
(1, 2, 3, 1, 2, 3, 1, 2, 3, 1, 2, 3)
```
Here, you first repeat the content of `numbers` three times and get a new tuple as a result. Then you repeat the content of `numbers` four times. Note that the order of the operands doesn’t affect the repetition result.
The repetition operator also has an augmented variation that you’ll call the augmented repetition operator. This variation is represented by the `*=` operator. Here’s how it works:
```
>>> numbers = (1, 2, 3)
>>> id(numbers)
4407400448

>>> numbers *= 3
>>> numbers
(1, 2, 3, 1, 2, 3, 1, 2, 3)
>>> id(numbers)
4407458624
```
# Reversing and Sorting Tuples
same as lists.
# Traversing tuples
Using for loop and the comprehension operator same as lists.
# Exploring Other Features of Tuples
With `.count()`, you can count the number of occurrences of a given item in a tuple. The method allows you to check how many times a given item is present in the target tuple.
On the other hand, the `.index()` method allows you to locate the first occurrence of an item in an existing tuple. If the target item is in the tuple, then the method returns its index.
As its name suggests, a membership test allows you to determine whether an object is a **member** of a **collection** of values. The general syntax for membership tests on a tuple looks something like this:
```
item in tuple_object

item not in tuple_object
```
etc.... (same as lists)
