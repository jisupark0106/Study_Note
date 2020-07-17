# 2.3 Extracting Indeed Pages

[https://www.crummy.com/software/BeautifulSoup/bs4/doc/#quick-start](https://www.crummy.com/software/BeautifulSoup/bs4/doc/#quick-start)

```python
import requests
from bs4 import BeautifulSoup

indeed_result = requests.get("https://kr.indeed.com/jobs?q=python&l=seoul")

indeed_soup = BeautifulSoup(indeed_result.text,"html.parser")

pagination = indeed_soup.find("div",{"class":"pagination"})

pages = pagination.find_all('a')

spans =[]

for page in pages:
  spans.append(page.find("span",{"class":"pn"}))

# array 접근 공부하기
print(spans[:-1])
```

# 2.4 Extracting Indeed Pages part Two

```python
import requests
from bs4 import BeautifulSoup

indeed_result = requests.get("https://kr.indeed.com/jobs?q=python&l=seoul")

indeed_soup = BeautifulSoup(indeed_result.text,"html.parser")

pagination = indeed_soup.find("div",{"class":"pagination"})

links = pagination.find_all('a')
pages =[]

# [:-1] except next page
for link in links[:-1]:
  pages.append(int(link.string))

# last page 
max_page=pages[-1]
```

# 2.5 Requesting Each Page

```python
from indeed import extract_indeed_pages
from indeed import extract_indeed_jobs

last_indeed_page = extract_indeed_pages()

extract_indeed_jobs(last_indeed_page)
```

```python
import requests
from bs4 import BeautifulSoup

LIMIT = 50
URL = "https://www.indeed.com/jobs?q=python&limit={LIMIT}"

def extract_indeed_pages():
  result = requests.get(URL)

  soup = BeautifulSoup(result.text,"html.parser")

  pagination = soup.find("div",{"class":"pagination"})

  links = pagination.find_all('a')
  pages =[]

  # [:-1] except next page
  for link in links[:-1]:
    pages.append(int(link.string))

  # last page 
  max_page=pages[-1]
  
  return max_page

def extract_indeed_jobs(last_page):
  for page in range(last_page) :
    result = requests.get(f"{URL}&start={page*LIMIT}")
    print(result.status_code)
```
