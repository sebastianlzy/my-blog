---
title: "EBS vs EC2 vs Lightsail vs Amplify"
date: 2020-12-18
slug: "/ebs-ec2-lightsail-amplify"
---

## S3 + Cloudfront

Amazon Simple Storage Service (Amazon S3) is an object storage service that offers industry-leading scalability, data availability, security, and performance. Amazon S3 is designed for 99.999999999% (11 9's) of durability, and stores data for millions of applications for companies all around the world.

Amazon CloudFront is a fast content delivery network (CDN) service that securely delivers data, videos, applications, and APIs to customers globally with low latency, high transfer speeds, all within a developer-friendly environment.

### Use case
1. Great for running a static website, single page application

### Advantages
1. No server to manage
2. S3 is resilient and scalable
3. Cost effective
4. HTTPS enabled

## Elastic beanstalk

AWS Elastic Beanstalk is an easy-to-use service for deploying and scaling web applications and services developed with Java, .NET, PHP, Node.js, Python, Ruby, Go, and Docker on familiar servers such as Apache, Nginx, Passenger, and IIS.
You can simply upload your code and Elastic Beanstalk automatically handles the deployment, from capacity provisioning, load balancing, auto-scaling to application health monitoring. At the same time, you retain full control over the AWS resources powering your application and can access the underlying resources at any time.

There is no additional charge for Elastic Beanstalk - you pay only for the AWS resources needed to store and run your applications.

### Use case
1. Deploying standard application in a familiar environment

### Advantages
1. Easily control environment through console or CLI
2. Coupled with Docker-compatible AMI, able to control the full stack  

### Disadvantages

## EC2

Amazon Elastic Compute Cloud (Amazon EC2) is a web service that provides secure, resizable compute capacity in the cloud. It is designed to make web-scale cloud computing easier for developers. Amazon EC2’s simple web service interface allows you to obtain and configure capacity with minimal friction. It provides you with complete control of your computing resources and lets you run on Amazon’s proven computing environment.

### Use case
1. Enterprise application with strong dedicated system operator

### Advantages
1. Fine grained control of every aspect of your application

### Disadvantages
1. High maintenance cost

### References
1. (EC2 quick start)[https://aws.amazon.com/quickstart/architecture/isms-p/]

## Lightsail
Lightsail is an easy-to-use cloud platform that offers you everything needed to build an application or website, plus a cost-effective, monthly plan. Whether you’re new to the cloud or looking to get on the cloud quickly with AWS infrastructure you trust, we’ve got you covered.

### Use case
1. Common web stacks i.e. LAMP, MEAN and PHP application (Wordpress, Magento)

### Advantages
1. Familiar EC2 environment

### Disadvantages

## Amplify

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


