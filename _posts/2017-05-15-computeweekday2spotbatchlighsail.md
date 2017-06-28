---
layout: post
title: "AWS Compute Week, Day 1: Spot, Batch, and Lightsail"
tag: [AWS]
category: [Cloud]
---

### Introduction to Spot

Learn about Spot and best practices
customer examples
Tools and partners to help manage spot instances
See a demo
Bid for unused EC2 capacity lying around in data centers
AWS has millions of customers; 2300 government agencies, 7k schools, 22k nonprofit
Spot market is a real time market where the price changes based on supply and demand
Never pay more then what you bid; if price goes higher then that, you get 2 minutes
Applications should be as stateless as possible
Pick a bunch of types and zones and etc. etc. for more uptime
21 percent run < 1 hour 
35 percent < 2 hours 
40  percent < 3 hours 
50 percent < less then 6 hours
spot blocks : only get a spot instance if you can have for dedicated number of hours
spot fleet: get lots of different kinds of spot instances
EC2 Spot Console
EC2 Spot Bid advisor
EC2 Spot Labs on Github : Python scripts that do cool things
How is market price set? Amazon sets it based on availability and bidding

### AWS batch

Batch computing, overview, use cases, Demo, Q&A
Execute a bunch of programs on a bunch of inputs
2007 NYT processed 130 years in 36 hours for 900 dollars in 2007 ; 11 million articles and 4TB
Scale it
Job: Unit of work executed by AWS batch as containerized application running on Amazon EC2; reference container, command parameters, or .zip(run the .zip on amazon linux container)
Array jobs: Coming soon; run many copies of an application against an array of elements
Job definitions: how to run the jobs; mount points etc. etc.
Job queue: where job lives until assigned to compute environment
Compute environment: the EC2 instances these jobs are going to run on managed(they do) unmanaged (you take care of the EC2)
Job states: submitted (in queue), pending( waiting on dependencies), runnable(Ready to run), starting (your job is in process of being scheduled), succeeded, failed,

### Introduction to AWS Lightsail
Everything you need for a low predictable price
Mem, processor, SSD, Transfer (prorated as well)
Launch a VPS with a single click
Pick your own preconfigured images with the stacks installed and applications
