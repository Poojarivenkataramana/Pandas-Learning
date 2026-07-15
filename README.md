# 🐼 Pandas Day 1 – Introduction to Pandas

## 📖 What is Pandas?

Pandas is a powerful Python library used for data manipulation and data analysis. It helps us work with structured data such as CSV files, Excel files, SQL tables, and more.

## 🎯 Why Do We Use Pandas?

- Read data from CSV, Excel, JSON, SQL, etc.
- Clean and preprocess data.
- Analyze and summarize data.
- Handle missing values.
- Filter and sort records.
- Prepare data for Machine Learning and Data Visualization.

---

# 📊 What is a DataFrame?

A **DataFrame** is a two-dimensional table in Pandas consisting of rows and columns, similar to an Excel spreadsheet or SQL table.

### Example

```python
import pandas as pd

data = {
    "Name": ["Ram", "Sita", "Rahul"],
    "Age": [22, 21, 24],
    "City": ["Hyderabad", "Bangalore", "Chennai"]
}

df = pd.DataFrame(data)

print(df)
```

### Output

```
    Name  Age        City
0    Ram   22   Hyderabad
1   Sita   21   Bangalore
2  Rahul   24     Chennai
```

---

# 📦 Install Pandas

```python
pip install pandas
```

---

# 📥 Import Pandas

```python
import pandas as pd
```

> **Note:** `pd` is the standard alias used for the Pandas library.

---

# 📂 Reading a CSV File

```python
import pandas as pd

df = pd.read_csv("big_employee_data.csv")
```

This reads the CSV file and stores it in a Pandas **DataFrame**.

---

# ✅ Topics Covered

- Installing Pandas
- Importing Pandas
- Understanding DataFrame
- Reading CSV Files
- Displaying DataFrames
- `head()`
- `tail()`
- `info()`
- `describe()`
- `shape`
- `columns`

---

# 🛠️ Technologies Used

- Python
- Pandas
- Jupyter Notebook

---

## 📚 Day 1 Summary

In this notebook, I learned the basics of Pandas, including how to install the library, import it, create a DataFrame, read CSV files, and explore datasets using built-in functions.
