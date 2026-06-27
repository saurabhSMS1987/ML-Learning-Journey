# Week 2: Day 1 Learning Log

**Date:** [Insert Date] | **Duration:** 8 hours | **Status:** ✅ Complete  
**Consistency:** 8/14 days (57%)

---

## 📚 Source Material

**Course:** Python for Data Analysis: Pandas & NumPy (Coursera)  
**Topics:** 12 sections covering NumPy arrays & Pandas DataFrames

---

## 🎯 Key Concepts Learned

### NumPy Fundamentals
- **Array creation:** np.array(), zeros(), ones(), arange(), linspace()
- **Attributes:** .shape, .dtype, .ndim, .size
- **Statistical functions:** mean(), std(), sum(), min(), max(), cumsum()
- **Operations:** reshape(), flatten(), sort(), unique()

### Math Operations
- Element-wise operations: +, -, *, /, **
- Broadcasting: operations on different-shaped arrays
- Scalar operations apply to all elements

### Indexing & Slicing
```python
arr = np.array([10, 20, 30, 40, 50])
arr[0]          # 10
arr[-1]         # 50
arr[1:3]        # [20, 30]
arr[::2]        # [10, 30, 50]
arr[arr > 30]   # [40, 50] - boolean indexing
```

### Pandas Fundamentals
- **Series:** 1D labeled array (like a column)
- **DataFrame:** 2D table (like spreadsheet)
- Creation from lists, dicts, or arrays
- Handles mixed data types & missing values

### Pandas Operations
```python
df.head()           # First 5 rows
df.info()           # Column info
df.describe()       # Statistics
df['Column']        # Access column
df[['Col1', 'Col2']] # Multiple columns
df.iloc[0]          # First row by position
df.loc[0, 'Name']   # Cell by label
```

### Sorting & Concatenation
```python
df.sort_values('Score', ascending=False)  # Sort by column
pd.concat([df1, df2])  # Combine vertically
pd.merge(df1, df2, on='key')  # Join like SQL
```

---

## 💻 Code Example

```python
import numpy as np
import pandas as pd

# NumPy - Calculate statistics
temps = np.array([20, 25, 22, 28, 24, 30])
print(f"Avg: {temps.mean()}, Hot days (>26): {temps[temps > 26]}")

# Pandas - Create & manipulate DataFrame
students = pd.DataFrame({
    'Name': ['Alice', 'Bob', 'Charlie'],
    'Math': [85, 92, 78],
    'English': [90, 88, 95]
})
students['Average'] = students[['Math', 'English']].mean(axis=1)
top_students = students.sort_values('Average', ascending=False)
```

---

## ✅ Accomplishments

✅ Mastered NumPy array creation & operations  
✅ Learned indexing (1D, 2D, slicing, boolean)  
✅ Built Pandas Series & DataFrames  
✅ Performed data manipulation operations  
✅ Practiced sorting & concatenation  
✅ Wrote working code examples  
✅ Completed all course exercises  

---

## 🚧 Challenges & Solutions

| Challenge | Solution |
|-----------|----------|
| Broadcasting concept | Visualized dimension alignment with examples |
| loc vs iloc | Created mental model: iloc = integer position |
| When to concatenate vs merge | concat = stacking, merge = SQL joins |

---

## 📊 Time Breakdown

- NumPy Theory & Practice: 3.5 hours
- Pandas Theory & Practice: 4 hours
- Code Examples & Testing: 0.5 hours

---

## 💡 Key Takeaways

1. **NumPy:** Vectorized operations = speed & efficiency
2. **Pandas:** Works on top of NumPy, handles tabular data
3. **Together:** Foundation for all data science work
4. **Boolean indexing:** More powerful than filtering with loops
5. **DataFrames:** Think of them as Excel sheets in Python

---

## 🎯 Confidence Level: 8/10

- Solid understanding of fundamentals
- Can manipulate arrays & DataFrames confidently
- Ready to apply to real data

---

## 🚀 Tomorrow's Focus (Day 2)

- Advanced SQL (Subqueries, joins)
- File importing (CSV, Excel, JSON)
- NumPy advanced operations
- More Pandas practice

---

## 📚 Resources

- Coursera: Python for Data Analysis: Pandas & NumPy
- Official NumPy & Pandas documentation
- Notebook: Python_101_-_Python_Libraries_for_Data_Analysis_-_Numpy_and_Pandas.ipynb

---

**Status:** Ready for Day 2 ✅

**Week 1:** 7/7 ✅ | **Week 2:** 1/7 ✅
