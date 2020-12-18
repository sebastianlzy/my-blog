---
title: "Hosting a website on AWS: EBS vs EC2 vs Lightsail vs Amplify"
date: 2020-12-18
slug: "/hosting-a-website-on-aws"
---

## S3 + Cloudfront
![S3 and cloudfront](https://github.com/sebastianlzy/draw-io/raw/master/icons/icons-S3andCloudfront.png)

**Amazon Simple Storage Service (Amazon S3)** is an object storage service that offers industry-leading scalability, data availability, security, and performance. Amazon S3 is designed for 99.999999999% (11 9's) of durability, and stores data for millions of applications for companies all around the world.

**Amazon CloudFront** is a fast content delivery network (CDN) service that securely delivers data, videos, applications, and APIs to customers globally with low latency, high transfer speeds, all within a developer-friendly environment.

### Who should use S3 + Cloudfront?
Those who have a static website or a single page application

### What are the advantages of using S3 + Cloudfront?
As the management of the solution is by Amazon, there is no server to manage. S3 is built to be resilient and scalable. It is the most cost effective solution for hosting a website

### References
1. [Hosting static websites on AWS](https://d0.awsstatic.com/whitepapers/Storage/Building%20Static%20Websites%20on%20AWS.pdf)
 
## AWS Elastic Bean Stalk
![Elastic bean stalk](https://github.com/sebastianlzy/draw-io/raw/master/icons/icons-Beanstalk.png)

**AWS Elastic Beanstalk** is an easy-to-use service for deploying and scaling web applications and services developed with Java, .NET, PHP, Node.js, Python, Ruby, Go, and Docker on familiar servers such as Apache, Nginx, Passenger, and IIS.
You can simply upload your code and Elastic Beanstalk automatically handles the deployment, from capacity provisioning, load balancing, auto-scaling to application health monitoring. At the same time, you retain full control over the AWS resources powering your application and can access the underlying resources at any time.

There is no additional charge for Elastic Beanstalk - you pay only for the AWS resources needed to store and run your applications.

### Who should use AWS Elastic Bean Stalk?
Those who want to deploy and manage their applications within minutes in the AWS Cloud. You don’t need experience with cloud computing to get started. AWS Elastic Beanstalk supports Java, .NET, PHP, Node.js, Python, Ruby, Go, and Docker web applications.

### What are the advantages of using AWS Elastic Bean Stalk?
AWS Elastic Beanstalk automates the details of capacity provisioning, load balancing, auto scaling, and application deployment, creating an environment that runs a version of your application. You can simply upload your deployable code (e.g., WAR file), and AWS Elastic Beanstalk does the rest. The AWS Toolkit for Visual Studio and the AWS Toolkit for Eclipse allow you to deploy your application to AWS Elastic Beanstalk and manage it without leaving your IDE. Once your application is running, Elastic Beanstalk automates management tasks–such as monitoring, application version deployment, a basic health check–and facilitates log file access. By using Elastic Beanstalk, developers can focus on developing their application and are freed from deployment-oriented tasks, such as provisioning servers, setting up load balancing, or managing scaling.

### What elements can I control using AWS Elastic Bean Stalk
With AWS Elastic Beanstalk, you can:

1. Select the operating system that matches your application requirements (e.g., Amazon Linux or Windows Server 2016)
2. Choose from several Amazon EC2 instances including On-Demand, Reserved instances, and Spot instances 
3. Choose from several available database and storage options
4. Enable login access to Amazon EC2 instances for immediate and direct troubleshooting
5. Quickly improve application reliability by running in more than one Availability Zone
6. Enhance application security by enabling HTTPS protocol on the load balancer
7. Access built-in Amazon CloudWatch monitoring and getting notifications on application health and other important events
8. Adjust application server settings (e.g., JVM settings) and pass environment variables
9. Run other application components, such as a memory caching service, side-by-side in Amazon EC2
10. Access log files without logging in to the application servers


### References
1. [Blue green deployment](https://aws.amazon.com/quickstart/architecture/blue-green-deployment/)

## EC2
![ec2](https://github.com/sebastianlzy/draw-io/raw/master/icons/icons-EC2.png)

Amazon Elastic Compute Cloud (Amazon EC2) is a web service that provides secure, resizable compute capacity in the cloud. It is designed to make web-scale cloud computing easier for developers. Amazon EC2’s simple web service interface allows you to obtain and configure capacity with minimal friction. It provides you with complete control of your computing resources and lets you run on Amazon’s proven computing environment.

### Who should use EC2?
1. Requirement: Team with strong dedicated system operator
2. Application that requires fine grain control or custom configuration

### What are the advantages of EC2?
EC2 allows small developers to acquire massive compute resource to handle large or spiky load. The "Elastic" nature of the service allow developers to instantly scale to meet spikes in traffic or demand

### What are the disadvantages of using EC2?
There is a significantly higher maintenance cost as businesses need to handle all aspect of the deployment and instances including patching

### References
1. [isms-p quickstart](https://aws.amazon.com/quickstart/architecture/isms-p/)

## Lightsail
![lightsail](https://github.com/sebastianlzy/draw-io/raw/master/icons/icons-Lightsail.png)

Lightsail is an easy-to-use cloud platform that offers you everything needed to build an application or website, plus a cost-effective, monthly plan. Whether you’re new to the cloud or looking to get on the cloud quickly with AWS infrastructure you trust, we’ve got you covered.

### Use case
1. Common web stacks i.e. LAMP, MEAN and PHP application (Wordpress, Magento)

### Advantages
1. Familiar EC2 environment

### Disadvantages

## Amplify
![Amplify](https://github.com/sebastianlzy/draw-io/raw/master/icons/icons-Amplify.png)

AWS Amplify is a set of tools and services that can be used together or on their own, to help front-end web and mobile developers build scalable full stack applications, powered by AWS. With Amplify, you can configure app backends and connect your app in minutes, deploy static web apps in a few clicks, and easily manage app content outside the AWS console.

Amplify supports popular web frameworks including JavaScript, React, Angular, Vue, Next.js, and mobile platforms including Android, iOS, React Native, Ionic, Flutter (Preview). Get to market faster with AWS Amplify.

### Use case
1. Built in support for static site generators such as Gatsby, Jekyll, and Hugo, and support for JavaScript single page applications written in a variety of frameworks like React, Angular, or Vue
2. Deploy a SPA with a serverless backend

### Advantages
1. Easy to use
2. Reduce go to market 
3. Strong integration with GraphQL

### Disadvantages



