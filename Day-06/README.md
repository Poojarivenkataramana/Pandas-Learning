# 🐼 Pandas Day 6 – GroupBy & Aggregation

> One of the most important topics in Pandas — used constantly in real-world data analysis and interviews.

---

## 🎯 Why do we use `groupby()`?

Imagine your manager asks:

> "What's the average salary in each department?"

Your data looks like this:

| Name  | Department | Salary |
|-------|------------|--------|
| Ram   | IT         | 70000  |
| Sita  | HR         | 50000  |
| Ravi  | IT         | 80000  |
| Priya | HR         | 60000  |
| Arjun | Finance    | 90000  |

You don't want the average of **all** employees — you want the average **within each department**.

That's exactly what `groupby()` does.

---

## 📖 Definition

> `groupby()` groups rows that have the same value in one or more columns so you can perform calculations on each group independently.

---

## 🏫 Real-World Example

Think of sorting students into classrooms.

Instead of treating all students as one big group:

```
All Students
│
├── Class A
├── Class B
└── Class C
```

Now you can calculate:
- Average marks in Class A
- Highest marks in Class B
- Number of students in Class C

`groupby()` works the same way.

---

## 🧩 Syntax

```python
df.groupby("ColumnName")
```

By itself, this only **creates groups**.
To get useful results, combine it with an **aggregation function**.

---

## 📊 Common Aggregation Functions

| Function  | Purpose                          |
|-----------|-----------------------------------|
| `sum()`   | Total                             |
| `mean()`  | Average                           |
| `max()`   | Highest value                     |
| `min()`   | Lowest value                      |
| `count()` | Count non-null values             |
| `size()`  | Count rows (including nulls)      |

---

## 🗂️ Example Dataset

```python
import pandas as pd

data = {
    "Name": ["Ram", "Sita", "Ravi", "Priya", "Arjun", "Kiran"],
    "Department": ["IT", "HR", "IT", "HR", "Finance", "IT"],
    "Salary": [70000, 50000, 80000, 60000, 90000, 75000],
    "Age": [25, 27, 30, 26, 32, 29]
}

df = pd.DataFrame(data)
print(df)
```

---

## Example 1 – Average Salary by Department

```python
df.groupby("Department")["Salary"].mean()
```

**Output:**

| Department | Average Salary |
|------------|-----------------|
| Finance    | 90000           |
| HR         | 55000           |
| IT         | 75000           |

**How it works:**

Pandas first groups the rows:

```
IT
----
70000
80000
75000

HR
----
50000
60000

Finance
---------
90000
```

Then it calculates the average for each group.

---

## Example 2 – Maximum Salary

```python
df.groupby("Department")["Salary"].max()
```

| Department | Max Salary |
|------------|------------|
| Finance    | 90000      |
| HR         | 60000      |
| IT         | 80000      |

---

## Example 3 – Minimum Salary

```python
df.groupby("Department")["Salary"].min()
```

---

## Example 4 – Total Salary

```python
df.groupby("Department")["Salary"].sum()
```

---

## Example 5 – Employee Count

```python
df.groupby("Department")["Name"].count()
```
or
```python
df.groupby("Department").size()
```

Both count employees, but there's a subtle difference:

- `count()` → ignores missing (`NaN`) values in the selected column
- `size()` → counts **every** row in each group

---

## ⚡ Multiple Aggregations at Once

Instead of writing four separate queries:

```python
df.groupby("Department")["Salary"].agg(
    ["count", "sum", "mean", "min", "max"]
)
```

**Output:**

| Department | count | sum    | mean  | min   | max   |
|------------|-------|--------|-------|-------|-------|
| Finance    | 1     | 90000  | 90000 | 90000 | 90000 |
| HR         | 2     | 110000 | 55000 | 50000 | 60000 |
| IT         | 3     | 225000 | 75000 | 70000 | 80000 |

> 💡 This is one of the most common **interview patterns**.

---

## 🔗 Group By Multiple Columns

You can group by more than one column.

```python
df.groupby(["Department", "Age"])["Salary"].mean()
```

This creates groups based on the **combination** of `Department` and `Age`.

---

## 🔄 Reset the Index

By default, the grouped column becomes the index.

```python
df.groupby("Department")["Salary"].mean().reset_index()
```

This turns the result back into a regular DataFrame.

---

## 🆚 SQL vs Pandas

| SQL                     | Pandas                    |
|--------------------------|----------------------------|
| `GROUP BY department`    | `groupby("Department")`   |
| `AVG(salary)`             | `.mean()`                 |
| `SUM(salary)`             | `.sum()`                  |
| `COUNT(*)`                | `.size()`                 |
| `MAX(salary)`             | `.max()`                  |
| `MIN(salary)`             | `.min()`                  |

> If you already know SQL `GROUP BY`, you'll find this topic very familiar.

---

## 🎤 Interview Questions

1. What is the purpose of `groupby()`?
2. Does `groupby()` calculate anything by itself?
3. What's the difference between `count()` and `size()`?
4. When would you use `agg()`?
5. Why might you use `reset_index()` after `groupby()`?

---

📌 *Part of my Pandas learning series — Day 6.*
