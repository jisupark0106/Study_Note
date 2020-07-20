2.11- 2.13 이전과 동일

# 2.14 What is CSV

comma-separated variables

# 2.15 Saving to CSV

```python
import csv

def save_to_file(jobs):
  file = open("jobs.csv",mode="w")
  writer=csv.writer(file)
  writer.writerow(["title","company","location","link"])
  for job in jobs:
    writer.writerow(list(job.values()))
    
  return
```

# 2.16 OMG THIS IS AWESOME

결과물 예시 

```python
title,company,location,link
[XR Experience] 메디컬 콘텐츠 Unity 개발 경력자,테트라시그넘,서울 송파구,https://kr.indeed.com/jobs?q=python&l=seoul&vjk=993c3077a05b9867&from=web&vjs=3
Cross Border e-Commerce - Business Intelligence for Korea Market,Shopee,서울,https://kr.indeed.com/jobs?q=python&l=seoul&vjk=69b824318cebcbb9&from=web&vjs=3
[TmaxAI/기술] 기술지원 엔지니어,티맥스소프트,성남 분당구,https://kr.indeed.com/jobs?q=python&l=seoul&vjk=94bbaed0e8988ea6&from=web&vjs=3
```
