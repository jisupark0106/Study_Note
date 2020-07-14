# 1.4 Creating a Your First Python Function

```python
//define function
//{x} , tab-indentation
def say_hello():
	print("hello")
print("bye")
//print("bye") is not say_hello()

// call say_hello()
say_hello()

```

# 1.5 Function Arguments

```python
//argument
def say_hello(who)
	print("hello",who)

//whatever you want you can send arguments
say_hello("jisu")
say_hello(True)

def add(a,b):
	print(a+b)

//default value setting value = 4
def sub(a,b=0):
	print(a-b)

add(2,3)
sub(3,4)
```

# 1.6 Returns

positioned arguments

```python
def p_plus(a,b):
	print(a+b)
//you care about results of the function
//return means the end of the function
def plus(a,b):
	return a+b

//r_result has a return value
//p_plus just print value, not store a value
p_result = p_plus(2,3)
r_result = plus(2,3)

print(p_result,r_result)

```

# 1.7 Keyworded Arguments

```python
//we don't care about value's position
def plus(a,b):
	return a+b

result = plus(b=30,a=1)

def say_hello(name, age):
	return f"hello {name} you are {age} yaars old"
// return "hello"+name+"you are "+age +"years old"

say_hello("jisu","25")
hello = say_hello(name ="jisu", age="25")
print(hello)
```
