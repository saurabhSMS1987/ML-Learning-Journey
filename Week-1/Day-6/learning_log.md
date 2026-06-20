# Day 6: Learning Log - Week 1 File Handling & Advanced SQL

**Date:** [Day 6 of Week 1]  
**Duration:** Full Day (~8 hours)  
**Status:** ✅ COMPLETE  
**Consistency:** 6/7 Days

---

## 📚 Overview

Day 6 completed **Python fundamentals with file handling** and mastered **advanced SQL joins**. Learned critical file I/O, explored LEFT/RIGHT/FULL/CROSS/SELF joins, reviewed cost functions, and prepared for final capstone project.

---

## 🎯 Learning Objectives

- ✅ File handling (read, write, append)
- ✅ Error handling with files
- ✅ Advanced SQL JOINs (all 6 types)
- ✅ Cost function fundamentals
- ✅ ML framework understanding

---

## 📖 What I Learned

### 1. FILE HANDLING IN PYTHON

**Resource:** Krish Naik Bootcamp | 15 exercises

#### Core Operations
```python
# Read file
with open("file.txt", "r") as file:
    content = file.read()

# Write to file
with open("file.txt", "w") as file:
    file.write("Hello")

# Append to file
with open("file.txt", "a") as file:
    file.write("New line\n")

# Error handling
try:
    with open("file.txt", "r") as file:
        content = file.read()
except FileNotFoundError:
    print("File not found!")
```

#### Common Operations
```python
# Count lines
def count_lines(filename):
    with open(filename, "r") as file:
        return len(file.readlines())

# Find and replace
def find_replace(filename, old, new):
    with open(filename, "r") as file:
        content = file.read()
    with open(filename, "w") as file:
        file.write(content.replace(old, new))

# Copy file
def copy_file(src, dst):
    with open(src, "r") as f1:
        with open(dst, "w") as f2:
            f2.write(f1.read())
```

**Key Insight:** Always use `with` statement. It handles file closing automatically.

---

### 2. ADVANCED SQL JOINS

**Resource:** DataCamp | 14 lessons

#### All JOIN Types

```sql
-- INNER JOIN: Matching only
SELECT * FROM a INNER JOIN b ON a.id = b.id;

-- LEFT JOIN: All left + matching
SELECT * FROM a LEFT JOIN b ON a.id = b.id;

-- RIGHT JOIN: All right + matching
SELECT * FROM a RIGHT JOIN b ON a.id = b.id;

-- FULL JOIN: All from both
SELECT * FROM a FULL JOIN b ON a.id = b.id;

-- CROSS JOIN: All combinations (a.rows × b.rows)
SELECT * FROM a CROSS JOIN b;

-- SELF JOIN: Join table to itself
SELECT e.name, m.name as manager
FROM employees e
JOIN employees m ON e.manager_id = m.id;
```

#### Practical Example
```sql
-- Find customers who haven't ordered
SELECT customers.name
FROM customers
LEFT JOIN orders ON customers.id = orders.customer_id
WHERE orders.order_id IS NULL;
```

**Key Insight:** Choose JOIN type based on what data you need from each table.

---

### 3. COST FUNCTIONS

**Resource:** DeepLearning.AI | 5 videos

#### What is Cost?
```
Cost = How wrong our predictions are
Goal = Find model weights that minimize cost

Cost = (1/m) × Σ(predicted - actual)²
```

#### How Models Learn
1. Start with random weights
2. Calculate cost (how wrong)
3. Move weights to decrease cost
4. Repeat until cost stops improving

**Key Insight:** Training means finding weights that minimize the cost function.

---

### 4. ML FRAMEWORK REVIEW

**Resource:** Daniel Bourke

#### 6-Step ML Process
1. Problem Definition
2. Data Collection
3. Data Preparation
4. Exploratory Data Analysis (Day 7!)
5. Model Building
6. Evaluation & Deployment

**Week 1 Progress:**
- ✅ Days 1-3: Foundation skills
- ✅ Day 4: Real analysis (Step 4)
- ✅ Day 6: Understanding building blocks
- ⏳ Day 7: Complete EDA project (Step 4 mastery)

---

## 📊 Statistics

| Metric | Count |
|--------|-------|
| Lessons | 22 |
| Code Examples | 35+ |
| SQL JOINs | 6 types |
| Exercises | 15 |
| Hours | ~8 |

---

## 🎓 Key Takeaways

1. **File handling is essential** - All data science starts with loading data
2. **JOINs solve complex problems** - Combine data from multiple sources
3. **Cost functions drive learning** - Models minimize cost to improve
4. **Error handling matters** - Prevent data loss with try-except
5. **You're ready for the capstone** - All Week 1 skills complete

---

## ✨ Overall Assessment

**File Handling:** ⭐⭐⭐⭐⭐  
**SQL JOINs:** ⭐⭐⭐⭐⭐  
**ML Concepts:** ⭐⭐⭐⭐  
**Day 7 Readiness:** ⭐⭐⭐⭐⭐  

**Overall: 4.75/5**

---

## 🚀 Confidence Level

**File Handling:** 95%  
**SQL JOINs:** 90%  
**ML Framework:** 85%  
**Day 7 Ready:** 95%  

---

## 💪 Status

✅ 6/7 Days Complete (85.7%)  
✅ All Python Fundamentals Mastered  
✅ Advanced SQL Learned  
✅ ML Context Understood  
⏳ ONE DAY LEFT!

---

*Ready for the final capstone project tomorrow.* 🎯

**Day 6 Learning Log Complete**
