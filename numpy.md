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
---

## Array with values

```py
# 1D array of length 3; all values set to 0
arr = np.zeros(3)

# 3x4 array with all values set to 1
arr = np.ones((3, 4))

# 5x5 array of 0 with 1 on diagonal (identity matrix)
arr = np.eye(5)
```
---

## Array with values #2

```py
# LINSPACE
# Array of 6 evenly divided values from 0 to 100
arr.linspace(0, 100, 6) # [0, 20, 40, 60, 80, 100]

# ARANGE
# Array of values from 0 to less than 10 with step 3
arr = np.arange(0, 10, 3) # [0, 3, 6, 9]

# 2x3 array with all values set to 8
arr = np.full((2, 3), 8)

# 4x5 array with random floats between 0 and 1
arr = np.random.rand(4, 5)

# 6x7 array of random floats between 0 - 100
arr = np.random.rand(6, 7) * 100

# 2x3 array with random integers between 0 and 4
arr = np.random.randint(5, size = (2, 3))
```
---

# ASKING FOR HELP

---

```py
# Views documentation for np.eye
np.info(np.eye)
```
---

# INSPECTING PROPERTIES

---

## Conversions

```py
# Convert arr elements to type dtype
arr.astype(dtype)

# Convert arr to a python list
arr.tolist()
```
---

## Returning size, shape, type etc

```py
# Returns number of elements in arr
arr.size

# Returns dimensions of arr (rows, columns)
arr.shape

# Returns type of elements in arr
arr.dtype
```
---

# COPYING, SORTING AND RESHAPING

---

```py
# Creates arr to new memory 
np.copy(arr)

# Creates view of arr elements with type dtype
np.view(dtype)

# Sorts arr
arr.sort()

# Sorts specific axis of arr
arr.sort(axis = 0)

# Flattens 2D array "two_d_arr" to 1D
two_d_arr.flatten()

# Transposes arr
arr.T

# Reshapes arr to 3 rows, 4 columns without changing the data
arr.reshape(3, 4)

# Changes arr shape to 5x6 and fills new values with 0
arr.resize((5, 6))
```
---

# ADDING AND REMOVING ELEMENTS

---

## Append

```py
# Appends values to the end of arr (like vector.push_back(value) in STL)
np.append(arr, values)
```
---

## Insert

```py
# Inserts values into arr before index 2
np.insert(arr, 2, values)
```
---

## Delete

```py
# Deletes row on index 3 of arr
np.delete(arr, 3, axis = 0)

# Removes the 5th column from arr
np.delete(arr, 4, axis = 1)
```
---