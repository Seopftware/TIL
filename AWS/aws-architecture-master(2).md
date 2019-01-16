# AWS

[Udemy - AWS Certified Solution Architect 2018](https://www.udemy.com/aws-certified-solutions-architect-associate/)를 기반으로 정리한 내용입니다.

## Section 5: The Backbone of AWS

### 26. EC2 101

#### What is EC2
- Amazon Elastic Compute Cloud(EC2) is a web service that provides resizable compute capacity in the cloud. Amazon EC2 reduces the time required to obtain and boot new server instances to minutes, allowing you to quickly scale capacity, both up and down, as your computing requirements change.
- Amazon EC2 changes the economics of computing by allowing you to pay only for capacity that you actually use. Amazon EC2 provides developers the tools to build failure resilient applications and isolate themselves from common failure scenarios.

EC2 Options
- On Demand
	- allows you to pay a fixed rate by the hour (or by the second) with no commitment.
	- Perfect for users that want the low cost and flexibility of Amazon EC2 without any up-front payment or long-term commitment.
	- Applications with short term, spiky, or unpredictable workloads that cannot be interrupted
	- Applications being developed or tested on Amazon EC2 for the first time.

- Reserved
	- provides you with a capacity reservation, and offer a significant discount on the hourly charge for an instance. 1 Year or 3 Year Terms
	- Applications with steady state or predictable usage
	- Applications that require reserved capacity
	- Users can make up-front payments to reduce their total computing costs even further
	- Standard RIs (Up to 75% off on-demand)
	- Convertible RIs (Up to 54% off on-demand) feature the capacity to change the attributes of the RI as long as the exchange results in the creation of Reserved Instances of equal or greater value.
	- Scheduled RIs are available to launch within the time window you reserve. This option allows you to match your capacity reservation to predictable recurring schedule that only requires a fraction of a day, a week, or a month.

- Spot
	- enables you to bid whatever price you want for instance capacity, providing for even greater savings if your application have flexible start and end times.
	- Applications that have flexible start and end times
	- Applications that are only feasible at very low compute prices
	- Users with an urgent need for large amounts of additional computing capacity


- Dedicated Hosts
	- Physical EC2 server dedicated for your use. Dedicated Hosts can help you reduce costs by allowing you to use your existing server-bound software licenses.
	- Useful for regulatory requirements that may not support multi-tenant virtualization.
	- Great for licensing which does not support multi-tenancy or cloud deployments.
	- Can be purchased On-Demand (hourly).
	- Can be purchased as a Reservation for up to 70% off the On-Demand price.

#### EC2 Instance Types

- F for FPGA
- I for IOPS
- G - Graphics
- H - High Disk Throughput
- T cheap general purpose (think T2 Micro)
- D for Density
- R for RAM
- M - main choice for general purpose apps
- C for Compute
- P - Graphics (think Pics)
- X - Extreme Memory

image Edward Norton fighting a Scottish duck who likes to hand out pictures of his homeland.

#### What is EBS?
- Amazon EBS allows you to create storage volumes and attach them to Amazon EC2 instances. Once attached, you can create a file system on top of these volumes, run a database, or use them in any other way you would use a block device. Amazon EBS volumes are placed in a specific Availability Zone, where they are automatically replicated to protect you from the failure of a single component.

#### EBS Volume Types (1)
- General Purpose SSD (GP2)
	- General purpose, balances both price and performance
	- Ratio of 3 IOPS per GB with up to 10,000 IOPS and the ability to burst up to 3000 IOPS for extended periods of time for volumes at 3334 GiB and above.

- Provisioned IOPS SSD (IO1)
	- Designed for I/O intensive applications such as large relational or NoSQL databasee.
	- Use if you need more than 10,000 IOPS
	- Can provision up to 20,000 IOPS per volume

- Throughput Optimized HDD (ST1)
	- Big data
	- Data warehouses
	- Log processing
	- Cannot be a boot volume

- Cold HDD (SC1)
	- Lowest Cost Storage for infrequently accessed workloads
	- File Server
	- Cannot be a boot volume

- Magnectic (Standard)
	- Lowest cost per gigabyte of all EBS volume types that is bootable. Magnetic volumes are ideal for workloads where data is accessed infrequently, and applications where the lowest storage cost is important.

#### EC2 Exam Tips

- On Demand: allows you to pay a fixed rate by the hour (or by the second) with no commitment
- Reserved: provides you with a capacity reservation, and offer a significant discount on the hourly charge for an instance. 1 Year 3 Year Terms 
- Spot: enables you to bid whatever price you want for instance capacity, providing for even greater savings if your applications have flexible start and end times.
- Dedicated Hosts: Physical EC2 server dedicated for your use. Dedicated Hosts can help you reduce costs by allowing you to use your existing server-bound software licenses.

- If a Spot instance is terminated by Amazon EC2, you will not be charged for a partial hour of usage. However, if you terminate the instance yourself, you will be charged for the complete hour in which the instance ran.

- FIGHT DR MC PX!

SSD
- General Purpose SSD: balances price and performance for a wide variety of workloads.
- Provision IOPS SSD: Highest-performance SSD volume for mission-critical low-latency or high-throughput workloads

Manetic
- Throughput Optimized HDD: Low cost HDD volume designed for frequently accessed, throughput-intensive workloads
- Cold HDD: Lowest cost HDD volume designed for less frequently accessed workloads
- Magnetic: Previous Generation. Can be a boot volume.

### 27. Let's Get Our Hands Dirty! Launch An EC2 Instance - Part1
### 28. Let's Get Our Hands Dirty! Launch An EC2 Instance - Part2
### 29. How To Use Putty (Windows Users Only)
### 30. Security Groups Basics
### 31. Upgrading EBS Volume Types - Lab
### 32. Creating a Windwos EC2 Instance & RAID Group
### 33. Create An AMI - Lab
### 34. AMI's - EBS Root Volumes vs Instance Store