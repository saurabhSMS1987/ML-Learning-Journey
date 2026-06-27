# Week 2: Day 4 Learning Log

**Date:** [Insert Date] | **Duration:** 8 hours | **Status:** ✅ Complete  
**Consistency:** 11/14 days (79%)

---

## 📚 Source Material

**Courses:** Transforming DataFrames | Aggregating DataFrames | Slicing & Indexing | Data Merging (DataCamp)  
**Topics:** DataFrame operations | Groupby | Indexing | Merging | Advanced selections

---

## 🎯 Key Concepts Learned

### Transforming DataFrames

**Adding & Modifying Columns:**
```python
# Add new column
df['new_col'] = df['col1'] + df['col2']

# Apply function to column
df['doubled'] = df['value'].apply(lambda x: x * 2)

# Create from conditions
df['category'] = df['price'].apply(
    lambda x: 'Expensive' if x > 100 else 'Cheap'
)

# Rename columns
df.rename(columns={'old': 'new'}, inplace=True)

# Drop columns
df.drop(['col1', 'col2'], axis=1, inplace=True)
```

**Sorting:**
```python
# Sort by single column
df.sort_values('score', ascending=False)

# Sort by multiple columns
df.sort_values(['age', 'salary'], ascending=[True, False])

# Sort index
df.sort_index()
```

---

### Aggregating Data with GroupBy

**Basic Groupby:**
```python
# Group and aggregate
df.groupby('category')['sales'].sum()

# Multiple aggregations
df.groupby('category')['sales'].agg(['sum', 'mean', 'count'])

# Group by multiple columns
df.groupby(['category', 'region'])['sales'].sum()

# Custom aggregation
df.groupby('category').agg({
    'sales': 'sum',
    'profit': 'mean',
    'quantity': 'count'
})
```

**Pivot Tables:**
```python
# Create pivot table
pivot = df.pivot_table(
    values='sales',
    index='region',
    columns='product',
    aggfunc='sum'
)

# Fill missing values
pivot.fillna(0)
```

---

### Indexing & Slicing

**loc (Label-based):**
```python
# Get row by label
df.loc[0]

# Get column
df.loc[:, 'name']

# Get cell
df.loc[0, 'name']

# Boolean indexing
df.loc[df['age'] > 25]

# Multiple conditions
df.loc[(df['age'] > 25) & (df['salary'] > 50000)]
```

**iloc (Position-based):**
```python
# Get row by position
df.iloc[0]

# Get first 5 rows
df.iloc[:5]

# Get specific cell
df.iloc[0, 2]

# Get range
df.iloc[0:10, 0:3]
```

**Setting Index:**
```python
# Set index
df.set_index('id', inplace=True)

# Reset index
df.reset_index(inplace=True)

# Multi-level index
df.set_index(['year', 'month'])
```

---

### Merging & Joining

**Merge (SQL-like):**
```python
# Inner join (default)
merged = pd.merge(df1, df2, on='id')

# Left join
merged = pd.merge(df1, df2, on='id', how='left')

# Right join
merged = pd.merge(df1, df2, on='id', how='right')

# Outer join
merged = pd.merge(df1, df2, on='id', how='outer')

# Multiple keys
merged = pd.merge(df1, df2, on=['id', 'date'])
```

**Concatenate:**
```python
# Vertical (stack rows)
result = pd.concat([df1, df2], ignore_index=True)

# Horizontal (side by side)
result = pd.concat([df1, df2], axis=1)

# With keys
result = pd.concat([df1, df2], keys=['first', 'second'])
```

---

## 💻 Code Example

```python
import pandas as pd

# Create sample data
sales = pd.DataFrame({
    'date': pd.date_range('2024-01-01', periods=6),
    'product': ['A', 'B', 'A', 'C', 'B', 'A'],
    'amount': [100, 150, 120, 200, 180, 140]
})

# Group and aggregate
daily_sales = sales.groupby('product')['amount'].agg(['sum', 'mean', 'count'])

# Create pivot table
pivot = sales.pivot_table(
    values='amount',
    index='date',
    columns='product',
    aggfunc='sum'
)

# Sort by amount
top_sales = sales.sort_values('amount', ascending=False)

# Filter
high_value = sales[sales['amount'] > 140]

print(daily_sales)
print(pivot)
print(top_sales)
```

---

## ✅ Accomplishments

✅ Mastered DataFrame transformations  
✅ Advanced groupby operations  
✅ Pivot table creation  
✅ loc & iloc indexing  
✅ Boolean indexing patterns  
✅ All join types (inner, left, right, outer)  
✅ Concatenation methods  
✅ Complex filtering  

---

## 🚧 Challenges & Solutions

| Challenge | Solution |
|-----------|----------|
| loc vs iloc confusion | Created mental model: loc=labels, iloc=positions |
| Groupby complexity | Started simple, added aggregations gradually |
| Join logic | Drew diagrams showing which rows remain |
| Multi-column operations | Practiced with real data examples |

---

## 📊 Time Breakdown

- DataFrame Transformations: 1.5 hours
- Groupby & Aggregations: 2 hours
- Indexing & Slicing: 2 hours
- Merging & Joining: 2 hours
- Practice: 0.5 hours

---

## 💡 Key Takeaways

1. **Groupby:** Most powerful aggregation tool
2. **Pivot tables:** Quick way to reshape data
3. **loc/iloc:** Essential for data selection
4. **Merge types:** Different joins for different needs
5. **Apply:** Flexible for custom transformations
6. **Index matters:** Proper indexing makes operations faster

---

## 🎯 Confidence Level: 9/10

- Excellent understanding of groupby
- Comfortable with all indexing methods
- Confident in merge operations
- Can transform data efficiently
- Ready for ML data prep

---

## 🚀 Tomorrow's Focus (Day 5)

- First ML models (Linear Regression)
- Scikit-learn introduction
- Model training & prediction
- Real dataset application
- Model persistence

---

## 📚 Resources

- DataCamp: Pandas manipulation courses
- Official pandas documentation
- Real data examples

---

**Status:** Ready for Day 5 & ML! ✅

**Week 1:** 7/7 ✅ | **Week 2:** 4/7 ✅
