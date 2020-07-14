[The Python Standard Library - Python 3.8.4rc1 documentation](https://docs.python.org/3/library/index.html)

# 1.0 Data Types of Python

```python
//variable -- number
a = 2
b = 3
print(a+b)

//variable -- string ('') ,(" ")
a = 'like this'
b = 3
print (a + b)

//varible -- boolean (True = 1, False = 0)
c= True
d = False

//variable -- float 
a_float = 3.12

//print type 
print(type(a_float))

//empty --- None (only python have)
//null or undefined same role
a_none = None 

//variable name 
//-- super_long_variable (python)
//superLongVariable -- javascript

```

# 1.1 Lists in Python

```python
//days = "mon,tue,wed,thur,fri"
//day_one = "mon"

//list
days = ["Mon","tue","wed","thur"]
print(type(days)) 

print("Mon" in days)
//library 보고 참고해보기

print(days[3])
print(len(days))

days.append("fri")
print(days)

```

# 1.2 Tuples and Dicts

```python
//mutable vs immutable
//list is mutable , tuple is immutable

//nobody can change tuple
days = ("mon","tue","wed","thur")

//dictionary [key-value]
name = "Jisu"
age = 25
Korean  = True
fav_food =["sushi","samgyop"]

jisu = {
	"name" : "Jisu",
	"age" : 25,
	"Korean"  : True,
	"fav_food' : ["sushi","samgyop"]
}
print(jisu["fav_food"])
jisu["women"] = True

```

# 1.3 Built in Functions

```python
//function is an action

print("adada")
print(len("dfkjklskdjlkfj"))

//turn types
int()
bool()
str()
float()

//example -- turn types
age = "18"
n_age = int(age)

```

'
