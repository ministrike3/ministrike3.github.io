---
layout: post
title: "AWS: IAM policy"
tag: [AWS]
category: [Cloud]
---
Today at work, I wanted to set up an EC2 instance->S3 bucket connection, but ensure that the S3 bucket is as locked down as possible. I also only wanted specific s3 commands to be allowed in my EC2 instance.

I had to learn what an IAM policy is, how it works, and how to write my own.

***

What is an IAM policy?

A set of RULES that, under the correct conditions, define what ACTIONS the policy PRINCIPAL or holder can take to specified AWS RESOURCES.

This boils down to "Who can do what to which resources. When do we care?"

***

IAM roles allow you to delegate access with defined permissions to trusted entities without having to share long-term access keys.

Lets look at one I wrote here:

{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:ListBucket",
                "s3:GetBucketLocation",
                "s3:ListBucketMultipartUploads"
            ],
            "Resource": "arn:aws:s3:::neilcomputing",
            "Condition": {}
        },
        {
            "Effect": "Allow",
            "Action": [
                "s3:GetObject",
                "s3:GetObjectAcl",
                "s3:PutObject",
                "s3:PutObjectAcl"
            ],
            "Resource": "arn:aws:s3:::neilcomputing/*",
            "Condition": {}
        }
    ]
}

Version: There's only two versions - 2012-10-17 and 2008-10-17; use the newer one!
Statement: The important part. Who does what to what resources when

Statements contain :
Effect: Either Allow or Deny (the following actions)
Principal: Who is doing this stuff? In the above statement, I have no principle because I was writing a role to assign to various EC2 instances (IE if you attach the role to it the principle is itself). Specify the ARN.
Action:What actions are in this list? In my case, various List, Get, and Put operations
Resource: What does it do these actions too?
Condition: This policy should run if _ is true (mine is blank because I want it always on)

***

To learn what an IAM role is, this blog post was incredibly helpful:

http://start.jcolemorrison.com/aws-iam-policies-in-a-nutshell/
