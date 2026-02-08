- Lists allows to create variable-length and mutable sequences of objects.IT can store objects of any type,  and also mix objects of different types within the same list, although list elements often share the same type.
- List characteristics :
  1. **Ordered**: They contain elements or items that are sequentially arranged according to their specific insertion order.
  2. **Zero-based**: They allow you to access their elements by indices that start from zero.
  3. **Mutable**: They support in-place mutations or changes to their contained elements.
  4. **Heterogeneous**: They can store objects of different types.
  5. **Growable and dynamic**: They can grow or shrink dynamically, which means that they support the addition, insertion, and removal of elements.
  6. **Nestable**: They can contain other lists, so you can have lists of lists.
  7. **Iterable**: They support iteration, so you can traverse them using a loop or comprehension while you perform operations on each of their elements.
  8. **Sliceable**: They support slicing operations, meaning that you can extract a series of elements from them.
  9. **Combinable**: They support concatenation operations, so you can combine two or more lists using the concatenation operators.
  10. **Copyable**: They allow you to make copies of their content using various techniques.
# Constructing lists :
There's several ways to create lists in python : `list literals`, `the list() constructor`, `a list comprehenssion`.

## Creating lists through literals :
This is the simplest way :
```
[item_0, item_1, ..., item_n]
```
like this :
```
digits = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
fruits = ["apple", "banana", "orange", "kiwi", "grape"]
cities = [
     "New York",
     "Los Angeles",
     "Chicago",
     "Houston",
     "Philadelphia"
 ]

matrix = [
     [1, 2, 3],
     [4, 5, 6],
     [7, 8, 9]
 ]

inventory = [
     {"product": "phone", "price": 1000, "quantity": 10},
     {"product": "laptop", "price": 1500, "quantity": 5},
     {"product": "tablet", "price": 500, "quantity": 20}
 ]

functions = [print, len, range, type, enumerate]

empty = []
```
Empty lists are useful in many situations. For example, maybe you want to create a list of objects resulting from computations that run in a loop. The loop will allow you to populate the empty list one element at a time.
## Using the `list()` Constructor :
General syntax :
```
variable = list([iterable])
print(variable)
```
To create a list, you need to call `list()` as you’d call any class constructor or function. Note that the square brackets around `iterable` mean that the argument is optional so the brackets aren’t part of the syntax.
some examples :
```
>>> list((0, 1, 2, 3, 4, 5, 6, 7, 8, 9))
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

>>> list({"circle", "square", "triangle", "rectangle", "pentagon"})
['square', 'rectangle', 'triangle', 'pentagon', 'circle']

>>> list({"name": "John", "age": 30, "city": "New York"}.items())
[('name', 'John'), ('age', 30), ('city', 'New York')]

>>> list("Pythonista")
['P', 'y', 't', 'h', 'o', 'n', 'i', 's', 't', 'a']

>>> list()
[]
```
## Using lists comprehension :
Basic syntax :
```
[expression(item) for item in iterable]
```
This behave like a for loop that iterate and store the values.
example :
```
items = [number for number in range(1, 11)]
print(items)
```
# Accessing Items in a List: Indexing
Each item in a list has an index that specifies its position in the list. Indices are integer numbers that start at `0` and go up to the number of items in the list minus `1`.
To access a list item through its index :
```
list_object[index]
```
The number of items in a list is known as the list’s **length**. You can check the length of a list by using the built-in `len()` function:
```
>>> len(languages)
6
```
So, the index of the last item in `languages` is `6 - 1 = 5`.
indexing can also go backward by using the minus sign `-1` show the last, `-2` the one before the last and so on. `-len()` can also be used to count how much items in the list backward.

When you have a list containing other sequences, you can access the items in any nested sequence by chaining indexing operations. Consider the following list of employee records:
```
employees = [
    ("John", 30, "Software Engineer"),
    ("Alice", 25, "Web Developer"),
    ("Bob", 45, "Data Analyst"),
    ("Mark", 22, "Intern"),
    ("Samantha", 36, "Project Manager")
]

# basic syntax used is list_of_sequences[index_0][index_1]...[index_n]

employees[1][0]
# Alice
employees[1][1]
# 25
employees[1][2]
# Web Developer
```
If the nested items are dictionaries, then you can access their data using keys:
```
employees = [
    {"name": "John", "age": 30, "job": "Software Engineer"},
    {"name": "Alice", "age": 25, "job": "Web Developer"},
    {"name": "Bob", "age": 45, "job": "Data Analyst"},
    {"name": "Mark", "age": 22, "job": "Intern"},
    {"name": "Samantha", "age": 36, "job": "Project Manager"}
]

employees[3]["name"]
# Mark
employees[3]["age"]
# 22
employees[3]["job"]
# Intern
```
# Retrieving Multiple Items From a List: Slicing
Another common requirement when working with lists is to extract a portion, or `slice`, of a given list. You can do this with a `slicing` operation, which has the following syntax:
```
list_object[start:stop:step]
```
example :
```
>>> digits = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

>>> first_three = digits[:3]
>>> first_three
[0, 1, 2]

>>> middle_four = digits[3:7]
>>> middle_four
[3, 4, 5, 6]

>>> last_three = digits[-3:]
>>> last_three
[7, 8, 9]

>>> every_other = digits[::2]
>>> every_other
[0, 2, 4, 6, 8]

>>> every_three = digits[::3]
>>> every_three
[0, 3, 6, 9]
```
the parameters can be played with as needed.
Every slicing operation uses a `slice` object internally. The built-in `slice()` function provides an alternative way to create `slice` objects that you can use to extract multiple items from a list. The signature of this built-in function is the following:
```
slice(start, stop, step)
```
example :
```
>>> letters = ["A", "a", "B", "b", "C", "c", "D", "d"]

>>> upper_letters = letters[slice(0, None, 2)]
>>> upper_letters
['A', 'B', 'C', 'D']

>>> lower_letters = letters[slice(1, None, 2)]
>>> lower_letters
['a', 'b', 'c', 'd']
```
writing none tells to the slicing operators to use the default.
![[Pasted image 20250730164148.png]]
# Creating copies of a list :
Making copies of an original list can be very helpful, so when you change a given list the original one doesn't get affected.
In python there's two way to create copies of a list :
1. A **shallow** copy
2. A **deep** copy
**Aliases** are also a related concept that can cause some confusion and lead to issues and bugs.
## Aliases of list :
An alias of a list is like giving another name to an existing list, changes in an alias will affect the rest of the aliases.
example :
```
countries = ["United States", "Canada", "Poland", "Germany", "Austria"]

nations = countries # here an alias is created
id(countries) == id(nations) # true

countries[0] = "United States of America" # A change in one alias affects all the other aliasses

print(nations)
# ["United States of America", "Canada", "Poland", "Germany", "Austria"]
```
aliases can come in handy in situations where you need to avoid name collisions in your code or when you need to adapt the names to specific naming patterns.
## Shallow copies of a list :
A **shallow copy** of an existing list is a new list containing references to the objects stored in the original list. In other words, when you create a shallow copy of a list, Python constructs a new list with a new identity. Then, it inserts references to the objects in the original list into the new list.
There are at least three different ways to create shallow copies of an existing list. You can use:
1. The slicing operator, `[:]`
2. The `.copy()`method
3. The `copy()` function from the `copy` module
### 1- The slicing operator :
==visit : Retrieving Multiple Items From a List: Slicing== because it has the same behavior.
example :
```
>>> countries = ["United States", "Canada", "Poland", "Germany", "Austria"]

>>> nations = countries[:]
>>> nations
['United States', 'Canada', 'Poland', 'Germany', 'Austria']

>>> id(countries) == id(nations)
False

>>> id(nations[0]) == id(countries[0])
True
>>> id(nations[1]) == id(countries[1])
True

>>> countries[0] = "United States of America"
>>> countries
['United States of America', 'Canada', 'Poland', 'Germany', 'Austria']

>>> nations
['United States', 'Canada', 'Poland', 'Germany', 'Austria']

>>> id(countries[0]) == id(nations[0])
False
>>> id(countries[1]) == id(nations[1])
True
```
This means that you don’t have copies of the items. You’re really sharing them but any modification in one doesn't affect the other. This behavior allows you to save some memory when working with lists and their copies.
```
languages = ["Python", "Java", "JavaScript", "C++", "Go", "Rust"]

language = languages[1:5]
print(language) # ['Java', 'JavaScript', 'C++', 'Go']

language = languages[1:5:2]
print(language) # ['Java', 'C++']
```
### 2- The `.copy()` method :
example :
```
>>> countries = ["United States", "Canada", "Poland", "Germany", "Austria"]

>>> nations = countries.copy()
>>> nations
['United States', 'Canada', 'Poland', 'Germany', 'Austria']

>>> id(countries) == id(nations)
False
>>> id(countries[0]) == id(nations[0])
True
>>> id(countries[1]) == id(nations[1])
True

>>> countries[0] = "United States of America"
>>> countries
['United States of America', 'Canada', 'Poland', 'Germany', 'Austria']
>>> nations
['United States', 'Canada', 'Poland', 'Germany', 'Austria']
```
another way to use the copy method :
```
>>> from copy import copy

>>> countries = ["United States", "Canada", "Poland", "Germany", "Austria"]

>>> nations = copy(countries)
>>> nations
['United States', 'Canada', 'Poland', 'Germany', 'Austria']

>>> id(countries) == id(nations)
False
>>> id(countries[0]) == id(nations[0])
True
>>> id(countries[1]) == id(nations[1])
True

>>> countries[0] = "United States of America"
>>> countries
['United States of America', 'Canada', 'Poland', 'Germany', 'Austria']
>>> nations
['United States', 'Canada', 'Poland', 'Germany', 'Austria']
```
Calling `.copy()` on `countries` gets you a shallow copy of this list. Now you have two different lists. However, their elements are common to both.
## Deep copies of a list :
Sometimes you may need to build a complete copy of an existing list. In other words, you want a copy that creates a new list object and also creates new copies of the contained elements. In these situations, you’ll have to construct what’s known as a **deep copy**.
When you create a deep copy of a list, Python constructs a new list object and then inserts copies of the objects from the original list recursively.
Here the `deepcopy()` function from the copy module is used :
```
>>> from copy import deepcopy

>>> matrix = [[1, 2, 3]]
>>> matrix_copy = deepcopy(matrix)

>>> id(matrix) == id(matrix_copy)
False
>>> id(matrix[0]) == id(matrix_copy[0])
False
>>> id(matrix[1]) == id(matrix_copy[1])
False
```
Note : both the lists and their sibling items have different identities.
here when you have nested lists its better to use the `deepcopy()` and not the `copy()` because when the copy of an object in the inside list is changed and the change affect every other copy.
example :
```
>>> from copy import copy

>>> matrix_copy = copy(matrix)
>>> matrix_copy[0][0] = 100
>>> matrix_copy[0][1] = 200
>>> matrix_copy[0][2] = 300
>>> matrix_copy
[[100, 200, 300]]

>>> matrix
[[100, 200, 300]]
```
its better the write it like that :
```
>>> matrix = [[1, 2, 3]]

>>> matrix_copy = deepcopy(matrix)
>>> matrix_copy[0][0] = 100
>>> matrix_copy[0][1] = 200
>>> matrix_copy[0][2] = 300
>>> matrix_copy
[[100, 200, 300]]

>>> matrix
[[1, 2, 3]]
```
Note : when you have a list containing immutable objects, such as numbers, strings, or tuples, the behavior of `deepcopy()` mimics what `copy()` does.
# Updating Items in Lists: Index Assignments
Lists can be updated without changing of the underlying list.
we use the following syntax :
```
list_object[index] = new_value
```
if the index of the value you want to change is unknown then the `.index()` can be used :
```
fruits = ["apple", "banana", "orange", "kiwi", "grape"]

print(fruits.index('kiwi')) # 3
```

```
>>> fruits = ["apple", "banana", "orange", "kiwi", "grape"]

>>> fruits[fruits.index("kiwi")] = "mango"
>>> fruits
['apple', 'banana', 'orange', 'mango', 'grape']
```
Multiple item in a list can be updated in one go using the slicing operator to access the items and modify them.
the general syntax :
```
list_object[start:stop:step] = iterable
```
If `iterable` has the same number of elements as the target slice, then Python updates the elements one by one without altering the length of `list_object`.
example :
```
>>> numbers = [1, 2, 3, 4, 5, 6, 7]

>>> numbers[1:4] = [22, 33, 44]
>>> numbers
[1, 22, 33, 44, 5, 6, 7]
```
you can add more or shrink it by using more or less value in the iterable.
to add thinks at the end :
```
>>> pets[len(pets):] = ["hawk"]
>>> pets
['cat', 'dog', 'parrot', 'gold fish', 'python', 'hawk']
```
# Growing and Shrinking Lists Dynamically
## Appending a Single Item at Once: `.append()`
This method allows you to append items to a list. The method takes one item at a time and adds it to the right end of the target list.
```
>>> pets = ["cat", "dog"]

>>> pets.append("parrot")
>>> pets
['cat', 'dog', 'parrot']

>>> pets.append("gold fish")
>>> pets
['cat', 'dog', 'parrot', 'gold fish']

>>> pets.append("python")
>>> pets
['cat', 'dog', 'parrot', 'gold fish', 'python']
```
This method allows you to add one item at a time, that item could be any data type including another list.
Using `.append()` is equivalent to doing the following slice assignment:
```
>>> pets[len(pets):] = ["hawk"]
>>> pets
['cat', 'dog', 'parrot', 'gold fish', 'python', 'hawk']
```
## Extending a List With Multiple Items at Once: `.extend()`
The `.extand()` method takes an iterable of object and appends them as individual items to the end of the targeted list.
example :
```
>>> fruits = ["apple", "pear", "peach"]

>>> fruits.extend(["orange", "mango", "banana"])
>>> fruits
['apple', 'pear', 'peach', 'orange', 'mango', 'banana']
```
The `.extend()` method unpacks the items in the input iterable and adds them one by one to the right end of your target list.
The `.extend()` can take any iterable as an argument. So, you can use tuples, strings, dictionaries and their components, iterators, and even sets. However, remember that if you use a set as an argument to `extend()`, then you won’t know the final order of items beforehand.
Again, you must note that `.extend()` is equivalent to the following slice assignment:
```
>>> fruits = ["apple", "pear", "peach"]

>>> fruits[len(fruits):] = ["orange", "mango", "banana"]
>>> fruits
['apple', 'pear', 'peach', 'orange', 'mango', 'banana']
```
## Inserting an Item at a Given Position: `.insert()`
The `.insert()` allows you to decide where you want to put your item and it takes two arguments :
1. **`index`**: the index at which you want to insert the item
2. **`item`**: the item that you need to insert into the list
When you insert an item at a given index, Python moves all the following items one position to the right in order to make space for the new item, which will take the place of the old item at the target index:
```
>>> letters = ["A", "B", "F", "G"]

>>> letters.insert(2, "C")
>>> letters
['A', 'B', 'C', 'F', 'G']

>>> letters.insert(3, "D")
>>> letters
['A', 'B', 'C', 'D', 'F', 'G']

>>> letters.insert(4, "E")
>>> letters
['A', 'B', 'C', 'D', 'E', 'F', 'G']
```
the `.insert()` add a single item in every call.
Here’s the equivalent slicing of an insert operation:
```
list_object[index:index] = [item]
```

```
items = [1, 2, 3, 4, 5]
items[items.index(4):items.index(4)] = [3.1, 3.2]
print(items) # [1, 2, 3, 3.1, 3.2, 4, 5]
```
## Deleting Items From a List
The methods are :
![[Pasted image 20250731151915.png]]
### The `.remove()` method
The `.remove()` method comes in handy when you want to remove an item from a list, but you don’t know the item’s index. If you have several items with the same value, then you can remove all of them by calling `.remove()` as many times as the item occurs.
### The `.pop()` method
The `.pop()` method allows you to remove and return a specific item using its index. If you call the method with no index, then it removes and returns the last item in the underlying list:
```
>>> to_visit = [
...     "https://realpython.com",
...     "https://python.org",
...     "https://stackoverflow.com",
... ]

>>> visited = to_visit.pop()
>>> visited
'https://stackoverflow.com'
>>> to_visit
['https://realpython.com', 'https://python.org']

>>> visited = to_visit.pop(0)
>>> visited
'https://realpython.com'
>>> to_visit
['https://python.org']

>>> visited = to_visit.pop(-1)
>>> visited
'https://python.org'
>>> to_visit
[]
```
### The `.clear()` method
The `.clear()` method clears everything in a given list.
```
>>> cache = [0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]
>>> cache.clear()
>>> cache
[]
```
The following slice assignment produces the same result as the `.clear()` method:
```
>>> cache = [0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]
>>> cache[:] = []
>>> cache
[]
```
### The `del` method
You can combine `del` with an indexing or slicing operation to remove an item or multiple items, respectively:
```
>>> colors = [
...     "red",
...     "orange",
...     "yellow",
...     "green",
...     "blue",
...     "indigo",
...     "violet"
... ]

>>> del colors[1]
>>> colors
['red', 'yellow', 'green', 'blue', 'indigo', 'violet']

>>> del colors[-1]
>>> colors
['red', 'yellow', 'green', 'blue', 'indigo']

>>> del colors[2:4]
>>> colors
['red', 'yellow', 'indigo']

>>> del colors[:]
>>> colors
[]
```
# Considering Performance While Growing Lists[[https://realpython.com/python-list/#considering-performance-while-growing-lists "Permanent link"]]

When you create a list, Python allocates enough space to store the provided items. It also allocates extra space to host future items. When you use the extra space by adding new items to that list with `.append()`, `.extend()`, or `.insert()`, Python automatically creates room for additional new items.

This process is known as **resizing**, and while it ensures that the list can accept new items, it requires extra CPU time and additional memory. Why? Well, to grow an existing list, Python creates a new one with room for your current data and the extra items. Then it moves the current items to the new list and adds the new item or items.

Consider the following code to explore how Python grows a list dynamically:
```
>>> from sys import getsizeof

>>> numbers = []
>>> for value in range(100):
...     print(getsizeof(numbers))
...     numbers.append(value)
...
56
88
88
88
88
120
120
120
120
184
184
...
```

In this code snippet, you first import [[https://docs.python.org/3/library/sys.html#sys.getsizeof]] from the [[https://docs.python.org/3/library/sys.html#module-sys]] module. This function allows you to get the size of an object in bytes. Then you define `numbers` as an empty list.

Inside the `for` loop, you get and [print](https://realpython.com/python-print/) your list object’s size in bytes. The first iteration shows that the size of your empty list is `56` bytes, which is the baseline size of every list in Python.

Next, the `.append()` method adds a new value to your list. Note how the size of `numbers` grows to `88` bytes. That’s the baseline size plus 32 additional bytes (`56 + 4 × 8 = 88`), which represent four 8-byte [pointers](https://realpython.com/pointers-in-python/) or slots for future items. It means that Python went ahead and allocated space for four items when you added the first element.

As the loop goes, the size of `numbers` grows to `120` bytes, which is `88 + 4 × 8 = 120`. This step allocates space for four more items. That’s why you get `120` four times on your screen.

If you follow the loop’s output, then you’ll notice that the next steps add room for eight extra items, then for twelve, then for sixteen, and so on. Every time Python resizes the list, it has to move all the items to the new space, which takes considerable time.

In practice, if you’re working with small lists, then the overall impact of this internal behavior is negligible. However, in performance-critical situations or when your lists are large, you may want to use more efficient data types, such as [`collections.deque`](https://realpython.com/python-deque/), for example.

Check out the [time complexity Wiki page](https://wiki.python.org/moin/TimeComplexity) for a detailed summary of how time-efficient `list` operations are. For example, the `.append()` method has a time complexity of _O(1)_, which means that appending an item to a list takes constant time. However, when Python has to grow the list to make room for the new item, this performance will be a bit poorer.

Being aware of the time complexity of common list operations will significantly improve your ability to choose the right tool for the job, depending on your specific needs.
# Concatenating and Repeating Lists
The python lists supports concatenating and repeating :
1. **Concatenation**, which uses the plus operator (`+`)
2. **Repetition**, which uses the multiplication operator (`*`)
## Concatenating Lists :
This consists of joining two things together using the `+` operator. The concatenating operator always create a new list that joins the lists so the new and old list has both different ids.
```
>>> digits = [0, 1, 2, 3, 4, 5]
>>> id(digits)
4558758720

>>> digits = digits + [6, 7, 8, 9]
>>> id(digits)
4470412224
```
the `+=` operator can also be used but instead of creating a new list it just mut the older one so both old and new list has the same id this operation is more memory and time efficient.
```
>>> digits = [0, 1, 2, 3, 4, 5]
>>> id(digits)
4699578112

>>> digits += [6, 7, 8, 9]
>>> id(digits)
4699578112
```
## Repeating the Content of a List :
**Repetition** consists of cloning the content of a given list a specific number of times. You can achieve this with the repetition operator `*`.
```
>>> ["A", "B", "C"] * 3
['A', 'B', 'C', 'A', 'B', 'C', 'A', 'B', 'C']

>>> 3 * ["A", "B", "C"]
['A', 'B', 'C', 'A', 'B', 'C', 'A', 'B', 'C']
```
 The `*=` operator can also be used :
 ```
 >>> letters = ["A", "B", "C"]
>>> letters *= 3
>>> letters
['A', 'B', 'C', 'A', 'B', 'C', 'A', 'B', 'C']
```
Again, the regular repetition operator returns a new list object containing the repeated data. However, its augmented variation mutates the target list in place, which makes it more efficient.
# Reversing and Sorting Lists
## Reversing a List: `reversed()` and `.reverse()`
### The `reversed()` method :
The built-in `reversed()` function takes a sequence as an argument and returns an iterator that yields the values of that sequence in reverse order:
```
digits = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

print(reversed(digits))
# <list_reverseiterator object at 0x00000263884FB730>

print(list(reversed(digits)))
# [9, 8, 7, 6, 5, 4, 3, 2, 1, 0]
print(digits)
# [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

digits = list(reversed(digits))
print(digits)
# [9, 8, 7, 6, 5, 4, 3, 2, 1, 0]
```
It’s important to note that `reversed()` retrieves items from the input sequence lazily. This means that if something changes in the input sequence during the reversing process, then those changes will reflect in the final result. ``reversed()` doesn’t create a copy of the input iterable. Instead, it works with a reference to it.`
### The `.revers()` method :
The `reversed()` function is great when you want to iterate over a list in reverse order without altering the original list but with the `.revers()` the list is reversed persistently.
example :
```
digits = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

digits.reverse()
print(digits)
# [9, 8, 7, 6, 5, 4, 3, 2, 1, 0]
```
the `.reverse()` mutates the underlying list in place.
### Using the slicing operator :
slicing is another technique that you can use to get a reversed copy of an existing list. To do this, you can use the following slicing operation:
```
>>> digits = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

>>> digits[::-1]
[9, 8, 7, 6, 5, 4, 3, 2, 1, 0]
```
## Sorting a List: `sorted()` and `.sort()`
When you pass a list to `sorted()`, you get a list of sorted values as a result. The function doesn’t alter the original data in your list.
```
digits = [5, 4, 3, 2, 1]
print(sorted(digits)) # [1, 2, 3, 4, 5]
print(digits) # [5, 4, 3, 2, 1]
```
When it comes to sort strings python begin by upper case then lower case letters following the Unicode code point :
```
>>> words = ["Hello,", "World!", "I", "am", "a", "Pythonista!"]

>>> sorted(words)
['Hello,', 'I', 'Pythonista!', 'World!', 'a', 'am']
```
the built-in `ord()` function to get the Unicode code point of a character in Python.
If needed you can sort by descending order use the following matrix :
```
sorted(numbers, reverse=True)
```
- The `sorted()` accepts only one argument the `key`. This argument allows you to specify a one-argument function that will extract a comparison key from each list item.
```
sorted(the_list_to_sort, key = lambda the_list_to_sort : the_list_to sort[index_of what_you_want_to_sort])
```
example :
```
>>> employees = [
...     ("John", 30, "Designer", 75000),
...     ("Jane", 28, "Engineer", 60000),
...     ("Bob", 35, "Analyst", 50000),
...     ("Mary", 25, "Service", 40000),
...     ("Tom", 40, "Director", 90000)
... ]

>>> sorted(employees, key=lambda employee: employee[1])
[
    ('Mary', 25, 'Service', 40000),
    ('Jane', 28, 'Engineer', 60000),
    ('John', 30, 'Designer', 75000),
    ('Bob', 35, 'Analyst', 50000),
    ('Tom', 40, 'Director', 90000)
]
```
here it sorts in function of the age.
If you need to sort a list in place instead of getting a new list of sorted data, then you can use the `.sort()` method and has the same characteristics as the `.revers()`.
# Traversing Lists
To traverse a list, you’ll need a loop that goes over each element from the start to the end of the list. Python provides several constructs that allow you to do this. The most popular are `for` loops and `list comprehensions`. You can also use some of Python’s `functional programming` tools for traversing lists.
## Using `for loops` :
Basic syntax :
```
colors = [
    "red",
    "orange",
    "yellow",
    "green",
    "blue",
    "indigo",
    "violet"
]

for color in colors:
    print(color)
red
orange
yellow
green
blue
indigo
violet
```
Other way :
```
for i in range(len(colors)):
    print(colors[i])
red
orange
yellow
green
blue
indigo
violet
```
the built in `enumerate()` :
```
for i, color in enumerate(colors):
    print(f"{i} is the index of '{color}'")

0 is the index of 'red'
1 is the index of 'orange'
2 is the index of 'yellow'
3 is the index of 'green'
4 is the index of 'blue'
5 is the index of 'indigo'
6 is the index of 'violet'
```
the `zip()` function :
```
integers = [1, 2, 3]
letters = ["a", "b", "c"]
floats = [4.0, 5.0, 6.0]

for i, l, f in zip(integers, letters, floats):
    print(i, l, f)

1 a 4.0
2 b 5.0
3 c 6.0
```
the `zip()` function allows to iterate over multiple lists in parallel.
### Performing modifications on lists using `for loops` :
#### Removing values :
It is also possible to perform modification on a list using the `for loop` this practice can lead to errors so be carful. As a rule of thumb, if you need to modify the content of a list in a loop, then take a copy of that list first.
```
>>> numbers = [2, 9, 5, 1, 6]

>>> for number in numbers:
...     if number % 2:
...         numbers.remove(number)
...
>>> numbers
[2, 5, 6]
```
Unfortunately, only `9` and `1` were removed, while `5` remained in your list. This unexpected and incorrect behavior happened because removing items from a list shifts their indices, which interferes with the indices inside a running `for` loop. You can avoid this problem in a few ways.
```
>>> numbers = [2, 9, 5, 1, 6]

>>> for number in numbers[:]:
...     if number % 2:
...         numbers.remove(number)
...
>>> numbers
[2, 6]
```
This time, the result is correct. You use the `[:]` operator to create a shallow copy of your list. This copy allows you to iterate over the original data in a safe way. Once you have the copy, then you feed it into the `for` loop, as before.
```
>>> numbers = [2, 9, 5, 1, 6]

>>> for number in reversed(numbers):
...     if number % 2:
...         numbers.remove(number)
...
>>> numbers
[2, 6]
```
When you remove only the last item from the right end of a list on each iteration, you change the list length, but the indexing remains unaffected. This lets you correctly map indices to the corresponding list elements.
NOTE : when you make this practice always `reverse` or use the `[:]` .
#### Modifying elements :
While modifying list elements during iteration is less of a problem than deleting them, it also isn’t considered a good practice. 
it is always better to create a new list and populate it with the transformed value.
## Building new lists with comprehensions
That allows you to create lists with transformed data out of another list or iterable.
That has the same logic as `for loop` but write more simply :
```
numbers = ["2", "9", "5", "1", "6"]

numbers = [int(number) for number in numbers]
print(numbers) # [2, 9, 5, 1, 6]
```
this is equivalent of a `for loop` with the `enumerate()` function.
```
>>> integers = [20, 31, 52, 6, 17, 8, 42, 55]

>>> even_numbers = [number for number in integers if number % 2 == 0]
>>> even_numbers
[20, 52, 6, 8, 42]
```
## Processing lists with functional tools
You can also take advantage of some Python functional programming tools, such as `map()` and `filter()`, to traverse a list of values. These functions have an internal loop that iterates over the items of an input iterable and returns a given result.
### `map()`
 the `map()` function takes a **transformation function** and an iterable as arguments. Then it returns an iterator that yields items that result from applying the function to every item in the iterable.
 ```
 >>> numbers = ["2", "9", "5", "1", "6"]

>>> numbers = list(map(int, numbers))
>>> numbers
[2, 9, 5, 1, 6]
```
In this example, `map()` applies `int()` to every item in `numbers` in a loop. Because `map()` returns an iterator, you’ve used the `list()` constructor to consume the iterator and show the result as a list.
### `filter()`
the built-in `filter()` function takes two arguments: a predicate function and an iterable of data. Then it returns an iterator that yields items that meet a given condition, which the predicate function tests for.
```
>>> integers = [20, 31, 52, 6, 17, 8, 42, 55]

>>> even_numbers = list(filter(lambda number: number % 2 == 0, integers))
>>> even_numbers
[20, 52, 6, 8, 42]
```
# Exploring other features of lists
## Finding items in a list
Python has a few tools that allow you to search for values in an existing list. 
- if you only need to quickly determine whether a value is present in a list, but you don’t need to grab the value, then you can use the `in` or `not in` operator, which will run a **membership** test on your list and that returns a Boolean value.
basic syntax :
```
print(item in list_object)
print(item not in list_object)
```
- The `.index()` method is another tool that you can use to find a given value in an existing list. If the value is in the list, then the method returns its index. Otherwise, it raises a `ValueError` exception.
basic syntax :
```
print(list_name.index(value))
```
note that if the value is repeated then it will return the index of the first occurrence.
- Lists provide yet another method that you can use for searching purposes. The method is called `.count()`, and it allows you to check how many times a given value is present in a list.
basic syntax :
```
print(list_name.count(value))
```

NOTE : Searching for a specific value in a Python list isn’t a cheap operation. The time complexity of `.index()`, `.count()`, and membership tests on lists is _O(n)_. Such linear complexity may be okay if you don’t need to perform many lookups. However, it can negatively impact performance if you need to run many of these operations.
## Getting the Length, Maximum, and Minimum of a List
- To determine the length of a list, you’ll use the built-in `len()` function.
NOTE : It’s important to note that because lists keep track of their length, calling `len()` is pretty fast, with a time complexity of _O(1)_. So, in most cases, you don’t need to store the return value of `len()` in an intermediate variable.
- To calculate the sum of numbers in a list the `sum()` function
- Another frequent task that you’ll perform on lists, especially on lists of numeric values, is to find the minimum and maximum values. To do this, you can take advantage of the built-in `min()` and `max()` functions.
## Comparing Lists
List objects support the standard comparison operators
```
>>> [2, 3] == [2, 3]
True
>>> [5, 6] != [5, 6]
False

>>> [5, 6, 7] < [7, 5, 6]
True
>>> [5, 6, 7] > [7, 5, 6]
False

>>> [4, 3, 2] <= [4, 3, 2]
True
>>> [4, 3, 2] >= [4, 3, 2]
True
```
Python compares lists in an item-by-item manner using lexicographical comparison. The first difference determines the result.
# Subclassing the Built-In `list` Class
# Putting Lists Into Action
## Removing Repeated Items From a List
using the `set` object creates a new list of unique value but without necessarily keeping the order.
```
>>> list(set([2, 4, 5, 2, 3, 5]))
[2, 3, 4, 5]
```
Another technique much safer to use is :
```
>>> def get_unique_items(list_object):
...     result = []
...     for item in list_object:
...         if item not in result:
...             result.append(item)
...     return result
...

>>> get_unique_items([2, 4, 5, 2, 3, 5])
[2, 4, 5, 3]
```
In this function, you accept a list as an argument. Then you define a new empty list to store the function’s result. In the loop, you iterate over the items in the input list. The conditional checks if the current item is absent in `result`. If that’s the case, then you add the item using `.append()`. Once the loop has finished, you return the resulting list, which will contain unique values.
The only problem with that method is that the `not in` operator can be too slow on larger lists do to it linear time complexity, to fix this then an additional helper variable need to be introduced  to hold copies of the unique values in a python set :
```
>>> def get_unique_items(list_object):
...     result = []
...     unique_items = set()
...     for item in list_object:
...         if item not in unique_items:
...             result.append(item)
...             unique_items.add(item)
...     return result
...

>>> len(get_unique_items(range(100_000)))
100000
```
ou use the set to quickly determine if the given value is already present. Sets implement the `in` and `not in` operators differently, making them much faster than their list counterparts. While this functions returns instantaneously, it requires twice as much memory because you’re now storing every value in two places.
## Creating multidimensional lists :
A multidimensional list is a list that contains other lists as its element.
one way to do that is by using a `for loop` :
```
>>> matrix = []
>>> for row in range(5):
...     matrix.append([])
...     for _ in range(5):
...         matrix[row].append(0)
...

>>> matrix
[
    [0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0]
]
```
In this example, you first create an empty list to store your matrix. Then you start a `for` loop that will run five times. In each iteration, you add a new empty list. So, your matrix will have five rows. Next, you start a nested loop that runs five times too.
the other way using comprehension :
```
>>> [[0 for _ in range(5)] for _ in range(5)]
[
    [0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0]
]
```
In this example, you use a list comprehension whose expression is another list comprehension. The inner comprehension provides the nested lists, while the outer comprehension builds the matrix.
This new version of your list comprehension is way more readable than the previous one. It takes advantage of the repetition operator to build the rows of your matrix. This example might it seem like the following would work:
```
>>> [[0] * 5] * 5
[
    [0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0]
]
```
This output looks like what you need. It’s a list containing five nested lists. However, this resulting matrix internally works pretty differently from all the previous solutions. If you change one value in a given row, then the change will reflect in all the other rows. When you pass a list as an argument to the repetition operator, you get aliases of the list instead of copies. So, all the rows in your matrix are actually the same list.
## Flattening Multidimensional Lists
Processing the data from a nested list can be a problem but flattening this data into a one dimensional list may be a common requirement. By flattening a list, you convert a multidimensional list, such as a matrix, into a one-dimensional list.
example :
```
>>> matrix = [[0, 1, 2]]

>>> flattened_list = []
>>> for row in matrix:
...     flattened_list.extend(row)
...

>>> flattened_list
[0, 1, 2, 10, 11, 12, 20, 21, 22]
```
## Splitting Lists Into Chunks
Another useful list-related skill is to split an existing list into a certain number of chunks. This skill comes in handy when you need to distribute the workload across multiple threads or processes for concurrent processing.
Multiple solutions exists one of the way to do that :
```
>>> def split_list(list_object, chunk_size):
...     chunks = []
...     for start in range(0, len(list_object), chunk_size):
...         stop = start + chunk_size
...         chunks.append(list_object[start:stop])
...     return chunks
...

>>> split_list([1, 2, 3, 4, 5, 6, 7, 8, 9], 3)
[[1, 2, 3]]
```
this piece of code firstly take a list object with a chunk size, after we create an empty list and a for loop that with the range function assign 3 different value to start the first one is 0 then 3 and after 6 (9 is not assigned because the range function stops at 9) after that we do a quick calculation to find where the .append needs to stop and add the list to chunks empty list.
## Using a List as a Stack or Queue
You can use a Python list to emulate a stack or queue data structure using the help of `.append()` and `.pop()`
- LIFO (last in last out) : The stack will hold actions that you can undo. You start by creating an empty list called `stack`. Then you push hypothetical actions onto the stack using `.append()`, which adds the actions to the right end of the list. The `.pop()` method returns the actions so that you can redo them. This method also removes the actions from the right end of the list following the LIFO order that distinguishes a stack data structure.
- FIFO (first in first out) : you can use `.append()` to place items at the end of the list, which is known as an **enqueue** operation. Similarly, you can use `.pop()` with `0` as an argument to return and remove items from the left end of the queue, which is known as a **dequeue**.
By using a Python list, you can quickly take advantage of the standard list functionality to provide basic stack and queue operations, such as push, pop, enqueue, and dequeue. However, keep in mind that even though lists can help you simulate stacks and queues, they aren’t optimized for these use cases. Using a list as a queue is especially bad because it can make the queue terribly slow.
# Deciding Whether to Use Lists
In general, you should use lists when you need to:

- **Keep your data ordered**: Lists maintain the order of insertion of their items.
- **Store a sequence of values**: Lists are a great choice when you need to store a sequence of related values.
- **Mutate your data**: Lists are mutable data types that support multiple mutations.
- **Access random values by index**: Lists allow quick and easy access to elements based on their index.

In contrast, avoid using lists when you need to:

- **Store immutable data**: In this case, you should use a tuple. They’re immutable and more memory efficient.
- **Represent database records:** In this case, consider using a tuple or a [data class](https://realpython.com/python-data-classes/).
- **Store unique and unordered values**: In this scenario, consider using a set or dictionary. Sets don’t allow duplicated values, and dictionaries can’t hold duplicated keys.
- **Run many membership tests where item doesn’t matter**: In this case, consider using a `set`. Sets are optimized for this type of operation.
- **Run advanced array and matrix operations**: In these situations, consider using [NumPy’s](https://realpython.com/numpy-array-programming/) specialized data structures.
- **Manipulate your data as a stack or queue**: In those cases, consider using [`deque`](https://realpython.com/python-deque/) from the [`collections`](https://realpython.com/python-collections-module/) module or [[https://realpython.com/queue-in-python/#asyncioqueue]], [[https://realpython.com/queue-in-python/#asynciolifoqueue]], or [[https://realpython.com/queue-in-python/#asynciopriorityqueue]]. These data types are thread-safe and optimized for fast inserting and removing on both ends.