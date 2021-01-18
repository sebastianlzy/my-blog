---
title: "AWS Certified Solution Architect Professional - Deployment"
date: 2021-01-18
tags:
  - certification
  - aws solution architect professional
  - deployment
  - chapter 10
---

# Chapter 10: Deployment

## Elastic Beanstalk

1. Developer centric view of deploying an application on AWS
2. Full control over the configuration of each component
3. Beanstalk is free, you have to pay the underyling resources
4. Support
   1. Go
   2. Java SE
   3. Java with Tomecat
   4. .NET on window server
   5. Node.js
   6. PHP
   7. Python
   8. Ruby
   9. Packer Builder
   10. Single container docker
   11. Multicontainer Docker
   12. Preconfigured Docker
   13. Custom platform
5.  Bean is great to "Replatform"
6.  Managed service
    1.  Instance configuration handled by beanstalk
    2.  Deployment stragtegy is configuratble but performed by Elastic Beanstalk
7.  Developer is responsible for just the application code 

### 3 architecture models

#### Single instance deployment

![bean-stalk](./deployment/beanstalk-deployment-strategy.png)