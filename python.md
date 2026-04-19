# <span style="color:green">Python Cheat sheet</span>
---

<p>
<span style="color:pink">A lot of these commands are being run on the shell, not the .py program</span>
</p>

# Random Basics (Shell part and normal assignments)
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

# Strings

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

# Mathematical Operations

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

# Conditionals

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

# Loops

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

# Functions

---

## Defining Functions

```py
```