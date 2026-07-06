# Week 3: Day 1 Learning Log

**Date:** [Insert Date] | **Duration:** 8 hours | **Status:** ✅ Complete  
**Consistency:** 15/21 days (71%)

---

## 📚 Source Material

**Course:** ML A-Z (2026) - Udemy (Deloitte)  
**Link:** https://deloittedevelopment.udemy.com/course/machinelearning/  
**Additional:** Python for ML & DS Masterclass (Udemy)

**Topics:** 22 detailed sections on ML data preparation

---

## 🎯 Key Concepts Learned

### 1. From Raw Data to ML-Ready Datasets

**The ML Pipeline:**
```
Raw Data → Clean Data → Prepared Data → ML Model → Predictions
  ↓          ↓            ↓              ↓          ↓
Import    Process    Transform      Train       Deploy
```

**What Makes Data "ML-Ready":**
- No missing values
- Categorical data encoded
- Features scaled properly
- Train/test split done
- No outliers (usually)
- Correct data types

---

### 2. Core Libraries for ML Preparation

```python
import numpy as np          # Numerical computing
import pandas as pd         # Data manipulation
import matplotlib.pyplot as plt  # Visualization
from sklearn.impute import SimpleImputer  # Missing values
from sklearn.preprocessing import StandardScaler, OneHotEncoder  # Scaling/Encoding
from sklearn.model_selection import train_test_split  # Train/Test split
from sklearn.compose import ColumnTransformer  # Multi-step preprocessing
```

---

### 3. Importing Datasets with Pandas

**Basic Import:**
```python
dataset = pd.read_csv('filename.csv')
```

**Common Parameters:**
```python
# Custom delimiter
df = pd.read_csv('file.csv', delimiter=';')

# Handle different separators
df = pd.read_csv('file.tsv', delimiter='\t')

# Skip rows
df = pd.read_csv('file.csv', skiprows=2)

# On bad lines
df = pd.read_csv('file.csv', on_bad_lines='skip')
```

---

### 4. Feature Selection with iloc

**Getting Features & Target:**
```python
# All rows, all columns except last
X = dataset.iloc[:, :-1].values

# All rows, last column only
y = dataset.iloc[:, -1].values

# Specific columns
X = dataset.iloc[:, [0, 1, 3]].values

# Specific range
X = dataset.iloc[:, 1:4].values
```

---

### 5. Handling Missing Values - SimpleImputer

**Problem:** Missing data breaks ML models

**Solution:** Replace with mean, median, or mode

```python
from sklearn.impute import SimpleImputer
import numpy as np

# Create imputer (mean strategy)
imputer = SimpleImputer(missing_values=np.nan, strategy='mean')

# Fit on training data (all columns)
imputer.fit(X[:, 0:8])

# Transform to replace NaN
X[:, 0:8] = imputer.transform(X[:, 0:8])
```

**Strategies Available:**
- `'mean'` - Average of column
- `'median'` - Middle value
- `'most_frequent'` - Mode
- `'constant'` - Fixed value

---

### 6. Encoding Categorical Data

**One-Hot Encoding (Multiple Categories):**
```python
from sklearn.compose import ColumnTransformer
from sklearn.preprocessing import OneHotEncoder

# Create transformer
ct = ColumnTransformer(
    transformers=[
        ('encoder', OneHotEncoder(), [0])  # Column 0
    ],
    remainder='passthrough'  # Keep other columns
)

# Apply encoding
X = np.array(ct.fit_transform(X))
```

**Label Encoding (Binary/Target):**
```python
from sklearn.preprocessing import LabelEncoder

le = LabelEncoder()
y = le.fit_transform(y)  # 'Yes'→1, 'No'→0
```

---

### 7. Train/Test Split

**Concept:** Split data to validate model properly

**Standard Split:**
```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(
    X, y,
    test_size=0.2,      # 80/20 split
    random_state=42     # Reproducibility
)
```

**Why `random_state=42`?**
- Ensures same split every run
- Makes results reproducible
- Good for debugging

---

### 8. Feature Scaling - StandardScaler

**Problem:** Features at different scales confuse ML models

**Solution:** Scale features to same range

```python
from sklearn.preprocessing import StandardScaler

# Create scaler
sc = StandardScaler()

# FIT on training data (important!)
X_train_scaled = sc.fit_transform(X_train)

# TRANSFORM test data (don't fit again)
X_test_scaled = sc.transform(X_test)
```

**Why Separate fit & transform?**
- Fit: Calculate mean & std from TRAINING data
- Transform: Apply same calculation to test data
- Prevents data leakage

---

### 9. Complete Data Preprocessing Pipeline

```python
import pandas as pd
import numpy as np
from sklearn.impute import SimpleImputer
from sklearn.preprocessing import OneHotEncoder, LabelEncoder, StandardScaler
from sklearn.compose import ColumnTransformer
from sklearn.model_selection import train_test_split

# 1. Import
dataset = pd.read_csv('data.csv')

# 2. Split features & target
X = dataset.iloc[:, :-1].values
y = dataset.iloc[:, -1].values

# 3. Handle missing values
imputer = SimpleImputer(strategy='mean')
X[:, 1:3] = imputer.fit_transform(X[:, 1:3])

# 4. Encode categorical features
ct = ColumnTransformer(
    transformers=[('encoder', OneHotEncoder(), [0])],
    remainder='passthrough'
)
X = np.array(ct.fit_transform(X))

# 5. Encode target variable
le = LabelEncoder()
y = le.fit_transform(y)

# 6. Train/Test split
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)

# 7. Feature scaling
sc = StandardScaler()
X_train[:, 3:] = sc.fit_transform(X_train[:, 3:])
X_test[:, 3:] = sc.transform(X_test[:, 3:])

# Ready for ML models!
```

---

## 💻 Coding Exercises Completed

### Exercise 1: Importing & Preprocessing
- ✅ Loaded dataset with pandas
- ✅ Created X & y matrices
- ✅ Used iloc for feature selection
- ✅ Extracted as numpy arrays

### Exercise 2: Handling Missing Data
- ✅ Identified missing values
- ✅ Applied SimpleImputer
- ✅ Used mean strategy
- ✅ Fitted & transformed correctly

### Exercise 3: Encoding Categorical Data
- ✅ One-Hot encoded multiple categories
- ✅ Label encoded binary target
- ✅ Used ColumnTransformer
- ✅ Handled mixed data types

### Exercise 4: Dataset Splitting & Scaling
- ✅ Split 80/20 train/test
- ✅ Applied StandardScaler
- ✅ Used random_state for reproducibility
- ✅ Verified scaled output

### Exercise 5: Feature Scaling (Wine Dataset)
- ✅ Loaded wine quality dataset
- ✅ Handled custom delimiter (`;`)
- ✅ Applied proper scaling pipeline
- ✅ Verified transformations

### Complete Pipeline: Data Preprocessing Tools
- ✅ Full end-to-end pipeline
- ✅ All preprocessing steps
- ✅ Production-ready code
- ✅ Clear documentation

---

## 📊 Data Processing Skills Acquired

### Data Import
✅ CSV file loading with pandas  
✅ Custom delimiters (`;`, `\t`)  
✅ Error handling for bad lines  
✅ DataFrame inspection  

### Missing Value Handling
✅ Identified missing data  
✅ SimpleImputer configuration  
✅ Mean/median/mode strategies  
✅ Applied on specific columns  

### Categorical Encoding
✅ One-Hot Encoding (nominal)  
✅ Label Encoding (binary/ordinal)  
✅ ColumnTransformer usage  
✅ Handling mixed data types  

### Train/Test Splitting
✅ 80/20 splits  
✅ Random state reproducibility  
✅ Stratified sampling  
✅ Avoiding data leakage  

### Feature Scaling
✅ StandardScaler (z-score)  
✅ Fit vs Transform distinction  
✅ Separate train/test scaling  
✅ Scaling only numerical features  

---

## ✅ Accomplishments

✅ Completed all 22 lecture topics  
✅ Mastered 5 coding exercises  
✅ Built complete preprocessing pipeline  
✅ Understood each preprocessing step  
✅ Practiced on 3+ real datasets  
✅ Code quality: Professional  

---

## 🚧 Challenges & Solutions

| Challenge | Solution |
|-----------|----------|
| Understanding iloc syntax | Practiced with different ranges & columns |
| When to use fit vs transform | Realized fit only on training data |
| Choosing imputation strategy | Tested mean/median for different datasets |
| Encoding categorical data | Used OneHotEncoder for nominal, Label for binary |
| Feature scaling importance | Saw dramatic accuracy improvement with scaling |

---

## 📊 Time Breakdown

- Lectures (22 topics): 3.5 hours
- Coding Exercise 1-5: 3 hours
- Complete Pipeline Project: 1 hour
- Practice & Experimentation: 0.5 hours

**Total: 8 hours**

---

## 💡 Key Takeaways

1. **Data prep is 80% of ML work** - More important than the algorithm
2. **Order matters** - Impute → Encode → Split → Scale
3. **Never fit on test data** - Major source of errors
4. **Reproducibility** - Always use random_state
5. **Understand each step** - Don't just copy code
6. **Check your data** - Print outputs to verify transformations

---

## 🎯 Confidence Level: 9/10

- Solid grasp of all preprocessing steps
- Can implement complete pipeline from scratch
- Understand why each step exists
- Ready to preprocess any dataset
- Prepared for ML model building

---

## 🚀 Tomorrow's Focus (Day 2)

**Week 3 Day 2 Plan:**
- Feature Engineering techniques
- Handling categorical features (advanced)
- Outlier detection & treatment
- Feature creation & selection
- Real-world data challenges

---

## 📚 Resources Used

- Udemy: ML A-Z (2026) - Deloitte
- Udemy: Python for ML & DS Masterclass
- Scikit-learn official documentation
- 5 Coding exercises (completed)
- Data Preprocessing Tools notebook

---

## 🎓 Connection to Bigger Picture

**Week 1-2:** Built basic ML models  
**Week 3 Day 1:** Now learning to properly prepare data  
**Week 3 Days 2-6:** Advanced techniques  
**Week 3 Day 7:** Capstone with optimized preprocessing  

**Why this matters:** Good data prep → Better models → Better results

---

## 📝 Jupyter Notebooks Created

- ✅ Coding_Exercise_1.ipynb (Import & Preprocess)
- ✅ Coding_Exercise_2.ipynb (Missing Data)
- ✅ Coding_Exercise_3.ipynb (Encoding)
- ✅ Coding_Exercise_4.ipynb (Split & Scale)
- ✅ Coding_Exercise_5.ipynb (Feature Scaling)
- ✅ data_preprocessing_tools.ipynb (Complete Pipeline)

---

**Status:** Ready for Day 2 ✅

**Week 1:** 7/7 ✅ | **Week 2:** 7/7 ✅ | **Week 3:** 1/7 ✅

---

*End of Day 1 Log*

**Total Consistency:** 15/21 days (71%)
