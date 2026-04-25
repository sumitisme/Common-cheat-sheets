# <span style="color:green">Python Cheat sheet</span>
---

<p>
<span style="color:pink">A lot of these commands are being run on the shell, not the .py program</span>
</p>

# RANDOM BASICS (SHELL PART AND NORMAL ASSIGNMENTS)
---

## Starting the interactive shell

```shell
python
```
---

## Quitting the interactive shell

```shell
exit()
```
---

## Running a script

```shell
python main.py
```
---

## Running a script in interactive mode

```shell
python -i main.py
```
---

## Basic assignments

```py
name    = "Hello"   # String
age     = 7         # Integer
height  = 5.6       # Float 
is_cat  = True      # Boolean 
flaws   = None      # None type
```
---

## Parallel and Chained assignments

```py
x, y = 10, 20   # x = 10, y = 20
a = b = c = 0   # all values 0
```
---

## Augmented Assignments

```py
counter += 1            # increments the value of counter and assigns it to counter 
numbers += [4, 5]       # Extends the existing list "numbers" by appending [4, 5] to it
permissions |= write    # bitwise "or" i.e. "|" operation is done between permissions and write and result is put in permissions
```
---

# STRINGS

---

## Creating Strings

```py
single_line     = 'Hello'
single_line2    = "Hello"
multiline       = """This
                        is
                        a
                        multi-line
                        text""" 
```
---

## Some operations in Strings

```py
Concatenation   = "Hello" + "world"     # Helloworld
Repeatation     = "Hello" * 3           # HelloHelloHello
length          = len("Hello")          # 5



"a".upper()                             # 'A'
"A".lower()                             # 'a'
" a ".strip()                           # 'a'
"abc".replace("bc", "ha")               # 'aha'
"a b".split()                           # ["a", "b"]
"-".join(["a", "b"])                    # 'a-b'
```
---

## String Indexing and Slicing

```py
text = "Python"
text[0]         # 'P'
text[-1]        # 'n'
text[1:4]       # 'yth'
text[:3]        # 'Pyt'
text[3:]        # 'hon'
text[::2]       # 'Pto' Here incrementation is happening i+=2
text[::-1]      # 'nohtyP' Here Decrement to the original length happens
```
---

## String Formatting

```py
name = "Jesus"
age = 2
f"Hello, {name}!"               # "Hello, Jesus!"
f"{name} is {age} years old"    # "Jesus is 2 years old"
f"Debug: {age=}"                # "Debug: age=2"

# Working with templates
template = "Hello, {name} is {age} years old"
template.format(name = "Jesus", age = 2)
```
---

## Raw strings

```py
"This is a normal python\ttext"     # This is a normal python   text
r"This is a raw python\ttext"       # This is a raw python\ttext
```
---

# MATHEMATICAL oPERATIONS

---

## Arithmetics

```py
10 + 3      # 13
10 - 3      # 7
10 * 3      # 30
10 / 3      # 3.3333333333333335
10 // 3     # 3
10 % 3      # 1
2 ** 3      # 8
```
---

## Extra functions to use

```py
abs(-5)             # 5
round(3.7)          # 4
round(3.14159, 2)   # 3.14
min(3, 1, 2)        # 1
max(3, 1, 2)        # 3
sum([1, 2, 3])      # 6
```
---

# CONDITIONALS

---

## If-Elif-Else

```py
if age < 13:
    category = "child"
elif age < 20:
    category = "teenager"
else:
    category = "adult"
```
---

## Comparison Operators

```py
x == y  # Equal to
x != y  # Not Equal to
x < y   # Less than
x > y   # Greater than
x >= y  # Greater than or Equal to
x <= y  # Less than or Equal to
```
---

## Logical Operators

<p>Just use the words themselves. Simple and clear.</p><br>

```py
if age >= 18 and has_car:
    print("Guy has car wau")
if is_weekend or is_holiday:
    print("No school")
if not is_raining:
    print("You can go outside.")
```
---

# LOOPS

---

## For Loops

```py
# Looping through a range
for i in range(5):      # 0, 1, 2, 3, 4
    print(i) 

# Looping through a list
fruits = ["Apple", "Banana"]
for variable in fruits:
    print(variable)     

    # Apple
    # Banana

# You can actually combine text formatting and you can number the data in this
fruits = ["Apple", "Banana"]
for i, variable in enumerate(fruits):
    print(f"{i}: {variable}") 
    
    # 0: Apple
    # 1: Banana
```
---

## While Loops

```py
while True:
    user_input = input("Enter 'quit' to exit: ")
    if user_input == "quit":
        break
    print(f"You entered: {user_input}")
```
---

## Loop Control

```py
for i in range(10):
    if i == 3:
        continue    # skip that particular iteration if condition is met
    if i == 7:
        break       # Exit loop
    print(i)
```
---

# FUNCTIONS

---

## Defining Functions

```py
def greet():
    return "Hello!"

def greet_person(name):
    return f"Hello, {name}!"

def add(x, y = 10):         # Default Parameter
    return x + y
```
---

## Calling the functions

```py
greet()                 # "Hello!"
greet_person("Kaiki")   # "Hello, Kaiki!"
add(5, 3)               # 8
add(7)                  # 17
```
---

## Return values

```py
def get_min_max(numbers):
    return min(numbers), max(numbers)
    
minimum, maximum = get_min_max([1, 5, 3]) # Since this function returns two values, so it needs two receivers
```
---

## Some Built-in functions

<p>I don't use all of these on a regular basis but some of these are super helpful</p><br>

```py
callable()  # Checks if the object can be called as a function
dir()       # Lists attributes and methods
globals()   # Get a dictionary of the current global symbol table. Global symbol table being the list of all globally defined symbols
hash()      # Get the hash value
id()        # Get the unique identifier
locals()    # Get a dictionary of the current local symbol table
repr()      # Get a string representation for debugging
```
---

## Lambda functions

```py
square = lambda x: x**2 # lambda is somewhat like a Macro. Basically a mini function
result = square(5)

# With Map and filter
numbers = [1, 2, 3, 4]
squared = list(map(lambda x: x**2, numbers))            # Squares every number in the list. so squared = [1, 4, 9, 16]
evens   = list(filter(lambda x: x % 2 == 0, numbers))   # Checks which of the data is even and only stores that as the result. [2, 4] is stored in this case
```

---

# CLASSES

---

## Defining classes

```py
class Dog:
    def __init__(self, name, age): # Constructor (initializer)
        self.name = name
        self.age = age

    def bark(self):     # You need "self" here if you want to use the data associated with the class
        return f"{self.name} says Woof!"

# Creating an instance of the class
my_dog = Dog("Dawg", 3)

# Accessing the bark function as a method
print(my_dog.bark()) # Dawg says Woof!
```
---

## Class Attributes and Methods

```py
class Cat:
    species = "Felis catus"

    def __init__(self, name):
        self.name = name

    def meow(self):
        return f"{self.name} says Meow!"

    @classmethod
    def create_kitten(cls, name): # This receieves the class itself "cls" and This uses the "factory" pattern from the gang of four book 
        return cls(f"Baby {name}")


c = Cat("Luna")
k = Cat.create_kitten("Luna") # can be done, so the name of the cat becomes "Baby Luna"
```
---

## Inheritance

```py
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        pass # Use pass if you want to keep a function empty
    
class Dog(Animal):
    def speak(self):
        return f"{self.name} barks!"
```
---

# EXCEPTIONS

---

## Try-Except

```py
try:
    number = int(input("Enter a number: "))
    result = 10 / number

except ValueError:
    print("That is not a valid number")
except ZeroDivisionError:
    print("Cannot divide by zero")
else:
    print(f"Result: {result}")
finally:
    print("Calculation Attempted")
```
---

## Some common exceptions

```py
ValueError          # Invalid value
TypeError           # Wrong type
IndexError          # List index out of range
KeyError            # Dictionary doesn't exist / Not found
FileNotFoundError   # File doesn't exist   
```
---

## Raising Exceptions

```py
def validate_age(age):
    if age < 0:
        raise ValueError("Age cannot be negative")
    return age
```
---

# COLLECTIONS

---

## Lists

```py
# Creating lists
empty = []
nums = [5]
mixed = [1, "two", 3.0, True]

# List methods
nums.append("x")        # Add to end
nums.insert(0, "y")     # Insert at index 0
nums.extend(["z", 5])   # Extend with iterable
nums.remove("x")        # Remove first "x"
last = nums.pop()       # Pop returns last element

# List indexing and checks
fruits = ["banana", "apple", "orange"]
fruits[0]           # "banana"
fruits[-1]          # "orange" 
"apple" in fruits   # True
len(fruits)         # 3
```
---

## Tuples

```py
# Creating tuples
point = (3, 4)
single = (1, )      # comma isn't a mistake here
empty = ()

# Basic tuple unpacking
point = (3, 4)
x, y = point
x                   # 3
y                   # 4

# Extended unpacking
first, *rest = (1, 2, 3, 4)
first               # 1
rest                # [2, 3, 4]
```
---

## Sets

```py
# Creating Sets
a = {1, 2, 3}
b = set([3, 4, 4, 5])

# Set Operations
a | b       # {1, 2, 3, 4, 5}
a & b       # {3}
a - b       # {1, 2}
a ^ b       # {1, 2, 4, 5}
```
---

## Dictionaries

```py
# Creating Dictionaries
empty = {}
pet = {"name": "Leo", "age": 42}

# Dictionary Operations
pet["sound"] = "Purr!"      # Add key and value
pet["age"] = 7              # Update Value
age = pet.get("age", 0)     # Get with default
del pet["sound"]            # Delete key
pet.pop("age")              # Remove and return

# Dictionary Methods
pet = {"name": "Frieda", "sound": "Bark!"}
pet.keys()              # dict_keys(['name', 'sound'])
pet.values()            # dict_values(['Frieda', 'Bark!'])
pet.items()             # dict_items([('name', 'Frieda'), ('sound', 'Bark!')])
```
---

# COMPREHENSIONS

---

## List Comprehensions

```py
# Basic
squares = [x**2 for x in range(10)]

# With Condition
evens = [x for x in range(20) if x % 2 == 0]

# Nested
matrix = [[i * j for j in range(3)] for i in range(3)]
```
---

## Other Comprehensions

```py
# Dictionary Comprehension
word_lengths = {word: len(word) for word in ["hello", "world"]}

# Set Comprehension
unique_lengths = {len(word) for word in ["who", "what", "why"]}

# Generator Expression
sum_squares = sum(x**2 for x in range(1000))
```
---

# FILE I/O

---

## File Operations

```py
# Read an entire file
with open("file.txt", mode = "r", encoding = "utf-8") as file:
    content = file.read()

# Read a file line by line
with open("file.txt", mode = "r", encoding = "utf-8") as file:
    for line in file:
        print(line.strip())

# Write a file
with open("output.txt", mode = "w", encoding = "utf-8") as file:
    file.write("Hello, World!\n")

# Append to a file
with open("log.txt", mode = "a", encoding = "utf-8") as file:
    file.write("New log entry\n")
```
---

# IMPORTS AND MODULES

---

## Import Styles

```py
# Import Entire module
import math
result = math.sqrt(16)

# Import specific function
from math import sqrt
result = sqrt(16)

# Import with alias
import numpy as np
array = np.array([1, 2, 3])

# Import all (don't use this frequently)
from math import *
```
---

## Package imports

```py
# Import from package
import package.module
from package import module
from package.subpackage import module

# Import specific items
from package.module import function, Class
from package.module import name as alias
```
---

# VIRTUAL ENVIRONMENTS

---

## Create a virtual environment

```shell
python -m venv .venv
```
---

## Activate the virtual environment (powershell)

```shell
.venv\Scripts\activate.bat
```
---

## Activate the virtual environment (Linux, WSL)

```shell
source .venv/bin/activate
```
---

## Deactivating the virtual environment

```shell
(.venv) $ deactivate
```
---

# Packages in virtual environment

---

## Installing package using pip

```shell
# Use the second one rather than the first one. It's good practice

pip install package_name # This installs it in the system

# and

python -m pip install requests # This installs stuff in the current environment
```
---

## Save Requirements and Install requirements from file

```shell
python -m pip freeze > requirements.txt
python -m pip install -r requirements.txt
```
---

# MISCELLANEOUS

---

## Pythonic Constructs

```py
# Swap Variables
a, b = b, a

# Flatten a list of lists
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
flat = [item for sublist in matrix for item in sublist]

# Remove Duplicates
unique_unordered = list(set(my_list))

# Remove Duplicates, preserve order
unique = list(dict.fromkeys(my_list))

# Count occurrences
from collections import Counter
counts = Counter(my_list)
```