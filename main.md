# Python Basics

# Intro
In this course we will be learing some basic python concepts.
Why python? In our case it is already installed on our computers and it has simple syntax making it easier to write scripts.

## Basic Syntax 
Python uses indentation to define blocks of code

```python
if 1 < 2:
    print('True')
```

Python has two main ways of commenting:

```python
#single line comments
"""
multi line
comments
"""
```
## Variables in python
A variable in python is created when it's declared.
In python, variables do not need a type when they are declared and the type can be changed later.

```python
x = 'alonso'
y = 182
print(x)
print(y)
```

You can specify the type if you want to

```python
x=str(3)
x=int(3)
```

And you can also ask python to return the type of a variable

```python
x = 'alonso'
y = 182
print(type(x))
print(type(y))
```

Variables are case sensitive.

## Booleans

Booleans represent True or False

```python
print(1>2)
print(1<2)
```

```python
a = 2
b = 1

if b > a:
  print("b is greater than a")
else:
  print("b is not greater than a")
```

