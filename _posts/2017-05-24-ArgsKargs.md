---
layout: post
title: "Python: What are *args and **kwargs?"
tag: [Python]
category: [Python,Learning] 
---
### *args is something you pass into a function when it might be a variable number of inputs:

for example, the following function only works for 2 variables:

def sum(a,b):
    return(a+b)

what if you want more variables?

def sum(*args):
    sum=0
    for number in args:
        sum+=number
    return(sum)

^^The above function will add any number of inputted variables together

A real example:

def my_three(a, b, c):
    print(a, b, c)
a = [1,2,3]
# here list is broken into three elements
my_three(*a)

***

### **kwargs allows us to pass variable number of keyword arguments:

def my_func(**kwargs):
    for i, j in kwargs.items():
        print(i, j)

my_func(name='neil', language='python', year=2)

language python
year 2
name neil