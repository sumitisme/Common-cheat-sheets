# <span style="color:green">Numpy Cheat sheet</span>

---

# IMPORTING NUMPY

---

```py
# Formality
import numpy as np
```
---

# IMPORTING DATA

---

## Creating an array from a .txt file

```py
# loadtxt
np.loadtxt('file.txt')
```
---

## Creating an array from a .csv file

```py
# genfromtxt
np.genfromtxt('file.csv', delimeter = ',')
```
---

## Writing an array to a .txt file

```py
# savetxt
np.savetxt('file.txt', arr, delimeter = ' ')
```
---

## Writing an array to a .csv file

```py
np.savetxt('file.csv', arr, delimiter = ',')
```
---

# CREATING ARRAYS

---

## Creating a 1D array

```py
# array
arr = np.array([1, 2, 3])
```
---

## Creating a 2D array

```py
arr = np.array([(1, 2, 3), (4, 5, 6)])
```