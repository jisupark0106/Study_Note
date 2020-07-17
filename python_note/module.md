# 1.12 Modules

```python
# modules : sets of function
# ex, math -> module import
# we can find module in python standard library

# import math
from math import ceil, fabs
from math import fsum as sum 
print(math.ceil(1.2))
print(math.fabs(1.2))
```

Import module example

```python
# calculator.py
def add (a,b):
	return a+b
```

```python
# main.py
# you can use file name (main), do not use main.py
from caculator import add
print(add(1,5))
```

# 2.0 What is Web Scrapping

### Web Scrapping

웹으로부터 데이터를 추출하는 것

# 2.1 What are We Building

채용정보 scrapping 

# 2.2 Navigating with Python

```python
# html 스크랩핑, text변환
import requests

indeed_result = requests.get("https://kr.indeed.com/jobs?q=python&l=seoul")
print(indeed_result.text)
```

beautiful soup : html 정보를 추출하기 좋은 package
