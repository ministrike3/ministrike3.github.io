---
layout: post
title: "What Is MapReduce"
tag: [MapReduce, Hadoop]
category: Big Data
---

People make MapReduce seem a lot more complicated then it actually is.

MapReduce is a programming model (often implemented with Hadoop in your choice of programming language) that is used to process huge amounts of data.

***

#### It has 2 main phases, and a few additional steps.

The first step is some sort of data processing that assigns what data each Mapper is going to have inputted.

The next step is actually running the mapper function; a mapper essentially takes in an input and outputs some key-value pairs.

Third, we have the shuffle step, where all key-value pairs with the same keys are grouped together.

Fourth, each one of these different groups of key value pairs has Reduce() run on it, which will then output any number of key-value pairs.

***

A common example of map-reduce in the real world is it use it to count word frequencies. You break your input text into groups; then run map on these groups. This outputs each word as a key value pair <word,1>. Each key-value pair with the key word is then group together; Reduce is run on them to output <word,count>.  

The major benefit is the ability to run all your maps in parallel, and all your reduces in parallel (since every reduce is run on a single key), which can save time and better utilize compute resources (and allow scalibility.)
