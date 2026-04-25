# <span style="color:green">Pandas Cheat sheet</span>

---

# CREATING DATAFRAMES

---

## Simple dataFrame

```py

# Two general ways of creating a DataFrame, I prefer the latter since it keeps things clear

# Specifying value for each column
df = pd.DataFrame(
    {
        "a" : [4, 5, 6],
        "b" : [7, 8, 9],
        "c" : [10, 11, 12]
    },
    index = [1, 2, 3]
)


# Specifying value for each row
df = pd.DataFrame(
    [
        [4, 7, 10],
        [5, 8, 11],
        [6, 9, 12]
    ],
    index   = [1, 2, 3],
    columns = ['a', 'b', 'c'] 
)
```

```py
# The dataframe will look like this

#    |  a | b | c
# ------------------
# 1  |  4 | 7 | 10  
# 2  |  5 | 8 | 11
# 3  |  6 | 9 | 12
```
---

## DataFrame with multi-index

```py
df = pd.DataFrame(
    {
        "a" : [4, 5, 6],
        "b" : [7, 8, 9],
        "c" : [10, 11, 12]
    },
    index = pd.MultiIndex.from_tuples(
        [
            ('d', 1), ('d', 2), ('e', 2)
        ],
        names = ['n', 'v']
    )
)
```

```py
# The dataframe will look like this

#         |   a | b | c
#   --------------------
#   n | v | 
#   --------------------
#   d | 1 |   4 | 7 | 10
#     | 2 |   5 | 8 | 11
#   --------------------
#   e | 2 |   6 | 9 | 12


# "d" will cover index 1 and 2 simultanuously and n and v are the names for the columns containing the index value and the multi index value
```
---

# RESHAPING THE DATA

---

## Appending the ROWS of two DataFrames

```py
pd.concat([df1, df2])
```
---

## Appending the COLUMNS of two Dataframes

```py
pd.concat([df1, df2], axis = 1)
```
---

## Gathering columns into rows

```py
pd.melt(df)
```
---

## Spreading rows into columns

```py
df.pivot(columns = 'var', values = 'val')
```
---

## Sorting, Renaming, Indexing and Dropping

```py
# To order the rows by values of a column "Column_name" (low to high)
df.sort_values('Column_name')

# To order the rows by values of a column (high to low)
df.sort_values('Column_name', ascending = False)

# To Rename the columns of a DataFrame
df.rename(columns = {'OldName': 'NewName'})

# Sort the index of a DataFrame
df.sort_index()

# Reset the index of a DataFrame to row numbers, moving index to columns
df.reset_index()

# To drop the columns from a DataFrame
df.drop(columns = ['Length', 'Height'])
```
---