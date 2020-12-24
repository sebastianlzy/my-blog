---
title: "Cost optimization for startup"
date: 2020-12-18
slug: "/cost-optimization-for-startup"
tags:
  - Cost optimization
---


## Common areas to investigate

### Choosing the cheaper region

Deploy in US-West-2 instead of US-West-1 can be cheaper and save on cost. US-West-2 might have expanded breadth/depth of service stack

### DevOps Environment Running 24x7

Hibernate or shut down resources when inactive i.e. Developer need to sleep. 

### PIOPS vs GP2/3 Block storage

Most application do not need the extra IO provided by PIOPS. Consider using GP2/3 where you are able to provision more IO if needed at a lower price than PIOPS

### Multi-AZ vs Single-AZ for non-Critical databases

Mission critical DBs should run on multi-AZ to minimize downtime and data loss. However, DBs in test/dev environment can run on single AZ to save half the cost

### Data transfer

If you are transferring TB's of data each month via EC2, a potential cost-saving tips will be to use Cloudfront with zero TTL
Applications spread across AZ's can incur substantial inter-region data transfer charges

### Account sprawl

Look for forgotten accounts and look to shutting them down

### Storage tier

Leverage S3 Storage tiers or use S3 intelligence tier to move data to cheaper alternatives

### Leverage on Spot instance

### Saving plans

1. Compute saving plans (Up t)
    1. 
2. EC2 instance saving plans 

### Reserve instance

1. Convertible RIs
2. Standard RIs
