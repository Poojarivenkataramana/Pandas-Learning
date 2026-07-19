# 🐼 Pandas Learning – Day 05

## 📚 Topics Covered

Today I learned the following Pandas Data Cleaning concepts:

1. 📌 What are Missing Values?
2. 🔍 `isnull()`
3. ✅ `notnull()`
4. 🛠️ `fillna()`

---

# 1️⃣ What are Missing Values?

## 📖 Definition
Missing values are empty or unavailable data in a dataset.

Pandas represents missing values as **NaN (Not a Number).**

## 📝 Syntax
```python
NaN
```

## 💡 Example

```python
import pandas as pd

df = pd.DataFrame({
    "Name":["Ram","Rahul"],
    "Age":[20,None]
})
```

Output

```
   Name   Age
0   Ram  20.0
1 Rahul   NaN
```

---

# 2️⃣ isnull()

## 📖 Definition

`isnull()` checks whether values are missing.

Returns **True** for missing values and **False** otherwise.

## 📝 Syntax

```python
df.isnull()
```

## 💡 Example

```python
df.isnull()
```

Output

```
    Name    Age
0  False  False
1  False   True
```

---

# 3️⃣ notnull()

## 📖 Definition

`notnull()` checks whether values are available.

Returns **True** for non-missing values and **False** for missing values.

## 📝 Syntax

```python
df.notnull()
```

## 💡 Example

```python
df.notnull()
```

Output

```
    Name    Age
0   True   True
1   True  False
```

---

# 4️⃣ fillna()

## 📖 Definition

`fillna()` replaces missing values with a specified value.

## 📝 Syntax

```python
df.fillna(value)
```

## 💡 Example

```python
df.fillna(0)
```

Output

```
    Name   Age
0    Ram   20
1  Rahul    0
```

Another Example

```python
df["Age"] = df["Age"].fillna(df["Age"].mean())
```

---

# 📌 Summary

✅ Learned about Missing Values

✅ Detected missing values using `isnull()`

✅ Checked available values using `notnull()`

✅ Filled missing values using `fillna()`

---

# 🚀 Next Topics

- `dropna()`
- `replace()`
- `duplicated()`
- `drop_duplicates()`

---

## ⭐ Day 05 Progress

**Topics Covered:** 4

**Topics Remaining:** 4

**Status:** ✅ Completed
