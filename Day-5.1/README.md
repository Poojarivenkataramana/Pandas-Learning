# Day 5 – Part 2: Handling Missing Values and Duplicates in Pandas

In this part of my Pandas learning journey, I practiced four important data-cleaning methods:

- `dropna()`
- `replace()`
- `duplicated()`
- `drop_duplicates()`

All examples below use a small employee dataset designed to contain duplicate rows.

---

## Sample Practice Dataset

```python
import pandas as pd

data = {
    'EmpID': [101, 102, 103, 101, 104, 105, 102, 106],
    'Name': ['Ravi', 'Anita', 'Kiran', 'Ravi', 'Meena', 'Arun', 'Anita', 'Divya'],
    'Age': [28, 25, 30, 28, 32, 27, 25, 29],
    'City': ['Hyderabad', 'Chennai', 'Bangalore', 'Hyderabad', 'Pune', 'Delhi', 'Chennai', 'Mumbai'],
    'Salary': [45000, 40000, 52000, 45000, 48000, 39000, 40000, 55000]
}

df = pd.DataFrame(data)
print(df)
```

This dataset has intentional duplicate rows:
- Row 0 and row 3 are duplicates.
- Row 1 and row 6 are duplicates.

---

## 1. `dropna()` – Remove Missing Values

**Definition:**  
`dropna()` removes rows or columns that contain missing values (`NaN` / `None`). It is mainly used for cleaning incomplete data before analysis.[web:2][web:5]

**Basic syntax:**

```python
df.dropna(axis=0, how='any', subset=None, inplace=False)
```

- `axis=0` or `'index'`: drop rows with missing values (default).[web:2][web:4]  
- `axis=1` or `'columns'`: drop columns with missing values.[web:2][web:8]  
- `how='any'`: drop if *any* value in the row/column is NaN.[web:2][web:3]  
- `how='all'`: drop only if *all* values are NaN.[web:2][web:3]  
- `subset`: list of columns to check for NaN.[web:7]  
- `inplace=True`: modify the original DataFrame.[web:4][web:6]

**Example with the practice dataset (assuming some NaNs):**

```python
# Drop rows where Age or Salary is missing
df_clean = df.dropna(subset=['Age', 'Salary'])
```

---

## 2. `replace()` – Change Data Values

**Definition:**  
`replace()` replaces one or more existing values in the DataFrame with new values. It can handle numbers, strings, lists, dictionaries, and even regular expressions.[web:10][web:11]

**Basic syntax:**

```python
df.replace(to_replace, value, inplace=False, regex=False)
```

- `to_replace`: value(s) or pattern(s) you want to change.[web:10][web:12]  
- `value`: new value(s) to put in place.[web:10][web:13]  
- `regex=True`: treat `to_replace` as a regular expression.[web:10][web:16]  
- `inplace=True`: update the original DataFrame.[web:10][web:13]

**Examples on the practice dataset:**

```python
# Change city name spelling
df_city_fixed = df.replace('Hyderabad', 'Hyd')

# Replace multiple values using a dict
df_gender = df.copy()
df_gender['Gender'] = ['M', 'F', 'M', 'M', 'F', 'M', 'F', 'F']
df_gender['Gender'] = df_gender['Gender'].replace({'M': 'Male', 'F': 'Female'})
```

---

## 3. `duplicated()` – Detect Duplicate Rows

**Definition:**  
`duplicated()` returns a boolean Series indicating whether each row is a duplicate of a previous row. `True` means the row has appeared before with the same values; `False` means it is the first occurrence.[web:24]

**Basic syntax:**

```python
df.duplicated(subset=None, keep='first')
```

- `subset`: list of columns to use for identifying duplicates (default: all columns).[web:24]  
- `keep='first'`: mark duplicates except the first occurrence.[web:24]  
- `keep='last'`: mark duplicates except the last occurrence.[web:24]  
- `keep=False`: mark **all** duplicate occurrences as `True`.[web:24]

**Examples on the practice dataset:**

```python
# Check duplicates using all columns
print(df.duplicated())

# Count how many duplicate rows
print(df.duplicated().sum())

# Check duplicates only by Name and City
print(df.duplicated(subset=['Name', 'City']))
```

---

## 4. `drop_duplicates()` – Remove Duplicate Rows

**Definition:**  
`drop_duplicates()` removes duplicate rows from the DataFrame, keeping one copy of each unique row by default. It is used to clean repeated records before analysis.[web:23][web:29]

**Basic syntax:**

```python
df.drop_duplicates(subset=None, keep='first', inplace=False)
```

- `subset`: columns used to identify duplicates (default: all columns).[web:23]  
- `keep='first'`: keep the first occurrence and drop later duplicates.[web:23]  
- `keep='last'`: keep the last occurrence and drop earlier duplicates.[web:23]  
- `keep=False`: drop **all** duplicates, keeping only rows that appear once.[web:23]  
- `inplace=True`: modify the original DataFrame.[web:23]

**Examples on the practice dataset:**

```python
# Remove duplicate rows based on all columns, keep first
df_no_dups = df.drop_duplicates()

# Remove duplicates, keep the last occurrence
df_no_dups_last = df.drop_duplicates(keep='last')

# Remove duplicates based only on Name and City
df_unique_name_city = df.drop_duplicates(subset=['Name', 'City'])
```

---

## Quick Summary Table

```markdown
| Method            | Main purpose                        | Acts on                      | Typical use case                              |
|-------------------|--------------------------------------|------------------------------|-----------------------------------------------|
| `dropna()`        | Remove missing values                | Rows or columns              | Clean NaN/None before analysis                |
| `replace()`       | Change data values                   | Cell values                  | Fix labels, codes, or inconsistent values     |
| `duplicated()`    | Detect duplicate rows                | Boolean result per row       | Identify where duplicates exist               |
| `drop_duplicates()` | Remove duplicate rows             | Rows                         | Keep only unique records in a dataset         |
```
