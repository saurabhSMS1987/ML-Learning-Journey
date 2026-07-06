# Week 3: Day 1 Learning Log

**Status:** ✅ Complete  
**Consistency:** 15/21 days (71%)

---

## 📚 Source Material

**Course:** ML A-Z (2026) - Udemy (Deloitte)  
**Topics:** Data preprocessing & ML preparation (22 sections)

---

## 🎯 Key Concepts Learned

### Data Preprocessing Pipeline

**Complete Workflow:**
```python
Import Data → Handle Missing → Encode Categories → Split Train/Test → Scale Features → Ready for ML
```

### Core Techniques

**1. Importing & Feature Selection (iloc)**
```python
dataset = pd.read_csv('file.csv')
X = dataset.iloc[:, :-1].values  # Features
y = dataset.iloc[:, -1].values   # Target
```

**2. Handling Missing Values (SimpleImputer)**
```python
from sklearn.impute import SimpleImputer
imputer = SimpleImputer(strategy='mean')
X[:, 1:3] = imputer.fit_transform(X[:, 1:3])
```

**3. Encoding Categorical Data**
```python
# One-Hot Encoding (multiple categories)
ct = ColumnTransformer([('encoder', OneHotEncoder(), [0])], remainder='passthrough')
X = np.array(ct.fit_transform(X))

# Label Encoding (binary/target)
le = LabelEncoder()
y = le.fit_transform(y)
```

**4. Train/Test Split**
```python
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
```

**5. Feature Scaling (StandardScaler)**
```python
sc = StandardScaler()
X_train = sc.fit_transform(X_train)    # Fit on training
X_test = sc.transform(X_test)          # Transform test (don't fit again!)
```

---

## ✅ Accomplishments

✅ Completed 22 lecture topics  
✅ Mastered 5 coding exercises  
✅ Built complete preprocessing pipeline  
✅ Handled missing data with SimpleImputer  
✅ Encoded categorical features (One-Hot & Label)  
✅ Performed proper train/test split  
✅ Applied feature scaling correctly  
✅ Practiced on 3+ real datasets  

---

## 🚧 Key Challenges

| Issue | Solution |
|-------|----------|
| iloc syntax | Practiced with different column ranges |
| Fit vs Transform | Learned: fit only on training data |
| Imputation strategy | Tested mean/median for different datasets |
| When to scale | Understood: after splitting, before modeling |

---

## 💡 Key Takeaways

1. **Data prep = 80% of ML work** (more important than algorithm choice)
2. **Order matters** - Impute → Encode → Split → Scale
3. **Never fit test data** - Prevents data leakage
4. **random_state=42** - Ensures reproducibility
5. **Fit on training, transform test** - Standard practice
6. **Verify transformations** - Always print outputs

---

## 🎯 Confidence Level: 9/10

Ready to preprocess any dataset with proper techniques ✅

---

## 📚 Files Created

- ✅ Coding_Exercise_1.ipynb
- ✅ Coding_Exercise_2.ipynb
- ✅ Coding_Exercise_3.ipynb
- ✅ Coding_Exercise_4.ipynb
- ✅ Coding_Exercise_5.ipynb
- ✅ data_preprocessing_tools.ipynb

---

**Status:** Ready for Day 2 ✅  
**Week 3 Progress:** 1/7 days ✅
