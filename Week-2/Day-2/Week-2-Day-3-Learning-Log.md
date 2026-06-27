# Week 2: Day 2 Learning Log

**Date:** [Insert Date] | **Duration:** 8 hours | **Status:** ✅ Complete  
**Consistency:** 9/14 days (64%)

---

## 📚 Source Material

**Courses:** Advanced SQL (DataCamp) | Pandas & Data Pipelines (Analyst Builder) | File Importing (DataCamp)  
**Topics:** Subqueries | Data pipelines | Multiple file formats

---

## 🎯 Key Concepts Learned

### Advanced SQL: Subqueries

**Subquery Basics:**
```sql
-- Subquery in WHERE clause
SELECT * FROM employees 
WHERE salary > (SELECT AVG(salary) FROM employees)

-- Subquery in SELECT clause
SELECT name, (SELECT COUNT(*) FROM orders 
             WHERE orders.emp_id = employees.id) as order_count
FROM employees

-- Subquery in FROM clause
SELECT * FROM (
  SELECT id, name, salary FROM employees WHERE salary > 50000
) AS high_earners
```

**Semi Join & Anti Join:**
- **Semi Join:** Returns rows that have a match in subquery (no duplicates)
- **Anti Join:** Returns rows that DON'T have a match in subquery
- Efficient for filtering without duplicates

**Multiple Conditions:**
```sql
WHERE (condition1 AND condition2)
OR (condition3 AND condition4)
```

---

### Data Pipelines Fundamentals

**What is a Data Pipeline?**
- Series of automated steps to process data
- Extract → Transform → Load (ETL)
- Moves data from source to destination
- Ensures data quality & consistency

**Pipeline Components:**
1. **Source:** Where data comes from
2. **Extraction:** Pull data
3. **Transformation:** Clean & process
4. **Loading:** Store in destination
5. **Monitoring:** Track pipeline health

**Why Pipelines Matter:**
- Automate repetitive tasks
- Ensure consistency
- Scale to large volumes
- Reduce manual errors

---

### File Importing: Multiple Formats

**CSV Files (Multiple Options):**
```python
import pandas as pd

# Basic CSV
df = pd.read_csv('file.csv')

# With custom delimiter
df = pd.read_csv('file.tsv', sep='\t')

# Skip rows
df = pd.read_csv('file.csv', skiprows=2)

# Handle errors
df = pd.read_csv('file.csv', on_bad_lines='skip')
```

**Excel Files:**
```python
# Read specific sheet
df = pd.read_excel('file.xlsx', sheet_name='Sheet1')

# Get all sheets
xls = pd.ExcelFile('file.xlsx')
print(xls.sheet_names)

# Multiple sheets
df1 = pd.read_excel('file.xlsx', sheet_name=0)
df2 = pd.read_excel('file.xlsx', sheet_name='Data')
```

**Other Formats:**
```python
# Pickle (Python objects)
import pickle
with open('file.pkl', 'rb') as f:
    data = pickle.load(f)

# SAS files
df = pd.read_sas('file.sas7bdat')

# Stata files
df = pd.read_stata('file.dta')

# HDF5 (large datasets)
import h5py
with h5py.File('file.h5', 'r') as f:
    data = f['dataset_name'][:]

# MATLAB
from scipy.io import loadmat
data = loadmat('file.mat')
```

**Exporting Data:**
```python
# CSV
df.to_csv('output.csv', index=False)

# Excel
df.to_excel('output.xlsx')

# Pickle
df.to_pickle('output.pkl')

# SQL database
from sqlalchemy import create_engine
engine = create_engine('sqlite:///database.db')
df.to_sql('table_name', engine, if_exists='replace')
```

---

## 💻 Code Example

```python
import pandas as pd
import pickle

# Read CSV with error handling
df = pd.read_csv('sales_data.csv', on_bad_lines='skip')

# Read Excel with multiple sheets
xls = pd.ExcelFile('inventory.xlsx')
products = pd.read_excel('inventory.xlsx', sheet_name='Products')

# Export to multiple formats
df.to_csv('output.csv', index=False)
df.to_pickle('output.pkl')
df.to_excel('output.xlsx')

# Filter & transform (pipeline step)
filtered = df[df['price'] > 100]
filtered['discount_price'] = filtered['price'] * 0.9
```

---

## ✅ Accomplishments

✅ Mastered SQL subqueries (WHERE, SELECT, FROM)  
✅ Learned semi joins & anti joins  
✅ Understood data pipeline concepts  
✅ Practiced 8+ file format importing  
✅ Learned export methods  
✅ Worked with Excel (multiple sheets)  
✅ Practiced pickle files  
✅ Completed all exercises  

---

## 🚧 Challenges & Solutions

| Challenge | Solution |
|-----------|----------|
| Subquery complexity | Started simple, built up; visualized data flow |
| File format variety | Practiced each format with real examples |
| Reading Excel sheets | Used .ExcelFile() to inspect before reading |
| Error handling | Used on_bad_lines='skip' for robust imports |

---

## 📊 Time Breakdown

- Advanced SQL (Subqueries): 2.5 hours
- Data Pipelines: 1.5 hours
- File Importing: 3.5 hours
- Practice & Code Examples: 0.5 hours

---

## 💡 Key Takeaways

1. **Subqueries:** Powerful for filtering with complex conditions
2. **Semi/Anti joins:** More efficient than regular joins for filtering
3. **Data pipelines:** Essential for production systems
4. **File formats:** Different sources need different approaches
5. **Exporting:** Always save processed data for downstream use
6. **Error handling:** Real data is messy; handle gracefully

---

## 🎯 Confidence Level: 8.5/10

- Strong understanding of subqueries
- Can import any common file format
- Understand pipeline concepts
- Ready to handle real-world data sources
- Comfortable with error handling

---

## 🚀 Tomorrow's Focus (Day 3)

- Relational databases in depth
- API integration
- JSON data handling
- Database queries through Python
- Multi-source data combining

---

## 📚 Resources

- DataCamp: Subqueries & File Importing courses
- Analyst Builder: Data Pipelines & Pandas
- Official pandas documentation
- SQLite tutorials

---

**Status:** Ready for Day 3 ✅

**Week 1:** 7/7 ✅ | **Week 2:** 2/7 ✅
