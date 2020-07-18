# 2.6 Extracting Titles

```python
def extract_indeed_jobs(last_page):
  for page in range(last_page) :
    result = requests.get(f"{URL}&start={0*LIMIT}")
    soup=BeautifulSoup(result.text,"html.parser")
    results = soup.find_all("div",{"class":"jobsearch-SerpJobCard"})

    for result in results:
      title=result.find("h2",{"class":"title"}).find("a")["title"]
    
      print(title)
```

# 2.7 Extracting Companies

```python
def extract_job(result):
  title=result.find("h2",{"class":"title"}).find("a")["title"]
  company = result.find("span",{"class":"company"})
  company_anchor = company.find("a")
  if company_anchor is not None:
    company = company_anchor.string
  else:
    company=company.string
  company=company.strip()
  print(title+" : "+company)
  return {'title': title,'company':company}
```

# 2.8 Extracting Locations and Finishing up

```python
import requests
from bs4 import BeautifulSoup

LIMIT = 50
URL = "https://kr.indeed.com/jobs?q=python&l=seoul&limit={LIMIT}"

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

def extract_job(result):
  title=result.find("h2",{"class":"title"}).find("a")["title"]
  company = result.find("span",{"class":"company"})
  company_anchor = company.find("a")
  if company_anchor is not None:
    company = company_anchor.string
  else:
    company=company.string
  company=company.strip()
  location = result.find("span",{"class":"location"}).string
  job_id = result["data-jk"]

  return {'title': title,'company':company,'location':location,'link':f"https://kr.indeed.com/jobs?q=python&l=seoul&vjk={job_id}&from=web&vjs=3"}

def extract_indeed_jobs(last_page):
  jobs=[]
  for page in range(last_page) :
    result = requests.get(f"{URL}&start={page*LIMIT}")
    soup=BeautifulSoup(result.text,"html.parser")
    results = soup.find_all("div",{"class":"jobsearch-SerpJobCard"})

  for result in results:
    job = extract_job(result)
    jobs.append(job)
  return jobs
```

# 2.9 StackOverflow Pages

```python
import requests
from bs4 import BeautifulSoup

URL = "https://stackoverflow.com/jobs?q=python"

def get_last_pages():
  result  = requests.get(URL)
  soup=BeautifulSoup(result.text,'html.parser')

  pages=soup.find("div","s-pagination").find_all("a")

  last_page = pages[-2].get_text().strip()
  print(last_page)
  return int(last_page)
```
stackoverflow는 혼자해보기
