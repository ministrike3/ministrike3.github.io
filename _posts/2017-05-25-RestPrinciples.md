---
layout: post
title: "Rest Principles"
tag: [Web, REST]
category: [Web] 
---
### What is a REST API?
A way of thinking about how a web server responds to your requests
It doesn't just respond with data, it responds with resources

Resource? Think about it as OOP and each server as having resources that interact with the request

For example, GET/POST/PUT/DELETE   /item/chair
its the chair in the item resource and our requests interact with it in different ways

***

REST is supposed to be stateless:

One request cannot depend on any other request
For example, logging into a website is not remembered (stateless) so the application must send enough information in every request to identify the user

***

Use Json:
essentially a dictionary, or more technically a string of a dictionary

***

Test First API Design:

Design the endpoints first
Lets you make design decisions first, like name or ID, etc.
Figure out what you actually need for your API
