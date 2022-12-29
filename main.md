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

## Booleans and Conditions

Booleans represent True or False

```python
print(1>2)
print(1<2)
```

Logical conditions in python:

* Equals: `a == b`
* Not Equals: `a != b`
* Less than: `a < b`
* Less than or equal to: `a <= b`
* Greater than: `a > b`
* Greater than or equal to: `a >= b`

```python
a = 2
b = 1

if b > a:
  print("b is greater than a")
else:
  print("b is not greater than a")
```

## Loops

You can use a while loop to execute a statement as long as the condition is true

```python
i = 1
while i < 10:
  print(i)
  i += 1
```

You can use a break to stop a loop

```python
i = 1
while i < 10:
  print(i)
  if i == 5:
    break
  i += 1
```

You can also use a for loop. It executes a statement for each item in a list

```python
my_list=["car","train","plane"]
for x in my_list:
    print(x)
```

To use the for loop an speficied number of times, you can use the `range()` function

```python
for x in range(10):
  print(x)
```

## Lists

We will pay more attention to lists as boto3 uses lists and dictionaries as most return types
Lists store multiple items on a single variable

```python
my_list=["car","train","plane"]
print(my_list)
```

List items are ordered, changeable, and allow duplicate values.

```python
my_list=["car","train","plane"]
print(my_list)
my_list=["car","train","plane","car"]
print(my_list)
```

The fist item of a list is [0]
[-1] is the last item of a list

```python
my_list=["car","train","plane"]
print(my_list[0])
print(my_list[1])
```

You can ask python the length of a list

```python
my_list=["car","train","plane"]
print(len(my_list))
```

You can check if an item exists on a list

```python
my_list=["car","train","plane"]
if "car" in my_list:
    print("Yes")
```

You can loop through a list

```python
my_list=["car","train","plane"]
for x in my_list:
    print(x)
```

## Dictionaries

Boto3 uses dictionaries extensively as well, so we will look better into them
Dictionaries are used to define key:value pairs

```python
my_dict={
    "brand":"Toyota"
    "model":"Corolla"
    "year":"1989"
}
```

You can access items by calling its key name

```python
my_dict={
    "brand":"Toyota"
    "model":"Corolla"
    "year":"1989"
}
x = my_dict['model']
```

You can loop through a dictionary in multiple ways:

Print "key" names:

```python
my_dict={
    "brand":"Toyota"
    "model":"Corolla"
    "year":"1989"
}
for x in my_dict:
    print(x)
```

Print "values"

```python
my_dict={
    "brand":"Toyota"
    "model":"Corolla"
    "year":"1989"
}
for x in my_dict:
    print(my_dict[x])
```

A dictionary can contain other dictionaries inside:

```python
myfamily = {
  "car1" : {
    "Brand" : "Toyota",
    "Name" : "Corolla"
  },
  "car2" : {
    "Brand" : "Nissan",
    "Name" : "Sentra"
  },
  "car3" : {
    "Brand" : "Honda",
    "Name" : "Civic"
  }
}
```

## Functions

A function is a piece of code that only runs when called
You define a function using the `def` keyword.

```python
def my_function():
    print('This is a function')
```

A function can take data in order to perform its functions. These are called parameters or arguments

```python
def add(a,b):
    print(a+b)
```

A function can return a data as a result of its code


```python
def add(a,b):
    result = a+b
    return result
```

## File Handling

You can use the `open()` function to open files in python
This function takes the filename and a mode as arguments.

* `r` - Read mode
* `a` - Append mode
* `w` - Write mode
* `x` - Create mode

```python
f = open("test.txt")
```

By default, python opens the file on read mode and as a text file

```python
f = open("test.txt", "rt")
```



