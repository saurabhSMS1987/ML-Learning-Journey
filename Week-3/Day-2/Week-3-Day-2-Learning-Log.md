# Week 3: Day 2 Learning Log

**Status:** ✅ Complete  
**Consistency:** 16/21 days (76%)

---

## 📚 Source Material

**Courses:**
- Python for ML & DS Masterclass (Udemy)
- Python Data Analysis and Visualization Masterclass (Udemy)
- ML A-Z 2026: Section 6 - Simple Linear Regression (Udemy)

**Topics:** Advanced Matplotlib + Simple Linear Regression

---

## 🎯 Key Concepts Learned

### Matplotlib Advanced Techniques

**1. Subplots (Multiple Plots)**
```python
import matplotlib.pyplot as plt

# Create 2x2 grid of plots
fig, axes = plt.subplots(2, 2, figsize=(10, 8))

axes[0, 0].plot(x, y)  # Top-left
axes[0, 1].scatter(x, y)  # Top-right
axes[1, 0].bar(x, y)  # Bottom-left
axes[1, 1].hist(y)  # Bottom-right

plt.tight_layout()
plt.show()
```

**2. Legends, Colors & Styles**
```python
plt.plot(x, y1, label='Series 1', color='blue', linestyle='--')
plt.plot(x, y2, label='Series 2', color='red', linestyle='-')
plt.legend()  # Show legend
plt.style.use('seaborn')  # Change stylesheet
```

**3. Plot Anatomy & Customization**
```python
plt.figure(figsize=(12, 6))  # Width, Height
plt.xlabel('X Label')
plt.ylabel('Y Label')
plt.title('Plot Title')
plt.grid(True)
```

---

### Simple Linear Regression

**Concept:** Predict continuous values using a line
```
y = mx + b
```

**Ordinary Least Squares:** Minimizes distance between actual & predicted values

**Implementation in Scikit-learn:**
```python
from sklearn.linear_model import LinearRegression
from sklearn.model_selection import train_test_split

# Load & prepare data
X = dataset.iloc[:, :-1].values
y = dataset.iloc[:, -1].values

# Split data (80/20)
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=0)

# Create & train model
model = LinearRegression()
model.fit(X_train, y_train)

# Make predictions
y_pred = model.predict(X_test)

# Visualize results
plt.scatter(X_test, y_test, color='red', label='Real')
plt.plot(X_test, y_pred, color='blue', label='Predicted')
plt.legend()
plt.show()
```

---

## ✅ Accomplishments

✅ Mastered subplots (grids, layouts)  
✅ Customized legends, colors, line styles  
✅ Learned plot anatomy (labels, titles, grids)  
✅ Changed Matplotlib stylesheets  
✅ Set figure dimensions (figsize)  
✅ Built first Linear Regression model  
✅ Made predictions on test data  
✅ Visualized real vs predicted values  
✅ Practiced on Salary dataset  

---

## 🚧 Key Challenges

| Issue | Solution |
|-------|----------|
| Subplot indexing | Learned: axes[row, col] for 2D grids |
| tight_layout() | Fixed overlapping labels |
| Linestyle syntax | Practiced: '-', '--', '-.', ':' |
| Linear regression assumptions | Understood: linear relationship needed |

---

## 💡 Key Takeaways

1. **Visualizations tell the story** - See model performance visually
2. **Subplots compare models** - Put predictions side-by-side
3. **OLS minimizes error** - Draws best-fit line mathematically
4. **Linear regression baseline** - Always start here before complex models
5. **Scaling affects visualization** - Use consistent axis ranges
6. **Check predictions** - Plot real vs predicted always

---

## 🎯 Confidence Level: 8.5/10

Strong visualization skills, good understanding of linear regression fundamentals ✅

---

## 📚 Files Created

- ✅ Matplotlib_Day_1_Practice.ipynb (subplots, legends, styles)
- ✅ simple_linear_regression.ipynb (OLS implementation)
- ✅ Salary_Data.csv (used for regression)

---

**Status:** Ready for Day 3 ✅  
**Week 3 Progress:** 2/7 days ✅
