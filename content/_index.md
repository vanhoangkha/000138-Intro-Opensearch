---
title : "Serverless - Integrate AWS OpenSearch with a DynamoDB Stream"
date: 2024-01-01
weight : 1 
chapter : false
---
# Serverless - Integrate AWS OpenSearch with a DynamoDB Stream

#### Overview

In the workshop 6 of this series, we will build the search feature for our application with Amazon OpenSearch integrated with DynamoDB stream.

The architecture of the web application:
![SeverlessExample](/images/serverless-diagram.png?featherlight=false&width=50pc)

We will create a new Lambda function to load streaming data from DynamoDB with the OpenSearch instance and a function to search for files in the OpenSearch instance. And we will also create an API for interactive search with the Lambda function.

#### Amazon OpenSearch
Amazon OpenSearch Service is a managed service that makes it easy for you to perform interactive log analytics, real-time application monitoring, website search, and more. OpenSearch is an open source, distributed search and analytics suite derived from Elasticsearch. Amazon OpenSearch Service offers the latest versions of OpenSearch, support for 19 versions of Elasticsearch (1.5 to 7.10 versions), as well as visualization capabilities powered by OpenSearch Dashboards and Kibana (1.5 to 7.10 versions).

Amazon OpenSearch Service manages the work involved in setting up a domain, from provisioning infrastructure capacity in the network environment you request to installing the OpenSearch or Elasticsearch software. Once your domain is running, Amazon OpenSearch Service automates common administrative tasks, such as performing backups, monitoring instances and patching software

Features of Amazon OpenSearch Service:
- **Scale**: Numerous configurations of CPU, memory, and storage capacity known as instance types, including cost-effective Graviton instances.
- **Security**: AWS Identity and Access Management (IAM) access control, easy integration with Amazon VPC and VPC security groups, encryption of data at rest and node-to-node encryption.
- **Stability**: Numerous geographical locations for your resources, Multi-AZ, dedicated master nodes to offload cluster management tasks, automated snapshots to back up and restore OpenSearch Service domains
- **Flexibility**: SQL support for integration with business intelligence (BI) applications, custom packages to improve search results
- **Integration with popular services**: Integration with Amazon CloudWatch for monitoring OpenSearch Service domain metrics and setting alarms, AWS CloudTrail for auditing configuration API calls to OpenSearch Service domains, Amazon S3, Amazon Kinesis, and Amazon DynamoDB for loading streaming data into OpenSearch Service,...

#### DynamoDB Stream
DynamoDB Streams captures a time-ordered sequence of item-level modifications in any DynamoDB table and stores this information in a log for up to 24 hours. Applications can access this log and view the data items as they appeared before and after they were modified, in near-real time.

A DynamoDB stream is an ordered flow of information about changes to items in a DynamoDB table. When you enable a stream on a table, DynamoDB captures information about every modification to data items in the table. Whenever an application creates, updates, or deletes items in the table, DynamoDB Streams writes a stream record with the primary key attributes of the items that were modified. A stream record contains information about a data modification to a single item in a DynamoDB table

#### Content

 1. [Preparation](1-preparation/)
 2. [Create API and Lambda Functions](2-create-api-and-lambda-functions/)
 3. [Create OpenSearch Instance](3-create-opensearch-instance/)
 4. [Test web operation](4-test-operation/)
 5. [Cleanup](5-cleanup)
