# 1.9 Conditionals part One

```python
def plus(a,b):
	if type(a) is int or type(b) is float:
		return a+b
	else:
		return None

plus(12,4)
plus(12,"hello")

```

# 1.10 if else and or

```python
def age_check(age):
	print(f"you are {age}years old")
	if age <= 18:
		print("you cant drink")
# elif - else if
	elif age == 18:
		print("you are new to this")
	# and &&
  elif age>20 and age<25:
		print("you are still kind of young")
	else : 
		print("enjoy your drink")

age_check(23)
age_check(29)
age_check(17)
```

# 1.11 for in

```python
# for loops 
days = ("mon","tue","wed","thur","fri")

for day in days:
	print(day)

# break
for day in days:
	if day is "wed":
		break
	else : 
		print(day)

# print letter
for letter in "hello"
	print(letter)
```
