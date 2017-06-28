---
layout: post
title: "AWS Compute Week, Day 2: Docker "
tag: [AWS]
category: [Cloud]
---
### Docker With ECS (Elastic Container Service)

Why containers?
OS virtualization, Process Isolation, Images, Automation
Portable Flexible Fast Efficient
Hard to switch over to batch jobs unless you have a cluster manager
Amazon ECS is a cluster management tool
Mix and match the different EC2 instances for your different container images
ECS scheduling will do everything for you
Optimistic, and strict scheduling
Optimistic tries to reserve, if fails, then fail
Other waits for completion before it works // block it out
No built in queue in ECS
Fully managed elastic service
Shared state optimistic scheduling
Deep integration with other AWS services
Load balancing, block storage, etc. etc.
Routing via Application Load balancer
Path based routing
Dynamic port mapping
HTTP/2
WebSockets
Detailed Logging
Task Definition



### Deep Dive on microservices and Docker/Containers
Microservices Architecture, ECS, Placement, and 12factor App
What is a microservice?
Small independent stateless process communicating with API?s. Small and focused on doing a small task which lets you have a modular approach to system building
Monolithic vs Microservices
Build it all inside a package and put it on a webserver  (but makes it hard for new features or bugs)
Make a change in the singular service you need
Black boxed

1Codebase
2Dependencies
3Config
4Backing Services
5Build,Release Run
6Processes
7 Port Binding
8 Concurrencies
9 Disposability
10 Dev/Prod parity
11 Logs
12Admin Processes

### Container Orchestration with Amazon ECS & Blox
New Cluster Query Language         
Lot of different things to filter by
Deep Dives on CI/CD and Docker
What is CI/CD,using Docker and ECS/ECR for this
Deployment strategies
Frequncies reduce difficultiy
Consistency improves confidence
Automation over toil
Empowered developers make happier teams
Smaller batch sizes are easier to debug
Faster delivery improves software development practices
Version control, branching, code review,
Compilation, unit tests, static analysis, packaging
Integration tests, load tests, security tests, acceptance test
Deployment, monitoring, measuring, validation