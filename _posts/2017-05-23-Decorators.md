---
layout: post
title: "Python: What is a Decorator? "
tag: [Python]
category: [Python,Learning] 
---
I was working on some python stuff when I stumbled upon the term decorator; not knowing what it was, a quick google search led to a relatively confusing explanation of what I believe to be a simple idea.

A decorator is simply a function that extends another function. As in, it executes that original function, but also does more. Take the function below:

def print_my_name:
    print("Neil Patel")

Now take this decorator below:

def my_decorator(some_function):
    def wrapper():
        print("Something is happening before some_function() is called.")
        some_function()
        print("Something is happening after some_function() is called.")
    return(wrapper)

If we were to execute this line of code:

my_decorator(print_my_name)

This is what would happen:

Something is happening before some_function() is called.
Neil Patel
Something is happening after some_function() is called.

***

You can call a decorator on a function using the @ sign! Take a look at the timing function below:

import time
def timing_function(some_function):
    def wrapper():
        t1 = time.time()
        some_function()
        t2 = time.time()
        return "Time it took to run the function: " + str((t2 - t1)) + "\n"
    return(wrapper)

@timing_function
def my_function():
    num_list = []
    for num in (range(0, 10000)):
        num_list.append(num)
    print("\nSum of all the numbers: " + str((sum(num_list))))

print(my_function())


basically, what the @timing_function line does is say : my_function=timing_function(my_function)!