---
layout: post
title: "AWS: No-AWS Knowledge Quick Interview Prep"
tag: [AWS]
category: [Cloud]
---


AWS:

EC2 ?> Cloud Server
S3 ?> Cloud Storage, can support a static website
Glacier ?> Archived storage (way cheaper)
AWS Elastic Beanstock ?> Web App

DynamoDB ?> NOSQL
RDS ?> Relational DQ
Redshift ?> Petabyte scale data warehouse solution

Hive +EMR in S3 ?> Analyzing Big Data


Python SDK for AWS ?> Boto3 ?	has Object oriented API; also allows for low-level direct access 
	Provides access for just about everything
	Client API ?> Low level direct access (1-1 HTTP API)
	Resource API ?> provide resource objects and collections to access attributes 		and perform actions
	Python 2 and 3 support
	has waiters to check for ready status of spun-up instances before executing 			anything
	has service specific features like automatic multi-part transfers for S3 and 			simplified query conditions for Amazon DynamoDB

Chalice : Python Serverless Microframework for AWS
	Quickly create and deploy applications that use Amazon API gateway and AWS 			lambda?	Not yet in production, do not have access to entire feature set

