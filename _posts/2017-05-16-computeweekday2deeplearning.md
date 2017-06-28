---
layout: post
title: "AWS Compute Week, Day 2: Deep Learning Workshop Introduction "
tag: [AWS]
category: [Cloud]
---
### Deploy a Deep Learning Framework on amazon ECS and EC2 Spot Instances
Introduce MXnet
Containers
Overview of ECS and ECR
Overview of AWS CloudFormation
Overview of EC2 Spot Instances
ECS and EC2 Spot Instances Together
Hands-on, Self paced workshop

What is MX net ?open source deep learning framework
Define train and deploy deep neural networks. Highly scalable, multihost, cpu/gpu

Why containers? Increase infrastructure utilization, environment isolation and fidelity, run diverse applications on shared hardware, changes are tracked, easy to deploy. Increase portability, and flexibility, speed and efficiency.

ECR is EC2 container registry that you use to store your docker images
It becomes a task definition and then reference an ECR container in the task

AWS Cloudformation
Great for infrastructure as Code. USE JSON or Yaml files as templates, make a service and build the stack
Stack replication and infrastructure scale out

Workshop: Image classification
Lab 1: Setup the workshop environment on AWS
Lab 2: Build an MXNet Docker Image
Lab 3: Launch MXnet with ECS
Lab 4: Image classification Demo
Lab 5: Wrap Image Classification in an ECS Task