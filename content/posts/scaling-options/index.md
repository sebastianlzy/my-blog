---
title: Scaling options
date: 2020-12-15
description: Questions to ask before adopting microservices or adding horizontal scaling 
tags:
  - Adopting microservices
  - Scaling options

---

## Scaling web application
Scalability is the ability to handle increased workload by repeatedly applying a cost effective strategy for extending a system’s capacity

### Scaling options
#### Horizontal vs vertical scaling
 
1. Horizontal scaling means scaling by adding more machines to your pool of resources (also described as “scaling out”)
2. Vertical scaling refers to scaling by adding more power (e.g. CPU, RAM) to an existing machine (also described as “scaling up”).

#### Questions to help understand the type of scaling required

1. Where are images and videos stored?
2. How many read/write request are recieved per second? per minute?
3. What is the level of security required?
4. Are these synchronous or asynchronous request?
5. Do you have any compliance requests? - Payment Card Industry Data Security Standard (PCI DSS)
6. How are you recording customer behavior data and fulfilling your analytics needs?
7. What are your load balancing considerations (scaling, caching, session maintenance) ?

### Step by step guide

#### Step 1: Ease server load - Leverage content delivery network (CDN)
Reduce server load by moving image and video to content delivery network (CDN). 
AWS provides Amazon Cloudfront as a CDN solution using more than 216 Points of presence to provide efficient caching. 
It also includes AWS shield to handle layer 3 & 4 DDoS attack

#### Step 2: Reduce read load - add read replica
Amazon Aurora provide up to 15 read replicas, which can span across region. 
As Amazon Aurora Replicas share the same data volume as the primary instance in the same AWS region, there is virtually no replication lag (typically 10s of millisecond)  

AWS RDS support up to 5 read replicas. For higher availability, AWS RDS can provide synchronous multi-AZ replication.

#### Step 3: Reduce write requests
Introduce queue to process asynchronous message. Amazon SQS is a highly scalable queue which can hold message until they are processed by your stack. You can implement a job-observer pattern
by setting up auto-scaling to automatically increase/decrease batch server depending on the number of SQS messages 

#### Step 4: Introduce a more robust caching engine
Use of Amazon Elastic Cache for Memcached/Redis to reduce write/read request. Use redis for more robust data persistence and complex data structure

#### Step 5: Scale your server
Vertical scaling is a great option until you are comfortable with concepts such as sharding and stateless. 
In most situation, a major architecture change is needed to enable horizontal scaling.

Alternatively, you can use Amazon managed services such as switching to Amazon Aurora Serverless or Lambda to help with variable workloads


### References
1. https://resources.sei.cmu.edu/asset_files/TechnicalNote/2006_004_001_14681.pdf
2. https://aws.amazon.com/blogs/architecture/scale-your-web-application-one-step-at-a-time/