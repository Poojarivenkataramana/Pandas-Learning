# 🐼 Pandas Day 04 – Sorting, Renaming & Creating Columns

## 📚 Topics Covered

- ✅ `sort_values()`
- ✅ `sort_index()`
- ✅ Multi-column Sorting
- ✅ `rename()`
- ✅ Create a New Column
- ✅ Update an Existing Column
- ✅ Drop a Column
- ✅ `inplace=True` vs Assignment
- ✅ SQL vs Pandas
- ✅ Practice Tasks
- ✅ Rapid Fire Interview Questions

---

# 1️⃣ sort_values()

### 📖 Definition

`sort_values()` is used to sort a DataFrame based on one or more column values.

### 📝 Syntax

```python
df.sort_values(
    by="Column_Name",
    ascending=True
)
```

### 💡 Example

```python
df.sort_values(by="Salary")
```

```python
df.sort_values(by="Salary", ascending=False)
```

---

# 2️⃣ Multi-column Sorting

### 📖 Definition

Sorts data using multiple columns.

Pandas sorts by the first column first and then sorts matching values using the second column.

### 📝 Syntax

```python
df.sort_values(
    by=["Department","Salary"],
    ascending=[True,False]
)
```

### 💡 Example

```python
df.sort_values(
    by=["Department","Salary"],
    ascending=[True,False]
)
```

---

# 3️⃣ sort_index()

### 📖 Definition

Sorts a DataFrame based on index values.

### 📝 Syntax

```python
df.sort_index()
```

```python
df.sort_index(ascending=False)
```

### 💡 Example

```python
df.sort_index()
```

---

# 4️⃣ rename()

### 📖 Definition

Changes one or more column names.

### 📝 Syntax

```python
df.rename(
    columns={
        "Old":"New"
    }
)
```

### 💡 Example

```python
df.rename(
    columns={
        "Salary":"Monthly_Salary"
    }
)
```

---

# 5️⃣ Create a New Column

### 📖 Definition

Creates a brand-new column using existing data or calculations.

### 📝 Syntax

```python
df["New_Column"] = value
```

### 💡 Example

```python
df["Bonus"] = df["Salary"] * 0.10
```

---

# 6️⃣ Update an Existing Column

### 📖 Definition

Modifies values in an existing column.

### 📝 Syntax

```python
df["Column"] = new_value
```

### 💡 Example

```python
df["Salary"] = df["Salary"] * 1.05
```

---

# 7️⃣ Drop a Column

### 📖 Definition

Removes one or more columns from a DataFrame.

### 📝 Syntax

```python
df.drop(columns=["Column"])
```

### 💡 Example

```python
df.drop(columns=["Bonus"])
```

Permanent deletion

```python
df.drop(columns=["Bonus"], inplace=True)
```

---

# 8️⃣ inplace=True vs Assignment

### Assignment

```python
df = df.rename(columns={"Salary":"Monthly_Salary"})
```

✅ Returns a new DataFrame.

---

### inplace=True

```python
df.rename(
    columns={"Salary":"Monthly_Salary"},
    inplace=True
)
```

✅ Modifies the original DataFrame.

---

# 9️⃣ SQL vs Pandas

| SQL | Pandas |
|------|---------|
| ORDER BY ASC | `sort_values()` |
| ORDER BY DESC | `sort_values(ascending=False)` |
| AS | `rename()` |
| Calculated Column | `df["New"]=...` |
| ALTER TABLE DROP COLUMN | `drop(columns=...)` |

---

# 🎯 Key Takeaways

- `sort_values()` sorts rows by column values.
- `sort_index()` sorts by index.
- `rename()` changes column names.
- New columns are created using assignment.
- Existing columns can be updated.
- `drop()` removes columns.
- Most Pandas methods return a new DataFrame.
- Use `inplace=True` to modify the original DataFrame.

---

# 🚀 What's Next?

**Day 05**

- Missing Values
- `isna()`
- `fillna()`
- `dropna()`
- Duplicate Values
- `replace()`
