---
title: "re:Invent 2020 level up"
date: 2021-01-31
---

# Table of Content

# Objective

Last year, re:Invent 2020 saw lots of new features/services being released. This blog helps to highlight a few of them
that is especially interesting for me

# Highlights

## Analytics

### AWS Glue Elastic Views

#### Challenge

Challenges customers face when attempting to combine and replicate data across multiple data stores. As a result, many
developers use ETL (extract, transform, and load) tools to build complex data integration pipelines

#### Solution

1. Customers can use SQL to create materialized views.
2. AWS Glue Elastic Views copies data automatically from each source data store to a target data store.
3. The service also keeps the data in the target data store updated automatically.•Customers don’t have to manage
   servers.

### Amazon QuickSight Q

#### Challenge

Business users rely on the business intelligence (BI) team to interpret the business question, develop metrics, insights
& dashboards.

#### Solution

Amazon QuickSight Q empowers business users and analysts to ask questions about their data using business language and
get answers in seconds. Amazon QuickSight Q adds natural language query (NLQ) capability to Amazon QuickSight. Unlike
conventional NLQ-based BI tools, Q is powered by machine learning (ML) to automatically understand the meaning and
relationships of your data across multiple data sources. Q uses this information to extract business terminologies such
as revenue, growth rate, turn over et al. and builds intelligent indexes to answers your business questions.

### Amazon Redshift AQUA

Amazon Redshift AQUA is a new distributed and hardware-accelerated cache that enables Redshift queries to run up to 10x
faster than other cloud data warehouses. Existing data warehousing architectures with centralized storage require data
be moved to compute clusters for processing. As data warehouses continue to grow over the next few years, the network
bandwidth needed to move all this data becomes a bottleneck on query performance.

### Amazon EMR on EKS

Amazon EMR on Amazon EKS adds a new deployment model to Amazon EMR that allows customers to run Apache Spark onAmazon
Elastic Kubernetes Service (Amazon EKS). It gives customers an easy and cost-effective way to process vast amounts of
data without the need to provision their own EC2 or container resources. With Amazon EMR on Amazon EKS, customers can
reuse existing EC2 instances or their shared EKS clusters and reduce EMR job startup times by eliminating the need to
create a new cluster of EC2 instances dedicated for analytics. For a more serverless Spark approach customers can also
deploy jobs to Fargate containers managed by EKS, which further leads to reducing management overhead.

## Builder experience

## Communication Apps

## Compute

## Container

## Databases

## Geospatial

## IOT

## Machine Learning

### Sagemaker Jumpstart

Sagemaker Jumpstart makes it extremely easy for experienced practitioners and beginners alike to quickly deploy and
evaluate models and solutions, saving days or even weeks of work.SageMaker JumpStart provides a set of solutions for the
most common use cases, such as fraud detection, predictive maintenance, and demand forecasting, that can be deployed
readily with just a few clicks. The solutions are fully customizable and come with AWS CloudFormation templates and
reference architectures that allow you to easily deploy them in your own environment, thus accelerating your ML journey.
SageMaker JumpStart also provides one-click deployment and fine-tuning of more than 150 pre-trained models from popular
model zoos, including PyTorch Hub and TensorFlow Hub. One-click deployment and fine-tuning features are available for
natural language processing, object detection, and image classification models, so you can minimize the time to deploy
open source models for your own use case. In addition, sample noteboks are provided for SageMaker built-in algorithms
that you can quickly adapt to your own datasets and use cases.

## Management and governance

## Mobile

## Networking

## Outpost

## SAAS

## Security

## Serverless

### Cloudwatch Lambda Insights

CloudWatch Lambda Insights is a monitoring and troubleshooting solution for serverless applications running on AWS
Lambda. The solution collects, aggregates, and summarizes system-level metrics including CPU time, memory, disk, and
network. It also collects, aggregates, and summarizes diagnostic information such as cold starts and Lambda worker
shutdowns to help you isolate issues with your Lambda functions and resolve them quickly.

### AWS Amplify Admin UI

AWS Amplify is a set of products and tools that enable mobile and front-end web developers to build and deploy secure,
scalable full-stack applications, powered by AWS. Amplify supports developers with client Libraries, code generation,
and deployment, hosting, and management of web and mobile applications.AWS Amplify now has an Admin UI that lets
developers create new cloud backends for their apps with a visual data modeler. You can now create data types,
relationships, and security rules that are backed by AWS AppSync GraphQL APIs. Amplify Projects can now be designed and
deployed from the Admin UI. Projects built in the Admin UI can be exported to developer client workstations, and
integrated with Amplify Client-based applications.Previously, Amplify Projects had to be created using the Amplify CLI
running on a workstation. Now, customers have a web-based console to visually design and manage their cloud backends
that works seamlessly with Amplify-based mobile or web application clients. This makes the power, security, and
scalability of AWS even more accessible for application developers

### Amazon VPC

Amazon VPC Reachability Analyzer is a new feature that enables you to perform connectivity testing between resources in
your virtual private clouds (VPC). With Reachability Analyzer, you can quickly troubleshoot connectivity issues caused
by misconfiguration, and proactively verify that your configuration matches your network connectivity intent. You can
run a reachability analysis between Elastic Network Interfaces (ENIs) in the same VPC or across two VPCs connected
through a peering connection. You can also run a reachability analysis between ENIs and gateways, including internet
gateways, virtual private gateways, and transit gateways. When the destination is not reachable, Reachability Analyzer
will identify the blocking configuration setting, such as a missing security group rule or routing table entry.Instance
Level Network Performance Metrics. Amazon EC2 now provides additional network performance metrics to help customers gain
more insights into instance network performance. Five new metrics provide customers visibility when their instances
exceed network allowances defined by AWS. This visibility helps you proactively resolve application performance issues
and right size your instance fleets based on your desired network performance. The new metrics inform customers in real
time if network traffic is impacted when instance allowances for inbound and outbound bandwidth, packets-per-second (
PPS), connections tracked and PPS to link-local services are exceeded. Utilizing these metrics, customers can quickly
troubleshoot application performance issues related to exceeded allowances and proactively scale-up their instance
fleets to accommodate a surge in network traffic. These metrics will also help customers’ right size their EC2 instances
from network standpoint allowing them to run benchmark tests before production deployment

### Audit Manager

AWS Audit Manager enables you to continuously audit your AWS usage, simplifying the assessment of risk and compliance
with regulations and industry standards. Audit Manager automates evidence collection to reduce the “all hands-on deck”
manual effort that often occurs during audits and enables you to scale your audit capability in the cloud as your
business grows. Audit Manager, simplifies the assessment of policies, procedures, and activities – also known as
controls – to ensure they are operating effectively. When it is time for an audit, AWS Audit Manager helps you manage
stakeholder reviews of your controls and enables you to build audit-ready reports while minimizing manual efforts. AWS
Audit Manager currently provides 13 prebuilt frameworks help translate evidence from cloud services into
auditor-friendly reports by mapping your AWS resources to the appropriate requirements, industry standards or
regulations, including as CIS AWS Foundations Benchmark, the General Data Protection Regulation (GDPR), and the Payment
Card Industry Data Security Standard (PCI DSS). You can also fully customize a framework and its controls for your
unique business requirements. Based on the framework you select, Audit Manager launches an assessment that continuously
collects and organizes relevant evidence from your AWS accounts and resources, including resource configuration
snapshots, user activity, and compliance check results.

### Serverless Larger functions and AVX2 Support

AWS Lambda is a serverless compute service that lets you run code without managing servers. With Lambda you can write
and run code in your favorite programming language. You simply choose the memory allocation required and Lambda
automatically allocates other resources on your behalf (cpu, network, io). There are over 140 services that can trigger
Lambda functions or you can invoke them yourself.AWS Lambda now supports memory configurations up to 10GB (previously
3GB) and proportionally allocates up to 6 vCPUs (previously 2 vCPUs). This enables customers to run larger workloads,
process bigger assets, and use more CPU in parallel. In addition, Lambda now supports Advanced Vector Extensions (AVX2).
This allows increased CPU performance for tasks such as AI/ML, media processing, scientific compute, or other CPU
intensive tasks.Previously, customers have architected multiple tech stacks accommodate these compute limitations with
Lambda. With these enhancements, customers will benefit from improved performance, enablement of more workloads, and
simplified architectures. All of these are available to all customers at no additional cost and improve the TCO for
Lambda.

### 1ms billing for AWS lambda

AWS Lambda is a serverless compute service that lets you run code without managing servers. With Lambda you can write
and run code in your favorite programming language. You simply choose the memory allocation required and Lambda
automatically allocates other resources on your behalf (cpu, network, io). There are over 140 services that can trigger
Lambda functions or you can invoke them yourself.Lambda now bills in 1 ms increments with no minimums. Previously,
customers were billed in 100 ms increments. This allows customers to realize immediate cost savings on most Lambda
functions and to obtain more cost savings through code and configuration optimization. This change affects on-demand
Lambda functions and Lambda functions that use Provisioned Concurrency.Before this change, a Lambda function that ran
for 99 ms or less would result in a 100 ms charge to the customer. Customers were not encouraged to invest any time in
optimization because, while there would be performance benefit for the effort, there would be no cost benefit. This
change enables customers to realize cost and performance benefits with their optimization efforts.

### Lambda Support for Container Images

AWS Lambda is a serverless compute service that lets you run code without managing servers. With Lambda you can write
and run code in your favorite programming language. You simply choose the memory allocation required and Lambda
automatically allocates other resources on your behalf (cpu, network, io). There are over 140 services that can trigger
Lambda functions or you can invoke them yourself.AWS Lambda supports packaging and deploying functions as container
images, making it easy for customers to build Lambda based applications by using familiar container tooling, workflows,
and dependencies. Customers also benefit from the operational simplicity, automatic scaling – sub-second startup times -
high availability, native integrations with 140 services, and pay for use model offered by AWS Lambda. Enterprise
customers can use a consistent set of tools with both their Lambda and containerized applications for central governance
requirements such as security scanning and image signing. Customers can create their container images by starting with
either AWS Lambda provided base images or by using one of their preferred community or private enterprise images.Just
like functions packaged as ZIP archives, functions deployed as container images will benefit from AWS Lambda’s
operational simplicity, automatic scaling with sub-second startup times, high availability, and native integrations with
140 AWS services. Customers can continue to use all Lambda features, such as Extensions, Telemetry APIs. Lambda Layers
and code signing are not applicable to the support for container images.Lambda support for container images allows for
images based on Linux, such as Alpine or Debian, and AWS provides base images for Lambda, such as Python3.8, NodeJS
10.x, NodeJS 12.x, .NetCore 2.1, Java 8 and 11, Ruby 2.5, and Golang. Lambda support for container images allows up to a
10GB image size for container images.Additionally, we have open sourced both the Lambda Runtime Interface Client (RIC)
and Runtime Interface Emulator (RIE). These components provide customers the ability to perform local testing on
functions packaged for container support. The RIC includes additional functionality allowing customers to extend their
preferred base images and making them Lambda compatible.Customers can continue to use their current Lambda function
deployment processes, such as creating ZIP archives and developing and deploying in the console. There is no change to
these processes.

## Storage

### EBS adds tiered pricing and faster io2 volumes

Building on the success of the io2 launch in August 2020, EBS continues to increase performance, throughput, and volume
size and still lower prices. AWS introduced a preview of its next generation storage platform io2 Block Express. Block
Express delivers 4x higher throughput, IOPS, and capacity than io2 volumes, along with sub-millisecond latency and
maintains the greater 99.999% durability. Additionally, EBS io2 volumes offer a tiered pricing model reducing the cost
of provisioning peak IOPS by 15%.

### EBS gives customers more choices and lowers costs for Block Storage

EBS GP3 volumes allow customers to provision volumes for IOPS, capacity and throughput independently. Customers that
need medium range IOPS (3,000-16,000) no longer have to pay for more capacity than they need. A 200 GB volume can be
provisioned with up 16,000 IOPS. This allows customers to build exactly the configurations they need forcing them to
over-provision in order to get performance. These configurations often result in massive cost savings to the customer.At
Storage Day in Nov 2020 the EBS team also slashed prices on SC1 by 40% creating a block storage tier with a $.015/GB
price point

### S3 Strong Consistency

Service Details – S3 now provides Strong Read-After-Write consistency for all S3 operations. This is a huge change from
S3 Eventual Consistency that S3 provided since it’s launch in 2006. All S3 GET, PUT, and LIST operations, as well as
operations that change object tags, ACLs, or metadata, are now strongly consistent. What you write is what you will
read, and the results of a LIST will be an accurate reflection of what’s in the bucket. This applies to all existing
andnew S3 objects, works in all regions, and is available at no extra charge! There’s no impact on performance, you can
update an object hundreds of times per second if you’d like, and there are no global dependencies.

