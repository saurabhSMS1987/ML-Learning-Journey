# Week 2: Day 5 Learning Log

**Date:** [Insert Date] | **Duration:** 8 hours | **Status:** ✅ Complete  
**Consistency:** 12/14 days (86%)

---

## 📚 Source Material

**Courses:** Linear Regression Theory | Scikit-learn | Merging with Different Joins (Udemy, DataCamp)  
**Topics:** Machine Learning fundamentals | First models | Advanced joins

---

## 🎯 Key Concepts Learned

### Machine Learning Basics

**What is Machine Learning?**
- Learn patterns from data
- Make predictions on new data
- Supervised: labeled data
- Unsupervised: unlabeled data
- Key: Training vs Testing

**Supervised Learning:**
- Regression: Predict continuous values (price, temperature)
- Classification: Predict categories (spam/not spam, cat/dog)

---

### Linear Regression

**Theory:**
```
y = m*x + b
- y: predicted value
- x: input feature
- m: slope (weight)
- b: intercept (bias)
```

**When to Use:**
- Continuous prediction
- Linear relationship between features & target
- Interpretability important
- Fast & simple model

**Cost Function:**
- Minimizes sum of squared errors (SSE)
- Gradient descent finds optimal weights
- Want: minimize prediction error

---

### Scikit-learn Workflow

**Standard ML Workflow:**
```python
from sklearn.linear_model import LinearRegression
from sklearn.model_selection import train_test_split
from sklearn.metrics import r2_score, mean_squared_error
import pandas as pd

# 1. Load data
df = pd.read_csv('data.csv')

# 2. Prepare features (X) & target (y)
X = df[['feature1', 'feature2']]
y = df['target']

# 3. Split into train & test
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)

# 4. Create model
model = LinearRegression()

# 5. Train model
model.fit(X_train, y_train)

# 6. Make predictions
y_pred = model.predict(X_test)

# 7. Evaluate
r2 = r2_score(y_test, y_pred)
mse = mean_squared_error(y_test, y_pred)
print(f'R² Score: {r2}')
print(f'MSE: {mse}')

# 8. Get weights
print(f'Coefficients: {model.coef_}')
print(f'Intercept: {model.intercept_}')
```

---

### Model Persistence

**Save & Load Models:**
```python
import pickle

# Save model
with open('model.pkl', 'wb') as f:
    pickle.dump(model, f)

# Load model
with open('model.pkl', 'rb') as f:
    model = pickle.load(f)

# Use loaded model
predictions = model.predict(new_data)
```

---

### Advanced Joins

**Merge Operations:**
```python
# Different join types
df1 = pd.DataFrame({'key': [1, 2, 3], 'A': ['a', 'b', 'c']})
df2 = pd.DataFrame({'key': [1, 2, 4], 'B': ['x', 'y', 'z']})

# Inner (only matching)
inner = pd.merge(df1, df2, on='key')  # [1, 2]

# Left (all from df1)
left = pd.merge(df1, df2, on='key', how='left')  # [1, 2, 3]

# Right (all from df2)
right = pd.merge(df1, df2, on='key', how='right')  # [1, 2, 4]

# Outer (all from both)
outer = pd.merge(df1, df2, on='key', how='outer')  # [1, 2, 3, 4]
```

**Merge with Suffixes:**
```python
# When column names conflict
merged = pd.merge(
    df1, df2,
    on='id',
    suffixes=('_left', '_right')
)
```

---

## 💻 Code Example

```python
from sklearn.linear_model import LinearRegression
from sklearn.model_selection import train_test_split
from sklearn.metrics import r2_score
import pandas as pd
import pickle

# Load data
df = pd.read_csv('heart_disease.csv')

# Prepare data
X = df[['age', 'cholesterol', 'blood_pressure']]
y = df['health_score']

# Split
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)

# Train model
model = LinearRegression()
model.fit(X_train, y_train)

# Evaluate
score = model.score(X_test, y_test)
print(f'Model R² Score: {score:.3f}')

# Save model
pickle.dump(model, open('health_model.pkl', 'wb'))

# Predictions
new_data = [[50, 200, 130]]
prediction = model.predict(new_data)
print(f'Prediction: {prediction[0]:.2f}')
```

---

## ✅ Accomplishments

✅ Learned ML fundamentals  
✅ Built first Linear Regression model  
✅ Trained & evaluated model  
✅ Made predictions on test data  
✅ Saved model with pickle  
✅ Understood scikit-learn workflow  
✅ Practiced advanced joins  
✅ **First working ML model!** 🎉  

---

## 🚧 Challenges & Solutions

| Challenge | Solution |
|-----------|----------|
| Understanding training/testing split | Visualized: data→split→train→test→evaluate |
| Model evaluation metrics | Learned R², MSE meaning & interpretation |
| Saving model correctly | Used pickle with 'wb' (write binary) mode |
| Join confusion | Practiced all 4 types with simple data |

---

## 📊 Time Breakdown

- ML Theory: 2 hours
- Linear Regression: 2 hours
- Scikit-learn Practice: 2.5 hours
- Advanced Joins: 1 hour
- Model Persistence: 0.5 hours

---

## 💡 Key Takeaways

1. **ML Workflow:** Load → Prepare → Split → Train → Evaluate
2. **Train/Test:** Split prevents overfitting on training data
3. **R² Score:** Higher is better (1.0 = perfect)
4. **Pickle:** Easy way to save Python objects
5. **Linear Regression:** Simple, interpretable, good baseline
6. **Scikit-learn:** Standard ML library; consistent API

---

## 🎯 Confidence Level: 7.5/10

- Good understanding of ML workflow
- Can build & train models
- Understand basic evaluation
- Comfortable with scikit-learn syntax
- Ready to improve models (Week 3 focus)

---

## 🚀 Tomorrow's Focus (Day 6)

- Logistic Regression (classification)
- OpenAI API integration
- GenAI fundamentals
- Building chatbots
- Tableau introduction

---

## 📚 Resources

- Udemy: Complete ML Bootcamp
- Scikit-learn documentation
- Real datasets for practice

---

**Status:** ML Journey Begun! ✅

**Week 1:** 7/7 ✅ | **Week 2:** 5/7 ✅
