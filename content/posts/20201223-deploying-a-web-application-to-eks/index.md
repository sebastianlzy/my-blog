---
title: Deploying a web application using EKS
date: 2020-12-23
description: Deploying a web application using EKS 
tags:
  - Container
  - EKS

---


# Objective
Wrap existing web application into a container and deploy to EKS

## Steps


## References

1. eksctl: https://eksctl.io/
2. Best practices: https://aws.github.io/aws-eks-best-practices/
3. Container-roadmap: https://github.com/aws/containers-roadmap
4. EKS workshop: https://www.eksworkshop.com/
    1. [Auto scaling](https://www.eksworkshop.com/beginner/080_scaling/deploy_ca/)


# FAQ

## CNI
### What is an overlay network?
An overlay network is a type of networking whereby administrators create multiple atomic and discrete virtualized network layers on top of the physical infrastructure. It decouples network services from the underlying infrastructure by leveraging encapsulation techniques

AWS Virtual Private Cloud uses this technique to run thousands of private, atomic networks across across millions of devices, spanning multiple sites and regions.

In the context of Kubernetes, an overlay network allows Pods in a Kubernetes cluster to communicate over multiple clusters in a separate IP range to the underlying VPC.

![fannel](https://cdn.sanity.io/images/hgftikht/production/1b228c7fea815cdc70a75dc1bc01d72bce3e503d-1600x972.png?w=1280&h=778&fit=crop&fm=webp)
 
### Why did AWS develop CNI?
Using overlay network is extremely complex. There are too many layer of abstraction and encapsulation

1. VPC Flow Logs don’t work: The underlying VPC has no context for the encapsulated overlay network that is running on top of it. VPC flow logs will only show traffic between the hosts in the Kubernetes cluster and makes troubleshooting any network related issues a pain.
2. Security Groups don’t work: Since the VPC has no context for the overlay network, it is unable to apply security policies to the individual pods, instead only applying them to the Kubernetes cluster itself. This means you need to run, manage and maintain two sets of network policy controls.
3. I have another thing I can break: By implementing an overlay network, I have created another fault domain for my application stack. The more fault domains that I need to worry about, the more likely I am going to be woken up at 3am with a problem that affects every single application in the cluster.
4. I don’t want to manage this stuff anymore: The reason we are moving to the cloud is to shift the accountability away from me and to a company that can scale these services larger, better, faster and more efficiently than I could dream to. By creating another network stack for me to manage, I feel like I’m stepping back into the dark ages of on-premise networks.

AWS VPC CNI looks to simplify the complexity by leveraging its ability to attached multiple ENI to a virtual machines

Goals of AWS VPC CNI:

1. Pod network connectivity performance must be similar to AWS VPC Network. That is, low latency, minimal jitter, high throughput and high availability
2. Users must be able to express and enforce granular network policies and isolation comparable to those achievable with native EC2 networking and security groups
3. Network operation must be simple and secure. Users must be able to apply existing AWS VPC networking and security best practices for building Kubernetes clusters over AWS VPC
4. VPC Flow Logs must work
5. VPC Routing Policies must work
6. Pod Network Setup in Seconds
7. Pods must be able to attach to the network in seconds
8. Clusters should be able to scale to ~2000 nodes.

![AWS VPC CNI](https://cdn.sanity.io/images/hgftikht/production/dc1f912510f1817d7c6b14d1ea53a337e1a35996-1600x989.png?w=1280&h=791&fit=crop&fm=webp)

### How does security group works with AWS CNI?

As AWS CNI map pods to a secondary IP addresses, we can specify which security groups to assign to pods 

![Sg](https://cdn.sanity.io/images/hgftikht/production/5a9416eb3f6aacadb79a91111eff50d48f682175-1600x851.png?w=1280&h=681&fit=crop&fm=webp)

### When should you not use AWS CNI?
Virtual Machines in AWS have a max limit on the number of Elastic Network Interfaces that can be attached to any single vm at any time. This number varies by instance type. This can be calculated as follows:

ENIs x Secondary ips per ENI = Max Pods per Node

If the application you are building requires extremely high density of pods to nodes, you would be better off using one of the other CNI solutions like Calico or Weave, or perhaps something like Hashicorp’s Nomad which has been proven to scale up to one million containers across 5k hosts.

Another issue with the AWS CNI is its inefficient use of IP addresses. In order to attach an IP address to a Pod as quickly as possible, the CNI pre-loads a number of IPs to the Node. If the cluster is deployed in a particularly small VPC, you may run out of addresses, even if they aren’t being used by real workloads.

1. https://docs.aws.amazon.com/eks/latest/userguide/pod-networking.html

### References
1. https://www.contino.io/insights/kubernetes-is-hard-why-eks-makes-it-easier-for-network-and-security-architects



