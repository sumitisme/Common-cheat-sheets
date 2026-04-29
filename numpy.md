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
arr.sort(axis = 0) # axis = 0 means row, axis = 1 means column

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

# COMBINING AND SPLITTING

---

## Concatenate

```py
# Adds arr2 as rows to the end of arr1
np.concatenate((arr1, arr2), axis = 0)

# Adds arr2 as columns to the end of arr1
np.concatenate((arr1, arr2), axis = 1)
```
---

## Split

```py
# Splits arr into 3 sub-arrays
np.split(arr, 3)
```
---

## Hsplit

```py
# Splits arr horizontally on the index 5
np.hsplit(arr, 5)
```
---

# INDEXING AND SLICING

---

## Indexing

```py
# Returns the element at index 5
arr[5]

# Returns the 2D array element on index [2][5]
arr[2, 5]

# Assigns array element on index 1 the value 4
arr[1] = 4

# Assigns array element on index [1][3] the value 10
arr[1, 3] = 10
```
---

## Slicing

```py
# Returns the elements at indices 0, 1, 2
arr[0:3]

# Returns the elements on rows 0, 1, 2 in column index 4
arr[0:3, 4]

# Returns the elements at index 0, 1
arr[:2]

# Returns column index 1, all rows
arr[:, 1]
```
---

# CONDITIONAL STATEMENTS

---

```py
# Returns an array of boolean values
arr < 5

# For the following to be true, both must be true
(arr1 < 3) & (arr2 > 5)

# Inverts a boolean array
~arr

# Returns array elements less than 5
arr[arr < 5]

# For the following to be true, at least one must be true
(arr1 < 3) | (arr2 > 5)
```
---

# SCALAR MATH

---

## Add

```py
# Add 1 to each array element
np.add(arr, 1)
```
---

## Subtract

```py
# Subtract 2 from each element
np.subtract(arr, 2)
```
---

## Mutiply

```py
# Multiply each array element by 3
np.multiply(arr, 3)
```
---

## Divide

```py
# Divide each array element by 4 (returns np.nan for division by zero)
np.divide(arr, 4)
```
---

## Power

```py
# Raise each array element to the power of 5
np.power(arr, 5)
```
---

# VECTOR MATH

---

## Add

```py
# Elementwise add arr1 to arr2
np.add(arr1, arr2)
```
---

## Subtract

```py
# Elementwise subract arr2 from arr1
np.subtract(arr1, arr2)
```
---

## Multiply

```py
# Elementwise multiply arr1 by arr2
np.multiply(arr1, arr2)
```
---

## Divide

```py
# Elementwise divide arr1 by arr2
np.divide(arr1, arr2)
```
---

## Power

```py
# Elementwise raise arr1 to the power of arr2
np.power(arr1, arr2)
```
---

## Array_equal

```py
# Following returns True if the arrays have the same elements and shape
np.array_equal(arr1, arr2)
```
---

## Sqrt

```py
# Square root of each element in the array
np.sqrt(arr)
```
---

## Sin

```py
# Sine of each element in the array
np.sin(arr)
```
---

## Log

```py
# Natural log of each element in the array
np.log(arr)
```
---

## Abs

```py
# Absolute value of each element in the array
np.abs(arr)
```
---

## Ceil

```py
# Does the ceiling operation on each element of arr
np.ceil(arr)
```
---

## Floor

```py
# Does the floor operation on each element of arr
np.floor(arr)
```
---

## Round

```py
# Rounds each element to the nearest integer
np.round(arr)
```