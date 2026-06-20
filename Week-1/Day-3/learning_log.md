# Day 3: Learning Log - Week 1 Data Manipulation & Visualization

**Date:** [Day 3 of Week 1]  
**Duration:** Full Day (~8 hours)  
**Status:** ✅ COMPLETE  
**Consistency:** 3/7 Days

---

## 📚 Overview

Day 3 focused on **practical data manipulation and visualization skills**. Mastered Matplotlib for creating professional charts, learned Pandas DataFrames for organizing data, and advanced SQL aggregation and grouping techniques. Applied all Python fundamentals from previous days to real data analysis.

---

## 🎯 Learning Objectives for Today

- [ ] Master Matplotlib visualization library
- [ ] Create multiple chart types professionally
- [ ] Understand and use Pandas DataFrames
- [ ] Dictionary manipulation for data storage
- [ ] SQL GROUP BY and aggregation functions
- [ ] SQL sorting and ordering techniques
- [ ] Combine multiple data techniques

**Status:** ✅ All objectives completed + notebooks saved

---

## 📖 What I Learned Today

### 1. MATPLOTLIB - PROFESSIONAL VISUALIZATION (DataCamp)

**Resource:** DataCamp - Matplotlib for Data Visualization  
**Lessons:** 19 lessons completed  
**Output:** `Matplotlib_Code_Practice.ipynb` saved

#### What is Matplotlib?

Python's most popular visualization library. Creates publication-quality charts and graphs.

#### Basic Plot Structure

```python
import matplotlib.pyplot as plt

# Basic line plot
plt.plot([1, 2, 3, 4], [1, 4, 9, 16])
plt.title("Simple Line Plot")
plt.xlabel("X Axis")
plt.ylabel("Y Axis")
plt.show()

# Basic scatter plot
plt.scatter([1, 2, 3, 4], [1, 4, 9, 16])
plt.title("Scatter Plot")
plt.show()

# Basic histogram
plt.hist([1, 1, 2, 2, 2, 3, 4, 4, 4, 4])
plt.title("Distribution")
plt.show()
```

#### Line Plots - Showing Trends

```python
# Simple line plot
months = [1, 2, 3, 4, 5, 6]
sales = [100, 150, 120, 180, 200, 220]

plt.plot(months, sales)
plt.title("Monthly Sales Trend")
plt.xlabel("Month")
plt.ylabel("Sales ($)")
plt.grid(True)
plt.show()

# Multiple lines
plt.plot(months, sales, label="Sales")
plt.plot(months, [80, 100, 90, 140, 160, 180], label="Target")
plt.legend()
plt.title("Sales vs Target")
plt.show()

# Customizing lines
plt.plot(months, sales, 
         color='red', 
         linewidth=2, 
         linestyle='--', 
         marker='o',
         markersize=8)
plt.show()
```

#### Scatter Plots - Showing Relationships

```python
# Basic scatter
ages = [25, 30, 35, 40, 45]
salaries = [30000, 35000, 40000, 50000, 60000]

plt.scatter(ages, salaries)
plt.title("Age vs Salary")
plt.xlabel("Age (years)")
plt.ylabel("Salary ($)")
plt.show()

# Scatter with customization
plt.scatter(ages, salaries, 
           s=200,  # Size of points
           alpha=0.6,  # Transparency
           c='red',  # Color
           edgecolors='black',  # Border color
           marker='o')  # Marker style
plt.show()
```

#### Histograms - Showing Distributions

```python
# Distribution of test scores
scores = [65, 70, 75, 75, 80, 80, 80, 85, 90, 95]

plt.hist(scores, bins=5, color='skyblue', edgecolor='black')
plt.title("Test Score Distribution")
plt.xlabel("Score")
plt.ylabel("Frequency")
plt.show()

# Multiple histograms
plt.hist(scores, bins=5, alpha=0.5, label="Class A", color='blue')
plt.hist([70, 75, 80, 85, 90], bins=5, alpha=0.5, label="Class B", color='red')
plt.legend()
plt.show()
```

#### Bar Charts - Comparing Categories

```python
# Simple bar chart
categories = ['Q1', 'Q2', 'Q3', 'Q4']
values = [100, 150, 120, 180]

plt.bar(categories, values, color='steelblue')
plt.title("Quarterly Revenue")
plt.ylabel("Revenue ($)")
plt.show()

# Horizontal bar chart
plt.barh(categories, values, color='steelblue')
plt.title("Quarterly Revenue")
plt.xlabel("Revenue ($)")
plt.show()

# Grouped bar chart
categories = ['A', 'B', 'C']
x = [0, 1, 2]
values1 = [10, 20, 15]
values2 = [15, 25, 20]

plt.bar([i - 0.2 for i in x], values1, width=0.4, label='Product 1')
plt.bar([i + 0.2 for i in x], values2, width=0.4, label='Product 2')
plt.xticks(x, categories)
plt.legend()
plt.show()
```

#### Pie Charts - Showing Composition

```python
# Simple pie chart
sizes = [30, 25, 20, 25]
labels = ['A', 'B', 'C', 'D']
colors = ['red', 'blue', 'green', 'yellow']

plt.pie(sizes, labels=labels, colors=colors, autopct='%1.1f%%')
plt.title("Distribution")
plt.show()

# Exploded pie chart
explode = (0.1, 0, 0, 0)  # Explode first slice
plt.pie(sizes, labels=labels, explode=explode, autopct='%1.1f%%')
plt.show()
```

#### Customization & Styling

```python
# Figure size
plt.figure(figsize=(10, 6))  # Width=10, Height=6

# Multiple subplots
fig, ((ax1, ax2), (ax3, ax4)) = plt.subplots(2, 2, figsize=(12, 10))

ax1.plot([1, 2, 3], [1, 4, 9])
ax1.set_title("Plot 1")

ax2.scatter([1, 2, 3], [1, 4, 9])
ax2.set_title("Plot 2")

ax3.bar(['A', 'B', 'C'], [1, 4, 9])
ax3.set_title("Plot 3")

ax4.hist([1, 2, 2, 3, 3, 3])
ax4.set_title("Plot 4")

plt.tight_layout()
plt.show()

# Saving figures
plt.savefig('my_plot.png', dpi=300, bbox_inches='tight')
```

**Key Insight:** Good visualizations tell stories. Choose the right chart type for your data.

---

### 2. PANDAS - DATA MANIPULATION WITH DATAFRAMES (DataCamp)

**Resource:** DataCamp - Pandas for Data Analysis  
**Lessons:** 19 lessons completed (part of Dictionaries + Pandas course)  
**Output:** `Dictionaries___Pandas.ipynb` saved

#### What is Pandas?

Library for working with structured data (tables). Built on NumPy but more user-friendly.

#### Creating DataFrames

```python
import pandas as pd
import numpy as np

# From dictionary
data = {
    'name': ['Saurabh', 'Raj', 'Priya'],
    'age': [25, 30, 28],
    'salary': [50000, 60000, 55000]
}
df = pd.DataFrame(data)

# From list
data_list = [
    ['Saurabh', 25],
    ['Raj', 30],
    ['Priya', 28]
]
df = pd.DataFrame(data_list, columns=['name', 'age'])

# From NumPy array
df = pd.DataFrame(np.random.rand(5, 3), columns=['A', 'B', 'C'])

# Display
print(df)
print(df.head())  # First 5 rows
print(df.tail())  # Last 5 rows
print(df.info())  # Information about DataFrame
print(df.describe())  # Statistical summary
```

#### Accessing Data

```python
df = pd.DataFrame({
    'name': ['Saurabh', 'Raj', 'Priya'],
    'age': [25, 30, 28],
    'city': ['Delhi', 'Mumbai', 'Bangalore']
})

# Column access
df['name']  # Series (single column)
df[['name', 'age']]  # DataFrame (multiple columns)

# Row access
df.loc[0]  # By label (first row)
df.iloc[0]  # By position
df.loc[df['age'] > 25]  # Conditional selection

# Element access
df.loc[0, 'name']  # Specific cell
df.iloc[0, 0]  # By position
```

#### Data Filtering

```python
# Filter by condition
df[df['age'] > 25]  # Get rows where age > 25
df[df['city'] == 'Delhi']  # Get rows where city is Delhi
df[(df['age'] > 25) & (df['city'] == 'Delhi')]  # Multiple conditions
df[df['name'].str.startswith('S')]  # String filtering

# Filter and select columns
df[df['age'] > 25][['name', 'age']]  # Filter then select columns
```

#### Grouping and Aggregation

```python
df = pd.DataFrame({
    'category': ['A', 'B', 'A', 'B', 'A'],
    'value': [10, 20, 15, 25, 12]
})

# Group by
grouped = df.groupby('category')['value'].sum()
# Output:
# category
# A    37
# B    45

# Multiple aggregations
df.groupby('category')['value'].agg(['sum', 'mean', 'count'])

# Multiple columns
df.groupby(['category'])['value'].describe()
```

#### Data Manipulation

```python
# Add new column
df['total_salary'] = df['salary'] * 12

# Modify column
df['age'] = df['age'] + 1

# Drop column
df = df.drop('age', axis=1)

# Rename column
df = df.rename(columns={'salary': 'monthly_salary'})

# Sort
df.sort_values('age')  # Ascending
df.sort_values('age', ascending=False)  # Descending
df.sort_values(['age', 'salary'])  # Multiple columns

# Handle missing values
df.fillna(0)  # Fill with 0
df.dropna()  # Remove rows with NaN
```

#### Statistical Operations

```python
df['salary'].mean()  # Average
df['salary'].median()  # Median
df['salary'].std()  # Standard deviation
df['salary'].min()  # Minimum
df['salary'].max()  # Maximum
df['salary'].sum()  # Total

df.describe()  # All statistics at once

df.corr()  # Correlation between columns
```

**Key Insight:** Pandas is the workhorse of data analysis. Master DataFrames and you unlock data manipulation.

---

### 3. DICTIONARIES - DATA STRUCTURE REVIEW (DataCamp)

**Resource:** DataCamp - Python Data Structures  
**Lessons:** Part of 19-lesson course  
**Practice:** Integrated with Pandas learning

#### Dictionary Fundamentals Review

```python
# Creating dictionaries
student = {'name': 'Saurabh', 'age': 25, 'gpa': 3.8}

# Accessing values
student['name']  # 'Saurabh'
student.get('age')  # 25
student.get('city', 'Unknown')  # Default if missing

# Adding/modifying
student['city'] = 'Delhi'
student['age'] = 26

# Removing
del student['gpa']
student.pop('gpa')  # Remove and return value

# Checking keys
'name' in student  # True
'gpa' in student  # False

# Getting all keys, values, items
student.keys()  # dict_keys(['name', 'age', 'city'])
student.values()  # dict_values(['Saurabh', 26, 'Delhi'])
student.items()  # dict_items([('name', 'Saurabh'), ...])
```

#### Nested Dictionaries

```python
# Storing complex data
company = {
    'name': 'TechCorp',
    'employees': {
        'emp1': {'name': 'Saurabh', 'salary': 50000},
        'emp2': {'name': 'Raj', 'salary': 60000}
    },
    'locations': ['Delhi', 'Mumbai', 'Bangalore']
}

# Accessing nested data
company['employees']['emp1']['name']  # 'Saurabh'
company['locations'][0]  # 'Delhi'
```

#### Dictionary Iteration

```python
student = {'name': 'Saurabh', 'age': 25, 'city': 'Delhi'}

# Iterate keys
for key in student:
    print(key)

# Iterate values
for value in student.values():
    print(value)

# Iterate both
for key, value in student.items():
    print(f"{key}: {value}")

# With list comprehension
[f"{k}: {v}" for k, v in student.items()]
```

**Key Insight:** Dictionaries are fundamental for organizing and retrieving data efficiently.

---

### 4. SQL AGGREGATION - GROUP BY & FUNCTIONS (DataCamp)

**Resource:** DataCamp - SQL for Data Analysis  
**Lessons:** 10 lessons on aggregation  

#### Aggregation Functions

```sql
-- COUNT: Number of rows
SELECT COUNT(*) FROM students;  -- Total rows
SELECT COUNT(age) FROM students;  -- Non-null ages
SELECT COUNT(DISTINCT country) FROM students;  -- Unique countries

-- SUM: Total
SELECT SUM(salary) FROM employees;
SELECT SUM(sales) FROM orders WHERE year = 2023;

-- AVG: Average
SELECT AVG(salary) FROM employees;
SELECT AVG(score) FROM students WHERE subject = 'Math';

-- MIN/MAX: Minimum and Maximum
SELECT MIN(salary), MAX(salary) FROM employees;
SELECT MIN(date), MAX(date) FROM transactions;
```

#### GROUP BY - Grouping Data

```sql
-- Group by single column
SELECT country, COUNT(*) 
FROM students 
GROUP BY country;

-- Group by multiple columns
SELECT country, age, COUNT(*) 
FROM students 
GROUP BY country, age;

-- Group with aggregations
SELECT 
    product_category,
    COUNT(*) as total_items,
    SUM(sales) as total_sales,
    AVG(price) as avg_price
FROM products
GROUP BY product_category;
```

#### HAVING - Filter Groups

```sql
-- Filter groups after aggregation
SELECT 
    country, 
    COUNT(*) as student_count
FROM students
GROUP BY country
HAVING COUNT(*) > 10;

-- Multiple conditions
SELECT 
    category,
    AVG(price) as avg_price
FROM products
GROUP BY category
HAVING AVG(price) > 100 AND COUNT(*) > 5;
```

#### Real-World Examples

```sql
-- Sales by region
SELECT 
    region,
    SUM(sales) as total_sales,
    COUNT(*) as num_transactions,
    AVG(sales) as avg_transaction
FROM sales_data
GROUP BY region
ORDER BY total_sales DESC;

-- Customer spending analysis
SELECT 
    customer_id,
    COUNT(*) as purchases,
    SUM(amount) as total_spent,
    AVG(amount) as avg_purchase,
    MIN(date) as first_purchase,
    MAX(date) as last_purchase
FROM orders
GROUP BY customer_id
HAVING SUM(amount) > 1000
ORDER BY total_spent DESC;
```

**Key Insight:** GROUP BY + aggregation functions answer business questions: totals, averages, counts by category.

---

### 5. SQL SORTING & ORDERING - ORDER BY (DataCamp)

**Resource:** DataCamp - SQL for Data Analysis  
**Lessons:** 13 lessons on sorting and ordering

#### ORDER BY Fundamentals

```sql
-- Ascending order (default)
SELECT * FROM students ORDER BY age;

-- Descending order
SELECT * FROM students ORDER BY salary DESC;

-- Multiple columns
SELECT * FROM employees 
ORDER BY department, salary DESC;

-- By column number
SELECT name, age, salary FROM employees
ORDER BY 2 DESC;  -- Order by age (2nd column)

-- Order by expression
SELECT 
    name, 
    salary,
    salary * 12 as annual_salary
FROM employees
ORDER BY salary * 12 DESC;
```

#### Combining with Other Clauses

```sql
-- With WHERE
SELECT name, score 
FROM students 
WHERE score > 70
ORDER BY score DESC;

-- With WHERE and LIMIT
SELECT name, salary
FROM employees
WHERE department = 'Sales'
ORDER BY salary DESC
LIMIT 10;  -- Top 10 sales employees by salary

-- With GROUP BY
SELECT 
    country,
    COUNT(*) as count
FROM students
GROUP BY country
ORDER BY count DESC;

-- With HAVING
SELECT 
    category,
    AVG(price) as avg_price
FROM products
GROUP BY category
HAVING COUNT(*) > 5
ORDER BY avg_price DESC;
```

#### LIMIT - Restricting Results

```sql
-- Top 5 records
SELECT * FROM students ORDER BY score DESC LIMIT 5;

-- Skip first 10, get next 10 (pagination)
SELECT * FROM products ORDER BY id LIMIT 10 OFFSET 10;

-- Top 3 by category
SELECT * FROM products 
WHERE category = 'Electronics'
ORDER BY price DESC
LIMIT 3;
```

#### Real-World Sorting Scenarios

```sql
-- Highest paid employees
SELECT name, salary 
FROM employees 
ORDER BY salary DESC 
LIMIT 10;

-- Most recent transactions
SELECT * 
FROM transactions 
ORDER BY date DESC 
LIMIT 20;

-- Best performing products
SELECT 
    product_name,
    SUM(quantity) as units_sold
FROM sales
GROUP BY product_name
ORDER BY units_sold DESC
LIMIT 5;
```

**Key Insight:** Sorting and ordering transforms raw data into actionable insights. Order by relevance, date, or value.

---

## 💻 Hands-On Practice

### Notebooks Created:

**1. Matplotlib Code Practice**
- Created 8+ different chart types
- Customized colors, labels, sizes
- Built multi-subplot layouts
- Saved publication-quality figures
- File: `Matplotlib_Code_Practice.ipynb`

**2. Dictionaries & Pandas**
- Worked with nested dictionaries
- Created multiple DataFrames
- Performed filtering operations
- Applied grouping and aggregation
- File: `Dictionaries___Pandas.ipynb`

### SQL Queries Executed:

```sql
-- Aggregation examples
SELECT COUNT(*) FROM students;
SELECT AVG(age) FROM students GROUP BY country;

-- Complex grouping
SELECT 
    category,
    COUNT(*) as items,
    SUM(price) as total
FROM products
GROUP BY category
HAVING COUNT(*) > 5
ORDER BY total DESC;

-- With filtering
SELECT 
    region,
    SUM(sales) as sales
FROM transactions
WHERE year = 2023
GROUP BY region
ORDER BY sales DESC;
```

---

## 📊 Statistics

| Metric | Count |
|--------|-------|
| **Lessons Completed** | 42 |
| **Topics Covered** | 5 |
| **Chart Types Learned** | 6 |
| **Code Examples** | 60+ |
| **SQL Queries** | 20+ |
| **Notebooks Saved** | 2 |
| **Hours Invested** | ~8 |

---

## 🎓 Key Takeaways

### 1. Matplotlib is Powerful
Good visualizations make data understandable. Choose the right chart type for your story.

### 2. DataFrames Simplify Data Work
Pandas DataFrames make data manipulation intuitive. Much easier than raw Python.

### 3. Dictionaries Organize Data
Before DataFrames, dictionaries store structured data. Good foundation for DataFrames.

### 4. GROUP BY Answers Business Questions
Aggregation + grouping extracts insights: totals, averages, counts by category.

### 5. Sorting Reveals Patterns
ORDER BY prioritizes information. Show most important results first.

### 6. Combining Techniques is Powerful
WHERE + GROUP BY + HAVING + ORDER BY = complete analysis.

### 7. Real Data is Messy
Practice with real datasets reveals what doesn't work in textbooks.

### 8. Documentation Matters
Commented code with clear variable names helps future you.

---

## 🤔 Reflections

**What Went Well:**
- ✅ Completed all 42 lessons
- ✅ Saved both practice notebooks
- ✅ Code examples all worked
- ✅ Topics connected naturally
- ✅ Good balance of theory and practice
- ✅ Created publication-quality visualizations

**Challenges Encountered:**
- Matplotlib has many customization options (overwhelming)
- Pandas syntax initially unfamiliar (coming from lists/dicts)
- SQL GROUP BY logic took time to internalize
- Choosing right chart type requires domain knowledge

**How I Overcame Them:**
- Focused on most common chart types first
- Practiced multiple DataFrame operations
- Worked through GROUP BY step by step
- Consulted examples for each chart type
- Revisited difficult concepts immediately

---

## 📋 Progress Toward Week 1 Goals

### Core Python Foundations:
- Functions: 🟢 (Using in code)
- Loops: 🟢 (Implicit in Pandas operations)
- Dictionaries: 🟢 (Foundation for DataFrames)
- File Handling: ⏳ (Coming Day 6)
- Lists: 🟢 (Foundation for arrays/DataFrames)

### Data Skills:
- SQL Basics: 🟢 (Strong: SELECT, WHERE, GROUP BY, ORDER BY)
- Data Visualization: 🟢 (Matplotlib mastered)
- Data Manipulation: 🟢 (Pandas proficient)
- NumPy: 🟡 (From Day 2, reinforced with Pandas)

---

## 🔗 Resources Used Today

| Resource | Platform | Lessons |
|----------|----------|---------|
| Matplotlib | DataCamp | 19 |
| Pandas | DataCamp | 19 |
| SQL Aggregation | DataCamp | 10 |
| SQL Sorting | DataCamp | 13 |

---

## 🎯 Tomorrow's Goals (Day 4)

### Day 4 Focus: Real Project + Control Flow

**Planned Learning:**
- Complete Control Flow mastery
- Logic and filtering techniques
- Build real SQL analysis project
- Apply all Week 1 skills to date

**Planned Projects:**
- Mental Health SQL analysis (real data)
- Control flow exercises
- Data-driven insights generation

**Time Allocation:**
- Control flow & logic: 2 hours
- SQL project building: 3 hours
- Problem-solving: 2 hours
- Documentation: 1 hour

---

## 📝 Notes for Future Reference

### Most Used Commands:

**Matplotlib:**
```python
plt.plot(x, y)
plt.bar(categories, values)
plt.pie(sizes, labels)
plt.scatter(x, y)
plt.hist(data)
```

**Pandas:**
```python
df[df['column'] > value]  # Filtering
df.groupby('category').sum()  # Grouping
df.sort_values('column')  # Sorting
df['new_col'] = df['col1'] + df['col2']  # New column
```

**SQL:**
```sql
SELECT columns FROM table WHERE condition GROUP BY column ORDER BY column;
SELECT AVG(column), SUM(column) FROM table GROUP BY category;
```

---

## ✨ Overall Day 3 Assessment

**Learning Quality:** ⭐⭐⭐⭐⭐ (5/5)  
**Practical Application:** ⭐⭐⭐⭐⭐ (5/5)  
**Code Quality:** ⭐⭐⭐⭐ (4/5)  
**Notebook Completeness:** ⭐⭐⭐⭐⭐ (5/5)  
**Concepts Mastered:** ⭐⭐⭐⭐⭐ (5/5)

**Overall Day 3 Rating: 4.8/5** 🌟

---

## 🚀 Confidence Level Moving Forward

**Matplotlib:** 90% confident  
**Pandas DataFrames:** 85% confident  
**SQL Aggregation:** 85% confident  
**SQL Sorting:** 90% confident  
**Data Visualization:** 85% confident  
**Overall:** 87% confident for Day 4

---

## 💪 Motivation & Mindset

**Momentum Building:**
- ✅ 3 consecutive days done
- ✅ 2 practice notebooks saved
- ✅ 121+ lessons completed
- ✅ Major visualization/data manipulation skills acquired

**Energy Level:**
- Peak energy - skills clicking together
- Seeing how concepts connect
- Excited about applying skills to real project tomorrow
- Confidence growing significantly

**Realization:**
> "I'm not just learning concepts. I'm building a complete data analysis toolkit."

---

## 🎯 Next Day Preview

Day 4 will be **project day** - first real data analysis project:
- International student mental health analysis
- Real SQL queries on real data
- Complete analysis workflow
- Professional documentation
- **First portfolio-ready project!**

**Ready for Day 4!** 🚀

---

**Status: Day 3 Complete ✅**

**Progress: 3/7 Days of Week 1 (42.9%)**

**Consistency: 4 More Days to Complete Week 1**

**Momentum: STRONG! Keep it going!**

---

*"Three days down, four to go. You're halfway through Week 1. Momentum is your best friend now."*

**Day 3 Learning Log Complete**

*Next: Day 4 Learning Log (Real Project)*
