# Week 2: Day 3 Learning Log

**Date:** [Insert Date] | **Duration:** 8 hours | **Status:** ✅ Complete  
**Consistency:** 10/14 days (71%)

---

## 📚 Source Material

**Courses:** Working with Databases (DataCamp) | Importing Data from Databases | JSON & APIs (DataCamp)  
**Topics:** Relational databases | SQL queries in Python | APIs | JSON data

---

## 🎯 Key Concepts Learned

### Relational Databases in Python

**Database Connections:**
```python
from sqlalchemy import create_engine
import pandas as pd

# Create connection
engine = create_engine('sqlite:///database.db')
# or: 'postgresql://user:password@localhost/dbname'

# Query database into DataFrame
df = pd.read_sql('SELECT * FROM users', engine)

# Close connection
engine.dispose()
```

**Database Operations:**
```python
# Execute query
result = engine.execute('SELECT * FROM orders WHERE amount > 100')

# Get data from specific table
df = pd.read_sql_table('users', engine)

# Execute custom SQL
df = pd.read_sql_query('SELECT * FROM users WHERE age > 25', engine)
```

---

### JSON Data Handling

**Loading JSON:**
```python
import json

# From file
with open('data.json') as f:
    data = json.load(f)

# From string
json_string = '{"name": "John", "age": 30}'
data = json.loads(json_string)

# Using pandas
df = pd.read_json('data.json')
```

**Working with Nested JSON:**
```python
# Flatten nested JSON
from pandas.io.json import json_normalize

nested = {'user': {'name': 'John', 'age': 30}, 'city': 'NYC'}
df = json_normalize(nested)

# Access nested values
user_name = data['user']['name']
for item in data['items']:
    print(item['id'])
```

**Converting to JSON:**
```python
# DataFrame to JSON
df.to_json('output.json')

# Dictionary to JSON
import json
json_str = json.dumps(data)
```

---

### API Integration

**Making API Requests:**
```python
import requests

# GET request
response = requests.get('https://api.example.com/users')
data = response.json()

# With parameters
params = {'page': 1, 'limit': 10}
response = requests.get('https://api.example.com/users', params=params)

# With headers (authentication)
headers = {'Authorization': 'Bearer YOUR_TOKEN'}
response = requests.get('https://api.example.com/users', headers=headers)
```

**Error Handling:**
```python
try:
    response = requests.get(url)
    response.raise_for_status()  # Raise error for bad status
    data = response.json()
except requests.exceptions.RequestException as e:
    print(f'Error: {e}')
```

**Working with API Responses:**
```python
# Check status
print(response.status_code)  # 200 = success

# Get response data
data = response.json()

# Convert to DataFrame
df = pd.DataFrame(data)
```

---

### Database Queries in Python

**Common SQL Operations:**
```python
# SELECT
df = pd.read_sql('SELECT * FROM table WHERE condition', engine)

# JOIN
query = '''
SELECT u.name, o.amount
FROM users u
JOIN orders o ON u.id = o.user_id
WHERE o.amount > 100
'''
df = pd.read_sql(query, engine)

# GROUP BY
query = '''
SELECT category, COUNT(*) as count, SUM(amount) as total
FROM sales
GROUP BY category
'''
df = pd.read_sql(query, engine)

# ORDER BY
df = pd.read_sql('SELECT * FROM users ORDER BY age DESC', engine)
```

---

### Combining Multiple Data Sources

```python
import pandas as pd

# Load from different sources
df_sql = pd.read_sql('SELECT * FROM database', engine)
df_json = pd.read_json('data.json')
df_csv = pd.read_csv('data.csv')

# Combine
combined = pd.concat([df_sql, df_json, df_csv])

# Merge
merged = pd.merge(df_sql, df_json, on='id')
```

---

## 💻 Code Example

```python
import pandas as pd
import requests
from sqlalchemy import create_engine

# 1. Get data from database
engine = create_engine('sqlite:///sales.db')
db_data = pd.read_sql('SELECT * FROM sales', engine)

# 2. Get data from API
response = requests.get('https://api.example.com/inventory')
api_data = pd.DataFrame(response.json())

# 3. Get data from JSON file
json_data = pd.read_json('updates.json')

# 4. Combine all sources
all_data = pd.concat([db_data, api_data, json_data])

# 5. Clean & save
all_data.dropna(inplace=True)
all_data.to_csv('combined_data.csv', index=False)
```

---

## ✅ Accomplishments

✅ Mastered database connections (SQLAlchemy)  
✅ Executed SQL queries from Python  
✅ Learned JSON structure & handling  
✅ Practiced nested JSON flattening  
✅ Made API requests  
✅ Handled API responses  
✅ Combined multiple data sources  
✅ Error handling & robustness  

---

## 🚧 Challenges & Solutions

| Challenge | Solution |
|-----------|----------|
| Nested JSON structure | Used json_normalize() to flatten |
| API authentication | Passed headers with Bearer token |
| Combining different formats | Used pd.concat() for vertical stacking |
| Database connection strings | Researched correct syntax for each DB |

---

## 📊 Time Breakdown

- Database Operations: 2.5 hours
- JSON Data: 2 hours
- API Integration: 2 hours
- Multi-source combining: 1.5 hours

---

## 💡 Key Takeaways

1. **SQLAlchemy:** Universal interface for different databases
2. **JSON:** Flexible format for APIs and config files
3. **APIs:** Modern data exchange standard
4. **Error handling:** Critical for production systems
5. **Data integration:** Combining sources is common in real projects
6. **CORS & authentication:** Needed for many APIs

---

## 🎯 Confidence Level: 8/10

- Comfortable with database queries
- Can parse JSON confidently
- Understand API request/response cycle
- Can handle multiple data sources
- Know error handling patterns

---

## 🚀 Tomorrow's Focus (Day 4)

- DataFrame transformations
- Aggregations & groupby
- Advanced indexing
- Merging & joining deep dive
- Real data analysis practice

---

## 📚 Resources

- DataCamp: Database & API courses
- SQLAlchemy documentation
- Requests library docs
- JSON specification

---

**Status:** Ready for Day 4 ✅

**Week 1:** 7/7 ✅ | **Week 2:** 3/7 ✅
