# <span style="color:green">Numpy Cheat sheet</span>

---

# IMPORTING NUMPY

---

```py
# Formality
import numpy as np
```
---

# CREATING ARRAYS

---

## 1d, 2d and 3d arrays

```py
# 1d
a = np.array([1, 2, 3])

# 2d
b = np.array([(1.5, 2, 3), (4, 5, 6)], dtype = float)

# 3d
c = np.array([[(1.5, 2, 3), (4, 5, 6)], [(3, 2, 1), (4, 5, 6)]], dtype = float)
```
---

## Initial Placeholders

```py
# Create an array of zeros
np.zeros((3, 4)) 

# Create an array of ones, data type -> int16
np.ones((2, 3, 4), dtype = np.int16)

# Create an array of evenly spaced values (step values)
d = np.arange(10, 25, 5) # 10 to 25, with step 5

# Create an array of evenly spaced values (number of samples)
np.linspace(0, 2, 9)

# Create a constant array
e = np.full((2, 2), 7) 

# Create a 2 x 2 identity matrix
f = np.eye(2)

# Create an array with random values
np.random.random((2, 2))

# Create an empty array
np.empty((3, 2))
```
---

# I/O

---

## Saving and Loading on a disk

```py
np.save('my_array', a)
np.savez('array.npz', a, b)
np.load('my_array.npy')
```

---

## Saving and Loading Text Files

```py
np.loadtxt("myfile.txt")
np.getfromtxt("myfile.csv", delimiter = ',')
np.savetxt("myarray.txt", delimiter = " ")
```
---

# ASKING FOR HELP 

---

```py
np.info(np.ndarray.dtype)
```
---

# INSPECTING YOUR ARRAY

---

```py
# Array dimensions
a.shape

# Length of array
len(a)

# Number of array dimensions
b.ndim

# Number of array elements
e.size

# Data type of array elements
b.dtype

# Name of data type
b.dtype.name

# Convert an array to a different type
b.astype(int)
```
---

# DATA TYPES

---

```py
# Signed 64-bit integer types
np.int64

# Standard double-precision floating point
np.float32

# Complex numbers represented by 128 floats
np.complex

# Boolean type staring TRUE and FALSE values
np.bool

# Python object type
np.object

# Fixed-length string type
np.string_

# Fixed-length unicode type
np.unicode_
```
---

# Array Mathematics

---

## Arithmetic operations

```py

# a, b and c are numpy arrays with the values
# a = [(1, 2, 3)]
# b = [(1.5, 2, 3), (4, 5, 6)]
# c = [[(1.5, 2, 3), (4, 5, 6)] , [(3, 2, 1), (4, 5, 6)]]

# Subtraction
g = a - b
np.subtract(a, b) # Do np.subtract(a, b, out = a) if you want to directly store to a, it's generally faster iirc

    # RESULTS : array([-0.5, 0., 0.], [-3., -3., -3.])

# Addition
b + a
np.add(b, a)

    # RESULTS : array([[3.5, 4. , 6. ], [5. , 7. , 9. ]])

# Division
a / b
np.divide(a, b)

    # RESULTS : array([[0.66666667, 1. , 1. ], [0.25, 0.4, 0.5]])

# Multiplication
a * b
np.multiply(a, b)

# RESULTS : array([[1.5, 4. , 9. ], [4. , 10. , 18. ]])

# Exponentiation
np.exp(b)

# Square root
np.sqrt(b)

# Print Sines of an array
np.sin(a)

# Element-wise cosine
np.cos(b)

# Element-wise natural logarithm
np.log(a)

# Dot product
e.dot(f)

# RESULTS : ([[7. , 7. ],[7. , 7. ]])    
```