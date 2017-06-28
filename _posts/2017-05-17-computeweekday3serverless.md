---
layout: post
title: "AWS Compute Week, Day 3: Serverless Day "
tag: [AWS]
category: [Cloud]
---
### Building Serverless Web Applications ?Randall Hunt
Technical Evangelist at AWS, of SpaceX and NASA
randhunt@amazon.com
@jrhunt on twitter
Concepts, Design Patterns, Tooling, Demo
AWS Lambda
No servers to provision or manage
Scales with Usage
Never pay for idle
Availability and fault tolerance built in
60TB/s throughput between S3 and Lambda
Never pay for Idle (GB/s)
Event driven, continuous Scaling
Function versioning and aliases
Versions = immutable copies of code+configurations
Aliases=mutable pointers to versons
Lambda Environment Variables
Key-Value pairs
Available via standard env variables, such as process.env or os.environ
Can be encrypted via AWS KMS
Web Applications, Backends, Data Processing, Chatbots, Amazon Alexa,
Amazon API Gateway Concepts
API gateway Variables
Sam : Serverless Application Model (helps define entire Serverless application)
is lot easier then cloud formation template
Framework is zappa for python is best

### Serverless Apps with AWS Step Functions
Trevor Roberts Jr, Solutions architect
Modern Serverless Apps -> Lambda functions
Take discrete units of work and doing them well and packing them into lambda functions
12 factor application
AWS step functions: Application Lifecycle
Json defined, Visualize in console, Monitor Execution
Seven State types: Task, Choice, Parallel, Wait, Fail, Succeed, Pass