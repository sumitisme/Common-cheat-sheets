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

# LOCATING ROWS AND COLUMNS

---

## loc, iloc, at, iat

```py
# To select rows 10-20
df.iloc[10:20]

# To select columns in positions 1, 2, 5 (first column is 0)
df.iloc[:, [1, 2, 5]] # first part meaning range of rows, second meaning range of columns

# To select all columns between x2 and x4 (inclusive)
df.loc[:, 'x2':'x4']

# To select rows meeting given logical condition and only at the specific columns
df.loc[df['a'] > 10, ['a', 'c']]

# To access single value by index
df.iat[1, 2]

# To access single value by label
df.at[4, 'A']
```
---

# SELECTING ROWS AND COLUMNS

---

## For Rows

```py
# Extract rows that meet logical criteria
df[df.Length > 7]

# Removing duplicate rows
df.drop_duplicates()

# Randomly selecting a fraction of rows
df.sample(frac = 0.5)

# Randomly select n rows
df.sample(n = 10)

# Selecting and ordering top n entries
df.nlargest(n, 'value')

# Selecting and ordering bottom n entries
df.nsmallest(n, 'value')

# Selecting first n rows
df.head(n)

# Selecting last n rows
df.tail(n)
```
---

## For Columns

```py
# Selecting multiple columns with specific names
df[['width', 'length', 'species']]

# Selecting a single column with a specific name
df['width'] # or df.width

# Selecting columns whose name (string) matches regex
df.filter(regex = 'regex')
```
---

# REGEX AND LOGIC

---

```py
# Some regex examples
'\.'                # Matches strings containing a period '.'
'Length$'           # Matches strings ending with word 'Length'
'^Sepal'            # Matches strings beginning with the world 'Sepal'
'^x[1-5]$'          # Matches strings beginning with 'x' and ending witth 1, 2, 3, 4, 5
'^(?!Species$).*'   # Matches strings except the string 'Species'

# General note
^       # First / Beginning
$       # Ending
```

```py
df.column.isin(values)  # Group membership
pd.isnull(obj)          # is NaN
pd.notnull(obj)         # is not NaN
df.any()
df.all()
```

---

# BASIC FILTERING

---

## Using Query

```py
# You can filter rows using Boolean expressions
df.query('Length > 7')
df.query('Length > 7 and Width < 8')

# Name is the column name
df.query('Name.str.startswith("abc")', engine = "python")
```
---

# METHOD CHAINING

---

```py
df =    (pd.melt(df)
            .rename(columns = {
                'variable'  : 'var',
                'value'     : 'val'
            })
            .query('val >= 200')
        )
```
---

# GROUPING DATA

---

## This will help with my original time series forecasting plans

```py
df.groupby(by = "col")      # Return a GroupBy object, grouped by values in column named "col"
df.groupby(level = "ind")   # Return a GroupBy object, grouped by values in index level named "ind"


# you can use summary functions with the groups
size()      # For size of each group
agg()       # For aggregate group using function
```
---

## Combining Datasets

```py
# Standard joins

# Joins matching rows from bdf to adf
pd.merge(adf, bdf, how = 'left', on = 'x1') # x1 is a column name here btw

# Joins matching rows from adf to bdf
pd.merge(adf, bdf, how = 'right', on = 'x1')

# Joins data while retaining values on both sets
pd.merge(adf, bdf, how = 'inner', on = 'x1')

# Joins data while retaining values on all rows
pd.merge(adf, bdf, how = 'outer', on = 'x1')


# Filtering joins

# All rows in adf that have a match in bdf
adf[adf.x1.isin(bdf.x1)]

# All rows in adf that don't have a match in bdf
adf[~adf.x1.isin(bdf.x1)]
```
---

## Set-like operations

```py
# Intersection
pd.merge(ydf, zdf)

# Union
pd.merge(ydf, zdf, how = 'outer')

# Rows that appear in ydf but not in zdf (Setdiff)
pd.merge(ydf, zdf, how = 'outer', indicator = True)
    .query('_merge == "left_only"')
    .drop(columns = ['_merge'])
```