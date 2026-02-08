site : https://www.geeksforgeeks.org/python/python-classes-and-objects/
A class is a user defined template for creating objects, when a class is created a new type of object is defined and then create multiple instances of this object type.

A class is created using the class keyword.  Attributes are variables defined inside the class and represent its property. Attributes can be accessed using .operator (e.g myclass.my_attribute)
### Object
An object is a specific instance of a class. It holds its own set of data (instance variables) and can invoke methods defined by its class. Multiple object can be created from the same class each with its own unique attributes.

```
class Dog:
    sound = "bark"

dog1 = Dog() # Creating object from class
print(dog1.sound) # Accessing the class
```

Here sound attribute is shared across all the instances of dog class.
# `__init__()` Function
`__init__()` function inside classes automatically initializes object attributes when an object is created this init method is the constructor in python.

```
class Dog:
    species = "Canine"  # Class attribute

    def __init__(self, name, age):
        self.name = name  # Instanceattribute
        self.age = age  # Instance attribute
```
### Object initiation using `__init__()`

```
class Dog:
    species = "Canine"  # Class attribute

    def __init__(self, name, age):
        self.name = name  # Instance attribute
        self.age = age  # Instance attribute

# Creating an object of the Dog class
dog1 = Dog("Buddy", 3)

print(dog1.name)  
print(dog1.species)
```
## The `self` parameter
self parameter is a reference to the current instance of class. It allows us to access the attributes and methods of the object.

```
class Dog:
    def __init__(self, name, age):  
        self.name = name 
        self.age = age

    def bark(self): 
        print(f"{self.name} is barking!")

# Creating an instance of Dog
dog1 = Dog("Buddy", 3)
dog1.bark()
```

Explanation:
- Inside bark(), self.name accesses specific dog's name and prints it.
- When we call dog1.bark(), Python automatically passes dog1 as self, allowing access to its attributes.
# `__str__()` method
__str__ method in Python allows us to define a custom string representation of an object. By default, when we print an object or convert it to a string using str(), Python uses the default implementation, which returns a string like <__main__.ClassName object at 0x00000123>.

```
class Dog:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def __str__(self):
        return f"{self.name} is {self.age} years old."
dog1 = Dog("Buddy", 3)
dog2 = Dog("Charlie", 5)

print(dog1)  
print(dog2)
```

Explanation:
- __str__ Implementation: Defined as a method in Dog class. Uses self parameter to access instance's attributes (name and age).
- Readable Output: When print(dog1) is called, Python automatically uses __str__ method to get a string representation of object. Without __str__, calling print(dog1) would produce something like <__main__.Dog object at 0x00000123>.
# Class and instance variable
### Class variables
These are variables that are shared across all instances of a class. It is defined at class level, outside any methods. All objects of class share same value for a class variable unless explicitly overridden in an object.
### Instance variable
Variables that are unique to each instance (object) of a class. These are defined within ****__init__()**** method or other instance methods. Each object maintains its own copy of instance variables, independent of other objects.

Example:

This code shows how class variables are shared across all objects, while instance variables are unique to each object.

```
class Dog:
    # Class variable
    species = "Canine"

    def __init__(self, name, age):
        # Instance variables
        self.name = name
        self.age = age

# Create objects
dog1 = Dog("Buddy", 3)
dog2 = Dog("Charlie", 5)

# Access class and instance variables
print(dog1.species)  # (Class variable)
print(dog1.name)     # (Instance variable)
print(dog2.name)     # (Instance variable)

# Modify instance variables
dog1.name = "Max"
print(dog1.name)     # (Updated instance variable)

# Modify class variable
Dog.species = "Feline"
print(dog1.species)  # (Updated class variable)
print(dog2.species)
```
### Explanation:

- Class Variable (species): Shared by all instances of class. Changing Dog.species affects all objects, as it's a property of class itself.
- Instance Variables (name, age): Defined in __init__() method. Unique to each instance (e.g., dog1.name and dog2.name are different).
- Accessing Variables: Class variables can be accessed via class name (Dog.species) or an object (dog1.species). Instance variables are accessed via object (dog1.name).
- Updating Variables: Changing Dog.species affects all instances. Changing dog1.name only affects dog1 and does not impact dog2.
# Additional important concepts in python classes and objects
### 1. Getter and Setter methods
Getter and Setter methods provide controlled access to an object attribute, the Getter is a method to retrieve an attribute safely and the Setter to update an attribute with validation/control.

example:

This works, but there’s **no control**. Anyone can assign anything (even invalid values).

```
class Person:
    def __init__(self, name):
        self.name = name  # public attribute

p = Person("Anis")
print(p.name)   # Access directly
p.name = "Chef" # Modify directly
print(p.name)

```

Using @property decorator:
```
class Person:
    def __init__(self, name):
        self._name = name # the underscore means "internal use"

    @property
    def name(self):  # getter
        return self._name

    @name.setter
    def name(self, value):  # setter
        if isinstance(value, str) and value.strip():
            self._name = value
        else:
            print("Invalid name!")

p = Person("Anis")
print(p.name)   # looks like direct access, but uses getter
p.name = "Chef" # looks like direct assignment, but uses setter
print(p.name)
p.name = ""     # Invalid

```

The utilization of the _ in attributes:
In Python, the underscore is a **convention**, its shows that this has to be accessed via methods/properties (not enforced by the language)

- `self.name` → **public** attribute: meant to be accessed directly.

- `self._name` → **"protected"** attribute: signals _"this is for internal use, don’t touch it directly"_.

- `self.__name` → **name-mangled (private)**: Python changes its name internally (`_ClassName__name`) to make accidental access harder.
### 2. Method Overriding
This method happens when a child class (subclass) defines a method with the same name as method in its parent class (superclass), when this method is called on a object of the child class python uses the child version not the parents.

example:

The `Dog` class **overrides** the `speak()` method from `Animal`:
```
class Animal:
    def speak(self):
        print("Animal makes a sound")

class Dog(Animal):
    def speak(self):  # overriding parent method
        print("Dog barks")

a = Animal()
a.speak()  # Animal makes a sound

d = Dog()
d.speak()  # Dog barks (child method overrides parent method)

```

Sometimes you want to extend the parent’s functionality, not replace it entirely.
```
class Animal:
    def speak(self):
        print("Animal makes a sound")

class Cat(Animal):
    def speak(self):
        super().speak()   # call parent method
        print("Cat meows")

c = Cat() # Animal makes a sound
c.speak() # Cat meows

```

Imagine a **base class** for payments and a **subclass** for credit card payments:
```
class Payment:
    def process(self, amount):
        print(f"Processing payment of {amount}$")

class CreditCardPayment(Payment):
    def process(self, amount):
        print("Verifying credit card...")
        super().process(amount)  # call parent logic
        print("Credit card payment approved.")

p = CreditCardPayment()
p.process(100)

# Verifying credit card...
# Processing payment of 100$
# Credit card payment approved.
```

- Use `super()` to reuse/extend parent functionality.
- Python always uses the **child’s method** if it exists.
### 3. Static Methods and Class methods
