---
layout: post
title: "Intro to Hadoop, Yarn, and HDFS"
tag: [Hadoop]
category: Big Data
---
Hadoop is an open source framework that you can install on a cluster so they can communicate and work together to store and process large amounts of data.

YARN is a Resource Manager. It tracks the availability of live nodes and resources and coordinates which tasks from which clients get what resources when.

Hadoop uses HDFS, the Hadoop Distributed File System. It uses a master/slave architecture where a single NameNode manages the file system Metadata, and one or more slave DataNodes actually store the data. A file is split into blocks and these blocks are then stored in a set of DataNodes. The NameNode maps the data, the DataNodes deal with the read write, block creation, deletion, and replication.

How does Hadoop work?

Step 1: Submit a job to Hadoop by specifying location of input and output files, the map and reduce functions, and the job configureation parameters.

Step 2: Hadoop submits the job to the Jobtracker, which distrubtes them to the slave nodes and deals with monitoring and scheduling.

Step 3: The tasktrackers execute the MapReduce and store the output of the reduce in the right places.
