---
title: "AWS Certified Developer Associate"
date: 2021-01-26
tags:
  - certification
  - aws developer associate
---
# Things to remember

## ALB

1. Access logs capture detailed information about requests sent to load balancer such as
   1. Time request was received
   2. Client's IP address
   3. Request paths
   4. Server response
2. Automatically encrypted using SSE-S3
3. No additional charge for access log, only charged for the storage cost for S3
4. Use Cognito Authentication via Cognito User Pools for ALB
5. HTTP error
   1. 503: service unavailable
   2. 504: gateway timeout
   3. 500 internal server error
   4. 403: forbidden
   5. 404: resource not found
   6. 429: throttle exception

## API gateway

1. Use API gateway mapping template to map payload from a method request to the corresponding integration request
2. Authorizers
   1. Lambda Authorizer
   2. Cognito User pool
   3. IAM permissions with sigv4

## Billing

1. Requires approximately 5 weeks of usage data to generate forecast
2. IAM user acces to the billing and cost management need to be activated once for all the users who need access by the account administrator

## Cloudformation

1. Template
   1. Description
   2. Metadata
   3. Parameters
      1. Does not allow the use of conditions
   4. Mappings
   5. Conditions
   6. Transform
      1. indicate it is a serverless application template
      2. AWS::Include to include template snippets stored in S3
   7. Resources
   8. Outputs
2. User data 
   1. run only during boot cycle
   2. Script enter as user data are executed with root user privillege
3. Exported output values in CF must have unique names within a single Region
4. Cross-stack reference
   1. Use export out field to flag value of VPC from network stack
   2. use `Fn::ImportValue` intrinsic function
5. Intrinsic function
   1. `!ImportValue` - return the value of an output exported by another stack
   2. `!Ref` - return the value of the specific parameter or resource
   3. `!GetAtt` - return the value of an attribute from a resource in the template
   4. `!Sub` - substitutes variables in an input string with values that you specify
6. Lambda resource
   1. Inline in CF by using AWS::Lambda::Function
   2. Upload code as zip to S3 and refer the object in `AWS::Lambda::Function`

## Compute

1. AWS account less than 12 months old can use a t2.micro for free within certain usage limits
2. Billed by second with a minimum of 60 seconds
3. Dedicated instances are EC2 that run in a VPC on hardware that is dedicated to a single customer
   1. However, it can share hardware with other instances from the same AWS account
4. Dedicated host is physical server and you will have the visibility and control over how instances are placed on the server

## Caching

1. Lazy loading: loads data into cache when necessary
2. Write through: adds data/update data in the cache whenever data is written to the database

## CodeBuild

1. Can run CodeBuild locally using CodeBuild Agent
2. Maximum number of build if 5 times the concurrent build limit
3. Build process will be automatically terminated post the expiry of the configured timeout
4. To encrypt build artifacts automatically,
   1. provide access to an AWS KMS
   2. specify a KMS key to use
   3. by default it uses AWS-managed CMK for Amazon S3 
5. Cache dependencies in S3

## Codepipeline

1. Setup CloudWatch Events rule that uses CodePipeline as event source with target lambda to send notifications for state changes

## Code commit

1. Data in CodeCommit repo is encrypted in transit and at rest

## Code deploy

1. Lifecycle 
   1. in place
      1. Before block traffic 
      2. Block traffic
      3. After Block traffic
   2. Standard flow
      1. ApplicationStop
      2. DownloadBundle
      3. BeforeInstall
      4. Install
      5. AfterINstall
      6.  ApplicationStart
      7.  Validate service
      8.  Before allow traffic
      9.  Allow traffic
      10. After allow traffic
   3.  BlueGreen
      11. Before block traffic 
      12. Block traffic
      13. After Block traffic
2.  Code deployment group
    1.  You can specify one or more deployment groups for a CodeDeploy application. The deployment group contains settings and configurations used during the deployment. Most deployment group settings depend on the compute platform used by your application. Some settings, such as rollbacks, triggers, and alarms can be configured for deployment groups for any compute platform.

## Cloudfront

1. Key pairs
   1. Cloudfront key pairs can only be created by root user
   2. use key pairs to create signed URL for private content

## Cloudwatch

1. Concepts
   1. Events: indicate a change in AWS environment; can also generate custom application-level events and publish them to Cloudwatch Events.
   2. Rules: A rule matches incoming events and route them to target
   3. Target: A target processes events
   4. A rule's target must be in the same region as the rule
2. Can create rules that self-trigger on an automated schedule in Cloudwatch Events using cron or rate expressions, min precision is 1 minute
3. Encryption
   1. Log group data is always encrypted in Cloudwatch Logs.
   2. Optionally use AWS KMS for encryption to be enabled at the log group level
   3. To associate a CMK with an existing log group, use `associate-kms-key`
4. Time interval
   1. Each data point covers 5 minutes that follow the start time of activity
   2. With detail monitoring, each data point cover the next minute of activity
5. Integrate with S3
   1. Export data from cloudwatch log group to S3 bucket


## DynamoDB

1. DAX is a fully managed, highly available, in-memory cache that deliver up to 10x performance improvement
2. Stream is a record contains informaiton about a data modification to a single item in a DynamoDB table
3. Transaction simplify the developer experience of making coordinated, all-or-nothing changes to multiple items
4. Provision write capacity for a global index should be equal or greater than the write capacity of the base table 
   1. Reason: new updates will write to both the base table and global secondary index otherwise, the write capacity will be throttled
5. LSI
   1. Maximum of 5 local secondary indexes per table
   2. Consume write and read capacity from base table
   3. Can fetch attribute that are not in the index
   4. Strong and eventual consistency
6. GSI
   1. Up to 20 GSI (default quota)
   2. Has its own provisioned throughput settings for read and write activity
   3. Does not fetch attributes that is not projected into index
   4. Eventual consistency only
7. Use parallel scan to improve scan operation

## Elastic Beanstalk

1. Deployment type
   1. Immutable (Blue/green deployment)
      1. Swap route 53 record of the 2 environment to redirect traffic to new version
   2. All at once - quickest 
   3. Rolling - avoid downtime and minimises reduced avaliability
   4. Rolling with additional batch - avoid any reduced availability
   5. Traffic splitting - canary testing
2. Creating resources
   1. Add resource to `.ebestensions/<settings>.config` folder
   2. Resource such as ElasticCache, RDS and load balancer (https)
3. Versions
   1. Removing older versions that are not used by elastic beanstalk with a Lifecycle policy
   2. Beanstalk delete old versions after creating new version, does not count the new version towards the maximum number of versions defined in the policy
4. Platform
   1. Multi-container platform: run multiple containers on each instance. Uses ECS to coordinate container deployment to multi-container docker environment
   2. Single-container platform: run a single container on each instance, includes an Nginx proxy server
   3. Custom platform: allows you to develop an entirely new platform from scratch, customizing the operating system, additional software, and scripts that Elastic Beanstalk runs on platform instances. Allows you to build a platform for an application that uses a language/infrastructure software which beanstalk doesnt provide a managed platform
5. Worker environment
   1. Use a cron.yaml to define the cron jobs and do repetitive tasks
6. create multiple environment
   1. Elastic beanstalk makes it easy to create new environment for application, "dev", "prod", "load test"


## ECS

1. Putting multiple containers into the same task 
   1. Enable containers to share a common lifecycle
   2. Containers can share resources
   3. Share data volumes
2. Deploying X-ray traces
   1. with Fargate
      1. Provide the correct IAM role to the container
      2. Deploy the X-Ray daemon as a sidecar container
   2. with EC2 (across all applications and accounts)
      1. Configure X-ray daemon to use an IAM instance role
      2. Create a role in the target unified account and allow roles in each sub-account to assume the role

## ECR

1. To upload an image
   1. `$(aws ecr get-login --no-include-email)`
      1.  get-login command retrieves a token that is valid for a specified registry for 12 hours, and then it prints a docker login command with that authorization token
   2. `docker pull 1234567890.dkr.ecr.eu-west-1.amazonaws.com/demo:latest`
2. 

## IAM

1. Access advisor on IAM console - to identify unused roles
2. Resource-based policy only support Trust policy
3. SCP and Permission boundar can only limit permissions but cannot grant permissions
4. STS give credential from 900 seconds (15 mins) up to 1 hour, default 1 hour
5. Use policy variable to "dyanmically calculate resources"
6. AWS STS decode-authorization-message
   1. Use to decode additional information about authorization status of a request
   2. The message is encoded because the user who requested the operation should not see
7. Cognito Identity Pool
   1. Amazon Cognito identity pools provide temporary AWS credentials for users who are guests (unauthenticated) and for users who have been authenticated and received a token. Identity pools provide AWS credentials to grant your users access to other AWS services.
8. Cognito Sync
   1. You can use it to synchronize user profile data across mobile devices and the web without requiring your own backend. The client libraries cache data locally so your app can read and write data regardless of device connectivity status.
   
## Kinesis data streams

1. Read
   1. 2MB/second/shard shared between all applications consuming data from the stream
   2. Use enhance fan out if there are multiple consumer receiving data from the stream in parallel. 
      1. 2MB/second read per client

## Lambda

1. Reserved concurrency
   1. To ensure that a function can always reach a certain level of concurrency
2. Provisioned concurrency
   1. Enable function to scale with fluctuations in latency
3. Use alias to point to a function version
   1. Can configure alias to point to existing version and direct a small percentage of traffic to new version
4. To store temporary files, you can use the local directory `/tmp` with 512 mb
5. Declaring database connection outside of the handler, allow the connection to be re-used across function calls as it is kept in the execution context

## Route 53

1. CNAME record - maps DNS queries for the name of the current record such as acme.example.com to mybusiness.com
   1. Cannot create CNAME for example.com but able to do www/acme.example.com
2. Alias record - redirect queries to selected AWS resources such as S3, Cloudfront, another record in S3
3. A record - point a domain to an IP address

## SQS

1. Visiblity timeout
   1. Use ChangeMessageVisilbity to extend a message's visibility timeout
   2. Minimum 0 seconds
   3. Maximum 12 hours
   4. Default 30 seconds
2. Parameters
   1. MessageDeDuplicationID: used for deduplication of sent messages. Message with same deduplicationID are not accepted sucessfully during 5 minute deduplication interval
   2. MessageGroupID: tag to specifies that a message belong to a specific message group
   3. ReceiveRequestAttemptID: used for deduplication of ReceivedMessage call
   4. ContentBasedDeduplication: queue setting to instruct SQS to hash the body message to generate the deduplication ID
3. SQS FIFO - 3000 messages per second (batch of 10 messages)/300 api calls per second
4. Dead-letter queue must be of the same type as the queue - i.e. fifo queue use fifo dead-letter queue
   1. Don't use dead-letter queue for application that needs exact order of message
5. Max message size 
   1. 1KB to 256KB
   2. > 256 kb to 2 GB, use Amazon S3 with SQS extended client library
6. Long polling 
   1. Eliminate number of empty responses and false empty responses
   2. Max wait time is 20 seconds
7. Encryption
   1. enable SQS KMS encryption to protect content of messages in queue
   2. SSE let you transmit sensitive data in encrypted queues
8. Maximum number of message retrieve is 10

## S3

1. Use **AWS IAM Access Analyzer **to help identify unintended access to resources in your organization and accounts such as S3 bucket or IAM roles.
2. Versioning applies to all of the object in the bucket
3. Object store in bucket before versioning have a state of versionID  = null
4. When you suspend versioning, existing object in bucket do not change
5. Bucket policy allows you to grant permissions to your Amazon S3 resources
6. To allow public access
   1. edit block public access settings
   2. edit account-level block public access settings
7. Minimizing the number of API call use
   1. --max-item: retrieve only the number of items 
   2. --page-size: specify CLI to request a smaller number of items for each call (default to 1000)
   3. --start-token: to retrieve the next set of items
8. Use S3 select to retrieve only a subset of data from an object by using SQL expression
9. IAM instance profile can create a pre-signed URL that is valid for up to 6 hours
10. Publish S3 events to
    1.  SNS
    2.  SQS (only standard queue)
    3.  Lambda
11. Header needed for encryption
    1.  SSE-KMS: `x-amz-server-side-encryption: aws:kms`
    2.  SSE-S3: `x-amz-server-side-encryption: ES256`
        

## SAM (Serverless Application Model)

1. Supported resource type
   1. AWS::Serverless::API
   2. AWS::Serverless::Application
   3. AWS::Serverless::Function
   4. AWS::Serverless::HttpAPI
   5. AWS::Serverless::LayerVersion
   6. AWS::Serverless::SimpleTable
   7. AWS::Serverless::StateMachine

## X-ray

1. X-Ray sampling
   1. Define how many request to record for a set of criteria
2. X-Ray Daemon 
   1. Software application that listens for traffic on UDP port 2000, gather raw segment data and relate it to X-Ray API
   2. Uses the instance's profile role to upload trace data to X-Ray
3. Annotations - simple key-value pairs that are indexed for use with filter expressions
4. Metadata - key value paris but not indexed
5. Segments - computing resources running using application logic send data  about their work as segments
6. Env variable
   1. AWS_XRAY_DAEMON_ADDRESS
      1. by default, SDK uses 127.0.0.1:2000 for both trace data and sampling.
      2. this variable can be configured if the daemon is listening on a different port
   2. AWS_XRAY_TRACING_NAME
      1. sets a service name that the SDK uses for segments
   3. AWS_XRAY_CONTEXT_MISSING
      1. set to LOG_ERROR to avoid throwing exceptions when instrumeted code attempts to record data when no segment is open
   4. AWS_XRAY_DEBUG_MODE
      1. set to TRUE to configure SDK to output logs to the console, instead of configuring a logger
   





















---





# Summary

## Chapter 1: IAM summary

1. IAM is universal
2. Root account is simply the account created when first setup your AWS account
   1. Has complete Admin access
3. New users have NO permissions when first created
4. New users are assigned access key id and secret access keys 
5. New users cannot use the access key id & secrect access key to login to AWS console
6. Secret access key can only be downloaded once
7. Always setup MFA on root
8. Create and customize own password rotation

## Chapter 2: EC2 summary

1. Pricing
   1. On-demand
   2. Reserved 
   3. Spot - enables you to bid for instance capacity
   4. Dedicated host - physical EC2 server dedicated to customers.
2. Spot instance
   1. If the spot instance is terminated by Amazon EC2, you will not be charged for a partial hour of usage
   2. If you terminate the instance, you will be charged for the complete hour in which the instance ran
3. EBS
   1. SSD
      1. General Purpose SSD
      2. Provisioned IOPS - Anything over 16,000 IOPS
   2. Magnetics - cannot be boot volume
      1. Throughtput optimized
      2. Cold HHD
4. ELB
   1. ALB
   2. NLB
   3. Classic load balancers
   4. 504 error means gateway timeout
      1. Application not responding within the idle timeout period
   5. Need IPV4 address, look for the X-forwarded-for header
5. Route 53
   1. Amazon's DNS service
   2. Allow to map domain names to EC2 instances, load balancers and S3 buckets
6. CLI
   1. Least privilege
   2. Create groups - assign users to group
   3. Do not create once access keys - create one access keys per developers
7. Exam tips
   1. Use roles to access AWS resources
   2. Encrypt the root device volume 
      1. using operation system level encryption
      2. take a snapshot of the volume and create a copy of that snap with encryption. Create an AMI from the snapshot and deploy to encrypted root device volume
      3. Encrypt additional volume using CLI
8. AWS database types
   1. RDS - OLTP
      1. SQL, MySQL, PostgresSQL, Oracle, Aurora, MariaDB
   2. DynamoDB - NOSQL
   3. Redshift - OLAP
   4. Elasticcache 
9. Read replica
   1.  Have automatic backups turned on to deploy a read replica
   2.  Have up to 5 read replica for RDS (except aurora)
   3.  Can have read replica of read replica (watch out for latency)
   4.  Each replica will have its own DNS endpoint
   5.  Can have read replica that have multi-AZ
   6.  Can crate read replica of multi-AZ source databases
   7.  Can be promoted to their own databases but it will break replication
   8.  Can have read replica in a second region 
10. Elastic cache
    1.  Good to alleviate load if database is read heavy
    2.  Memcached
        1.  Keep thing as simple as possible
        2.  Scale cache horizontally
    3.  Redis
        1.  Advance data types
        2.  Do data sorting and ranking
        3.  Data persistence
        4.  Multi AZ
        5.  Pub/sub capabailities

## S3 Summary

1. S3 is object based
   1. Files can be 0 bytes to 5 TB
   2. Unlimited storage
   3. S3 is a universal namespace, globally unique name
   4. Read after write consistency for PUTS of new object
2. Storage classes
   1. IA
   2. One zone IA
   3. Glacier
3. S3 Object
   1. Key
   2. Value
   3. Version ID
   4. Metadata
   5. Subresources
      1. Bucket policies, ACLs
      2. CORS
      3. Transfer acceleration
4. Newly created buckets are private
   1. Bucket policies - applied at bucket level
   2. ACL  - applied at an object levels
5. S3 buckets encryption
   1. to prevent unencrypted files from being uploaded, create a policy which only allows request that include x-amz-server-side-encryption parameter
6. CORS
   1. Enable cross origin access for AWS resources
   2. By default, resources in one bucket cannot access resources located in another
   3. Use S3 website URL, not regular bucket URL
7. Cloudfront
   1. Edge location
   2. Origin - all files that CDN will distribute
   3. Distribution - name given the CDN
      1. Web distribution
   4. Can read and write
   5. Cached for the life of the TTL (default, 24 hours)
   6. Can clear cache manually (invalidation)
   7. 2 performance optimization for S3
      1. Use cloudfront
      2. Avoid sequential key names for S3 objects to prevent multiple objects from storing on the same partition
         1. This will avoid I/O contention, creating "hot spot"
  
## Serverless

#### Exam tips
1. Lambda
   1. Lambda Scale out 
   2. 1 event = 1 function
   3. X-ray allow you to debug what is happening
   4. Lambda can do things globally
2. API gateway
   1. has caching capabilities
   2. low cost and scales automatically
   3. throttle API gateway
   4. log results to cloudwatch
   5. enable CORS 
3. Version control
   1. Latest version use $latest
   2. immutable
   3. can split traffic using aliases
   4. can split only 2 ways
4. Step function
   1. great way to visualize your serverless application
5. X-ray
   1. interceptors to add to code
   2. client handler to instrument AWS SDK clients
   3. Http client to instrument calls to other internal and external http web service
   4. Integrates with
      1. ELB
      2. Lambda
      3. API gateway
      4. EC2
      5. Elastic beanstalk

## DynamoDB

1. Low latency NoSQL database
2. Suppot JSON, HTML, XML
3. Support both document and key-value data model
4. 2 types of primary key
   1. partition key
   2. composite key - partition key + sort key
5. 2 consistency model 
   1. strong consistency
   2. eventual consistency
6. Access controlled using IAM
   1. use condition paramter : dynamodbLeadingKey to allow user to access only the items where the partition key value matches their userID
7. Indexes enable fast queries 
8. Local secondary index
   1. created when create table
   2. same partition key as the table
   3. different sort key
9. Global secondary index
   1.  create any time
   2.  different partition key
   3.  different sort key
10. Scan vs query
    1.  A query find items in a tble using only the primary key attribute
    2.  A scan operations examine every item in the table, return all data attributes
        1.  Can use projection expressioto refine results
    3.  Query results are always sorted by sort key
        1.  Sort in accesnding rder
        2.  To reverse order, use scanindexforward
    4.  To improve performance
        1.  Use a smaller page size, which uses lesser read operations
        2.  isolate scan operations to specific tables and segregate them
        3.  Try parallel scans
        4.  Avoid using scans; design tables in a way you can use Query, Get, or BatchGetItem
11. Capacity Unit
    1.  1 x write capacity = 1kb write per second
    2.  1 x read capacity = 4kb read per second (strong consistency)/ 2 x 4kb read (eventual consistency)
12. DAX
    1.  In memory caching
    2.  eventually consistent read only
    3.  point to DAX cluster
    4.  Most suitable for read heavy application
13. Elastic cache
    1.  In-memory cache
    2.  2 caching strategies: Lazy-loading / write through
    3.  Lazy loading only caches data when it is requested
    4.  Write data into cache whenever there is a change to databasse

## KMS

1. Creating a CMK
   1. Setup CMK
   2. Key administrative permissions
   3. Key usage permissions
2. Exam tips
   1. AWS-managed CMK
   2. Customer-managed CMK
      1. Create own and manage yourself
      2. encrypt and decrypt up to 4KB and generate data key
3. Envelope encryption
   1. Encrypting the key that encrypt your data
   2. CMK is used to encrypt the data key (envelope key)
   3. The data key encrypt your data
   4. KMS does not store a copy of the data key
   5. Avoid over sending all data into KMS
4. API calls
   1. aws kms encrypt - encrypt plain text into ciphertext
   2. aws kms decrypt
   3. aws kms re-encrypt - decrypt and re-encrypt using a CMK
   4. aws kms enable-key-rotation
   5. aws kms generate-data-key - use to encrypt data

## Other service

1. SQS 
   1. Distributed message queueing system
   2. maximum retention period is 14 days
   3. pull-based
   4. Standard
      1. Best effort ordering
      2. occasional duplicates
      3. message delivered at least once
   5. No priority queue
   6. FIFO
      1. first in first out
      2. no duplicates
      3. messages are delivered once
   7. Visibility time out
      1. amount of time the message is invisible after a reader pick up (default 30s to a max to 12 hours)
   8. Short polling
      1. response is returned immediately even if no message are in the queue
   9. Long polling
      1. Periodically polls the queue and only return a response when a message is in the queue, or the timeout is reached. Most cost effective option
      2. max 20 seconds for a long poll timeout
   10. Delay queue
      3. postpone delivery of new messages (0 - 15 mins)
   11. Large SQS messages > 256 kb - 2GB
      4.  Use S3 to store large SQS messages
      5.  Use SQS Extended client library + AWS SDK for java
2.  SNS
    1.  Support SMS, SQS, HTTP, email
    2.  Push notifications
    3.  Pub/sub model
    4.  Consumer need to subscribe to a topic
    5.  Fanout to large number of recipients
3.  SES
    1.  Send and receive emails
    2.  Not subscription based
4.  Difference between SNS and SQS
    1.  SNS
        1.  Messaging service
        2.  push notification
    2.  SQS
        1.  messaging service
        2.  pull based
        3.  polling the queue for messages
5.  Kinesis
    1.  Streams
        1.  Capture and store streaming video and data for real-time processing
        2.  Consumer process and analyse the data in real-time
        3.  Made up of shards
        4.  Each shard is a sequence of one or more data records
        5.  KCL running on consumer run a record processor for each shard being consume
        6.  Number of consumer should not exceed the number of shard
    2.  Firehose
        1.  Capture, transform and load data continously
    3.  Analytics
        1.  real time analytics using standard SQL on data recieved by kinses data stream or fire hose
        2.  store data on es,s 3
6.  Elastic beanstalk
    1.  Deploy and scale web applications
    2.  Provision AWS resources
    3.  Take care of system administration (os updates, health checks)
    4.  Use elastic beanstalk configuration files
        1.  JSON or yml
        2.  .config extenstions
        3.  save into .ebextensions folder at root folder level
    5.  Deployment types
        1.  All at once
        2.  Rolling
        3.  Rolling with additional batch
        4.  Immutable
        5.  Traffic splitting (enabling canary testing)
    6.  RDS 
        1.  inside beanstalk
            1.  quick and easy way to get started
            2.  database will be terminated
            3.  suitable for dev and tes
        2.  outside beanstalk
            1.  tear down application stack without impacting database
            2.  additional configuration, security group and connection information as environment properties
            3.  for production env

## CI/CD

1. Exam tips
   1. Continous integration - integrating or merging the code changes (code commit)
   2. continous delivery - automating build, test and deployment (code build, code deployment)
   3. continous deployment - fully automated release process (code pipeline)
2. Code commit
   1. centralized code repository
   2. enable collaboration
   3. version control
3. In-place vs blue green
   1. In-place
      1. capcity is reduced
      2. lambda not supported
      3. rolling back involves a re-deploy
      4. great when deploying the first time
   2. Blue/green
      1. no capacity reduction
      2. green instances can be created ahead of time
      3. easy to switch
      4. pay for 2 environment
4. Code deploy
   1. appspec file
   2. OS, files, hooks
      1. Hooks
         1. Before block traffic : before deregistring with lb
         2. Block
         3. After block traffic : after deregistring
         4. Application stop
         5. download bundle 
         6. Before install
         7. install
         8. After install
         9. application start
         10. validate Service
         11. Before allow traffic : before registring with lb
         12. allow traffic
         13. after allow traffic
   3. save at the root directory
   4. Deployment
      1. de-registring, installation, re-registrating with a load balancer
5. Code pipeline
   1. AWS and third-party tools
6. ECS: container orchestration
   1. Fargate (serverless)
   2. EC2 (more control)
7. ECR: container registry
8. Docker exam tip
   1. docker build -t imagerepo
   2. docker tag (apply an alias)
   3. docker push
9. Code build
   1.  buildspec.yml
   2.  view logs in cloudwatch
10. Cloudformation
    1.  configure and provision AWS infrastructure
        1.  Parameters : input custom values
        2.  Conditions: base on env
        3.  Resources : Mandatory (AWS resources)
        4.  Mapping: custom mapping
        5.  Transform: reference code in S3, specify to use for SAM
    2.  Nested stacks
        1.  great for frequently used configs
        2.  template stored in S3
        3.  resource type is stack
11. SAM
    1.  Serverless application model
    2.  sam package
    3.  sam deploy - deploy

## Advance IAM

1. Cognito is an Identiy Broker which handles interaction between your application and Web ID provider
   1. Provide sign-up, sign-in and guest user access
   2. Uses user pool
   3. Uses push syn to send a silent push notifications of user data updates to multiple devices
2. Policies
   1. AWS managed policy
   2. Customer managed policy
   3. Inline policy

## Cloudwatch, cloudtrail and config

1. Cloudwatch monitor performance
2. Cloudtrail monitor API calls
3. AWS config records the state of AWS environment and can notify changes
