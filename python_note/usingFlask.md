# 4.1 Introduction to Flask

```python
from flask import Flask

app = Flask("usingFlask")

@app.route("/")
def home():
  return "Hello Welcom to jisupark"

@app.route("/contact")
def contact():
  return "Contact me!"

# repl.it 
app.run(host="0.0.0.0")
```

# 4.2 Dynamic URLs and Templates

templates/jobsearch.html

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Job Search</title>
  </head>
  <body>
    <h1>Job search</h1>
    <form action="/report" method="get">
      <input placeholder='Search for a job' required name ="word"/>
      <button>Search</button>
    </form>
  </body>
</html>
```

main.py

```python
@app.route("/")
def home():
  return render_template("jobsearch.html")
```

# 4.3 Forms and Query Arguments

```python
from flask import Flask, render_template,request

@app.route("/report")
def report():
  word = request.args.get('word')
  return f"this is the {word} report"
```

report.html

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Job Search</title>
  </head>
  <body>
   <h1>Search Results</h1>
   <h3>You are looking for {{searchingBy}} </h3>
  </body>
</html>
```

```python
@app.route("/report")
def report():
  word = request.args.get('word')
  return render_template("report.html",searchingBy = word)
```

[https://usingflask.jisupark0106.repl.co/report?word=hello](https://usingflask.jisupark0106.repl.co/report?word=hello)

# 4.4 Scrapper Integration

word가 존재하지 않으면 home으로 redirect

```python
@app.route("/report")
def report():
  word = request.args.get('word')
  if word:
    word = word.lower()
  else: 
    return redirect('/')
  return render_template("report.html",searchingBy = word)
```

# 4.5 Faster Scrapper

fake DB 만들기

```python
db = {}

@app.route("/report")
def report():
  word = request.args.get('word')
  if word:
    word = word.lower()
    fromdb = db.get(word)

    if fromdb:
      jobs = fromdb
    else:
      jobs = get_jobs(word)
      db[word] = jobs
  else: 
    return redirect('/')
  return render_template("report.html",searchingBy = word, resultsNumber=len(jobs))
```

# 4.6 Rendering Jobs!

CSS : Grid

Flask {{value}} , {% for a in as%}

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Job Search</title>
    <style>
      section{
        display:grid;
        gap:20px;
        grid-template-columns:repeat(4,1fr);
      }
    </style>
  </head>
  <body>
   <h1>Search Results</h1>
   <h3>Found {{resultsNumber}} results for : {{searchingBy}} </h3>

    <section>
      <h4>title</h4>
      <h4>company</h4>
      <h4>location</h4>
      <h4>link</h4>
      {% for job in jobs %}
        <span>{{job.title}}</span>
        <span>{{job.company}}</span>
        <span>{{job.location}}</span>
        <a href = "{{job.link}}" target="_blank">Apply</a>
      {% endfor %}
    </section>
  </body>
</html>
```
