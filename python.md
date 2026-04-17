# <span style="color:green">Python Cheat sheet</span>
---

<p>
<span style="color:pink">These commands are being run on the shell, not the .py program</span>
</p>

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