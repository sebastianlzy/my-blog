---
title: "Hosting a website on AWS"
date: 2020-12-18
slug: "/hosting-a-website-on-aws"
tags:
  - AWS amplify
  - AWS elastic beanstalk
  - AWS elastic computing
  - AWS lightsail
  - Amazon S3
  - Amazon Cloudfront
---

## Objective

AWS has a plethora of services that help developers build world class application and it pride itself with the broadest and deepest set of services. Nevertheless, choosing the right product for your application requires intimate knowledge of the service. I have put together a simple decision tree to help team starting out in AWS to build a new application 

### Decision tree
![Decision Tree](https://github.com/sebastianlzy/draw-io/raw/master/icons/icons-compute-decision-tree.png)

### References
1. [compute decision tree](https://medium.com/weareservian/choosing-a-suitable-aws-compute-product-a-decision-tree-1dc46caef824)

## Services

### Amazon S3 + Amazon Cloudfront
![S3 and cloudfront](https://github.com/sebastianlzy/draw-io/raw/master/icons/icons-S3andCloudfront.png)

**Amazon Simple Storage Service (Amazon S3)** is an object storage service that offers industry-leading scalability, data availability, security, and performance. Amazon S3 is designed for 99.999999999% (11 9's) of durability, and stores data for millions of applications for companies all around the world.

**Amazon CloudFront** is a fast content delivery network (CDN) service that securely delivers data, videos, applications, and APIs to customers globally with low latency, high transfer speeds, all within a developer-friendly environment.

#### Who should use Amazon  S3 + Amazon Cloudfront?
Those who have a static website or a single page application

#### What are the advantages of using Amazon S3 + Amazon Cloudfront?
As the management of the solution is by Amazon, there is no server to manage. S3 is built to be resilient and scalable. It is the most cost effective solution for hosting a website

#### References
1. [Hosting static websites on AWS](https://d0.awsstatic.com/whitepapers/Storage/Building%20Static%20Websites%20on%20AWS.pdf)
 
### AWS Elastic Bean Stalk
![Elastic bean stalk](https://github.com/sebastianlzy/draw-io/raw/master/icons/icons-Beanstalk.png)

**AWS Elastic Beanstalk** is an easy-to-use service for deploying and scaling web applications and services developed with Java, .NET, PHP, Node.js, Python, Ruby, Go, and Docker on familiar servers such as Apache, Nginx, Passenger, and IIS.
You can simply upload your code and Elastic Beanstalk automatically handles the deployment, from capacity provisioning, load balancing, auto-scaling to application health monitoring. At the same time, you retain full control over the AWS resources powering your application and can access the underlying resources at any time.

There is no additional charge for Elastic Beanstalk - you pay only for the AWS resources needed to store and run your applications.

#### Who should use AWS Elastic Bean Stalk?
Those who want to deploy and manage their applications within minutes in the AWS Cloud. You don’t need experience with cloud computing to get started. AWS Elastic Beanstalk supports Java, .NET, PHP, Node.js, Python, Ruby, Go, and Docker web applications.

#### What are the advantages of using AWS Elastic Bean Stalk?
AWS Elastic Beanstalk automates the details of capacity provisioning, load balancing, auto scaling, and application deployment, creating an environment that runs a version of your application. In addition Elastic Beanstalk automates management tasks–such as monitoring, application version deployment, a basic health check–and facilitates log file access


#### What are the disadvantages of AWS Elastic Bean Stalk?
AWS Elastic Beanstalk is a managed services. As a result, many of the granular controls are not expose to business application developers to change. 


#### References
1. [Blue green deployment](https://aws.amazon.com/quickstart/architecture/blue-green-deployment/)

### AWS EC2
![ec2](https://github.com/sebastianlzy/draw-io/raw/master/icons/icons-EC2.png)

Amazon Elastic Compute Cloud (Amazon EC2) is a web service that provides secure, resizable compute capacity in the cloud. It is designed to make web-scale cloud computing easier for developers. Amazon EC2’s simple web service interface allows you to obtain and configure capacity with minimal friction. It provides you with complete control of your computing resources and lets you run on Amazon’s proven computing environment.

#### Who should use AWS EC2?
1. Requirement: Team with strong dedicated system operator
2. Application that requires fine grain control or custom configuration

#### What are the advantages of AWS EC2?
EC2 allows small developers to acquire massive compute resource to handle large or spiky load. The "Elastic" nature of the service allow developers to instantly scale to meet spikes in traffic or demand

#### What are the disadvantages of AWS EC2?
There is a significantly higher maintenance cost as businesses need to handle all aspect of the deployment and instances including patching

#### References
1. [isms-p quickstart](https://aws.amazon.com/quickstart/architecture/isms-p/)

### AWS Lightsail
![lightsail](https://github.com/sebastianlzy/draw-io/raw/master/icons/icons-Lightsail.png)

Lightsail is an easy-to-use cloud platform that offers you everything needed to build an application or website, plus a cost-effective, monthly plan. Whether you’re new to the cloud or looking to get on the cloud quickly with AWS infrastructure you trust, we’ve got you covered.

#### Who should use AWS Lightsail?
Common web stacks i.e. LAMP, MEAN and PHP application (Wordpress, Magento) can be deployed on AWS light sail. It is great for first-time cloud users and developers looking to run their prototype 

#### What are the advantages of AWS Lightsail?
AWS lightsail provides a simplified UI that helps developer to focus on getting a server running with preinstalled sotware as soon as possilbe. The service can grow and scale with the application over time. With plans starting at $5 a month, it is very affordable

#### What are the disadvantages of AWS Lightsail?
Scaling has to be done manually and it is not recommended for enterprise-level workloads. 

### Amplify
![Amplify](https://github.com/sebastianlzy/draw-io/raw/master/icons/icons-Amplify.png)

AWS Amplify is a set of tools and services that can be used together or on their own, to help front-end web and mobile developers build scalable full stack applications, powered by AWS. With Amplify, you can configure app backends and connect your app in minutes, deploy static web apps in a few clicks, and easily manage app content outside the AWS console.

Amplify supports popular web frameworks including JavaScript, React, Angular, Vue, Next.js, and mobile platforms including Android, iOS, React Native, Ionic, Flutter (Preview). Get to market faster with AWS Amplify.

#### Who should use AWS Amplify?
AWS amplify is great for developers who don't want to build their backend or other components from scratch. 

#### What are the advantages of AWS Amplify?
AWS amplify includes a wide variety of open-source libraries with a drag and drop UI components that allow developers to use as their building blocks for their app. 

#### What are the disadvantages of AWS Amplify?
AWS amplify tries to be a one service that rule them all. It has backend, frontend, UI component, scaffolding, infrastructure as code, CI/CD pipeline. As such, it can be ambiguous and complex to managed. 



