# Week 2: Day 6 Learning Log

**Status:** ✅ Complete  
**Consistency:** 13/14 days (93%)

---

## 📚 Source Material

**Courses:** Logistic Regression | OpenAI API | Building Chatbots | Tableau (Udemy, DataCamp, Tableau)  
**Topics:** Classification | GenAI | API integration | Data visualization

---

## 🎯 Key Concepts Learned

### Logistic Regression (Classification)

**Theory:**
- Predicts probability (0 to 1)
- Sigmoid function: smooth S-curve
- Output: P(class=1)
- Decision boundary: typically 0.5

**When to Use:**
- Binary classification (yes/no, spam/ham)
- Probability predictions needed
- Interpretable features important

**Scikit-learn Implementation:**
```python
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import classification_report, confusion_matrix
import pandas as pd

# Data preparation
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)

# Create & train
clf = LogisticRegression(random_state=42)
clf.fit(X_train, y_train)

# Predictions
y_pred = clf.predict(X_test)  # Class predictions
y_proba = clf.predict_proba(X_test)  # Probabilities

# Evaluation
print(confusion_matrix(y_test, y_pred))
print(classification_report(y_test, y_pred))
```

**Evaluation Metrics:**
- Accuracy: % correct predictions
- Precision: of predicted positive, how many correct
- Recall: of actual positive, how many detected
- F1-score: Balance of precision & recall

---

### OpenAI API

**Setup & Basic Usage:**
```python
from openai import OpenAI

client = OpenAI(api_key='your-api-key')

# Simple chat
response = client.chat.completions.create(
    model='gpt-4o-mini',
    messages=[{'role': 'user', 'content': 'Hello!'}]
)
print(response.choices[0].message.content)
```

**Prompting Techniques:**

1. **Zero-shot:** Direct question, no examples
```python
messages = [{'role': 'user', 'content': 'Classify: This is great!'}]
```

2. **Few-shot:** Provide examples first
```python
messages = [
    {'role': 'user', 'content': 'Classify: Awesome! | Positive'},
    {'role': 'user', 'content': 'Classify: This is great!'}
]
```

3. **System message:** Set behavior
```python
messages = [
    {'role': 'system', 'content': 'You are a helpful assistant.'},
    {'role': 'user', 'content': 'What is ML?'}
]
```

**Multi-turn Conversations:**
```python
conversation = [
    {'role': 'system', 'content': 'You are a math tutor.'},
    {'role': 'user', 'content': 'What is 2+2?'},
    {'role': 'assistant', 'content': '2+2 equals 4.'},
    {'role': 'user', 'content': 'What about 3+5?'}
]
response = client.chat.completions.create(
    model='gpt-4o-mini',
    messages=conversation
)
```

---

### Building Chatbots

**Simple Chatbot Pattern:**
```python
def chatbot():
    messages = [{'role': 'system', 'content': 'You are helpful.'}]
    
    while True:
        user_input = input('You: ')
        messages.append({'role': 'user', 'content': user_input})
        
        response = client.chat.completions.create(
            model='gpt-4o-mini',
            messages=messages
        )
        
        assistant_message = response.choices[0].message.content
        messages.append({'role': 'assistant', 'content': assistant_message})
        print(f'Bot: {assistant_message}')
```

---

### Tableau Fundamentals

**Data Connections:**
- Connect to various data sources
- CSV, Excel, databases, cloud services
- Refresh data automatically
- Live vs extract connections

**Basic Workflow:**
1. Connect to data source
2. Explore data structure
3. Drag fields to build visualization
4. Format & style
5. Create dashboard
6. Share insights

---

## 💻 Code Example

```python
from sklearn.linear_model import LogisticRegression
from sklearn.model_selection import train_test_split
from sklearn.metrics import classification_report
from openai import OpenAI
import pandas as pd

# 1. Logistic Regression
df = pd.read_csv('titanic.csv')
X = df[['age', 'fare', 'pclass']]
y = df['survived']

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)

clf = LogisticRegression()
clf.fit(X_train, y_train)

print(classification_report(y_test, clf.predict(X_test)))

# 2. OpenAI API for classification
client = OpenAI(api_key='your-key')

messages = [
    {'role': 'system', 'content': 'Classify sentiment: positive/negative'},
    {'role': 'user', 'content': '"This product is amazing!" | Classify:'}
]

response = client.chat.completions.create(
    model='gpt-4o-mini',
    messages=messages
)
print(response.choices[0].message.content)
```

---

## ✅ Accomplishments

✅ Mastered Logistic Regression  
✅ Understood classification metrics  
✅ Built OpenAI API integration  
✅ Implemented few-shot prompting  
✅ Created multi-turn chatbot  
✅ Connected to Tableau data sources  
✅ Understood confusion matrix  
✅ Explored GenAI capabilities  

---

## 🚧 Challenges & Solutions

| Challenge | Solution |
|-----------|----------|
| Classification vs Regression | Clear: classification=categories, regression=continuous |
| Understanding probabilities | Visualized: sigmoid curve, threshold at 0.5 |
| API costs | Started with simple prompts, understood token counting |
| Tableau interface | Explored connection options systematically |

---

## 💡 Key Takeaways

1. **Classification:** Different problem type than regression
2. **Probabilities:** More informative than just predictions
3. **Confusion matrix:** Visual summary of model performance
4. **OpenAI API:** Powerful tool for text tasks
5. **Few-shot prompting:** Improves output quality
6. **Chatbots:** Simple state management + API = interactive AI

---

## 🚀 Tomorrow's Focus (Day 7)

- Capstone project (Supply Chain Analytics)
- Apply all Week 2 skills
- Build complete end-to-end project
- Professional documentation
- Model evaluation & insights

---

## 📚 Resources

- Udemy: ML Bootcamp (Classification section)
- DataCamp: OpenAI API course
- OpenAI documentation
- Scikit-learn metrics guide

---

**Status:** Ready for Capstone! ✅

**Week 1:** 7/7 ✅ | **Week 2:** 6/7 ✅
