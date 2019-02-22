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
action
- Termination protection 기능 활용 중인지
- Secutity Group 관리 제대로 되고 있는지
- Monitoring System 유용한지?

Lab Summary
- Termination Protection is turned off by default, you must turn it on.
- On an EBS-backed instance, the default action is for the root EBS volume to be deleted when the instance is terminated.
- EBS Root Volume of your DEFAULT AMI's cannot be encrypted. You can also use a third party tool (such as bit locker etc) to encrypt the root volume, or this can be done when creating AMI's (lab to follow) in the AWS console or using the API.
- Additional volumes can be encrypted.
### 29. How To Use Putty (Windows Users Only)
### 30. Security Groups Basics

action
- security group을 어떻게 관리하고 있는가? 관리 전략은?

#### Security Group Lab
- All inbound Traffic is Blocked By Default
- All outbound Traffic is Allowed
- Changes to Security Groups take effect immediately
- You can have any number of EC2 instances within a security group
- You can have multiple security groups attached to EC2 Instances
- Security Groups are STATEFUL
	- If you create an inbound rule allowing traffic in, that traffic is automatically allowed back out againg.
- You cannot block specific IP addresses using Security Groups, instaed use Network Access Control Lists.
- You can specify allow rules, but not deny rules.

### 31. Upgrading EBS Volume Types - Lab

#### Volumes & Snapshots

- Volumes exist on EBS:
	- Virtual Hard Disk
- Snapshots exist on S3
- Snapshots are point in time copies of Volumes.
- Snapshots are incremental - this means that only the blocks that have changed since your last snapshot are moved to S3.
- If this is your first snapshot, it may take some time to create.

#### Snapshots of Root

- To create a snapshot for Amazon EBS volumes that serve as root devices, you should stop the instance before taking the snapshot.
- However you can take a snap while the instance is runnung.
- You can create AMI's from EBS-backed Instances and Snapshots.
- You can change EBS volume sizes on the fly, including changing the size and storage type.
- Volumes will ALWAYS be in the same availability zone as the EC2 instance.
- To move an EC2 volume from one AZ/Region to another, take a snap or an image of it, then copy it to the new AZ/Region

#### Volumes vs Snapshots - Security

- Snapshots of encrypted volumes are encrypted automatically.
- Volumes restored from encrypted snapshots are encrypted automatically.
- You can share snapshots, but only if they are unencrypted.
	- These snapshots can be shared with other AWS accounts or made public.

### 32. Creating a Windwos EC2 Instance & RAID Group

#### RAID, Volumes & Snapshots

- RAID = Redundant Array of Independent Disks
	- RAID 0: Striped, No Redundancy, Good Performance
	- RAID 1: Mirrored, Redundancy
	- RAID 5: Good for reads, bad for writes, AWS does not recommend ever putting RAID 5's on EBS
	- RAID 10: Striped & Mirrored, Good Redundancy, Good Performance

#### How can I take Snapshot of a RAID Array?

- Problem: Take a snapshot, the snapshot excludes data held in the cache by application and the OS. This tends not to matter on a single volume, however using multiple volumes in a RAID array, this can be a problem due to interdependencies of the array.
- Solution: Take an application consistent snapshot.

- Stop the application from writing to disk
- Flush all caches to the disk
- How can we do this?
	- Freeze the file system
	- Unmount the RAID Array
	- Shutting down the associated EC2 instance

### 33. Create An AMI - Lab

#### Snapshots of Root Device Volumes
- To create a snapshot for Amazon EBS volumes that serve as root devices, you should stop the instance before taking the snapshot.

#### Volumes vs Snapshots - Security
- Snapshots of encrypted volumes are encrypted automatically.
- Volumes restored from encrypted snapshots are encrypted automatically.
- You can share snapshots, but only if they are unencrypted.
	- These snapshots can be shared with other AWS accounts or made public

### 34. AMI's - EBS Root Volumes vs Instance Store

#### You can select your AMI based on
- Region (see Region and Availability Zones)
- Operating system
- Architecture (32-bit or 64-bit)
- Launch Permissions
- Storage for the Root Device (Root Device Volume)
	- Instance Store (EPHEMERAL STORAGE)
	- EBS Backed Volumes

#### EBS vs Instance Store
- All AMIs are categorized as either backed by Amazon EBS or backed by instance store.
- For EBS Volumes: The root device for an instance launched from the AMI is an Amazon EBS volume created from an Amazon EBS snapshot.
- For Instance Store Volumes: The root device for an instance launched from the AMI is an instance store volume created from a template stored in Amazon S3.

#### EBS vs Instance Store - Exam Tips
- Instance Store Volumes are sometimes called Ephemeral Storage.
- Instance Store Volumes cannot be stopped. If the underlying host fails, you will lose your data.
- EBS backed instances can be stopped. You will not lose the data on this instance if it is stopped.
- You can reboot both, you will not lose your data.
- By default, both ROOT volumes will be deleted on termination, however with EBS volumes, you can tell AWS to keep the root device volume.

### 35. Load Balancing Theory

#### Type Of Load Balancers

- Application Load Balancer
- Network Load Balancer
- Classic Load Balancer



#### Application Load Balancers

- Application Load Balancers are best suited for load balancing of HTTP and HTTPS traffic. They operate at Layer 7 and are application-aware. They are intelligent, and you can create advanced request routing, sending specified requests to specific web servers.



#### Network Load Balancer

- Network Load Balancer are best suited for load balancing of TCP traffic where extreme performance is required. Operating at the connection level (Layer 4), Network Load Balancer are capable of handling mllions of requests per second, while maintaing ultra-low latencies. 



#### Classic Load Balancers

- Classic Load Balancers are the legacy Elastic Load Balancers. You can load balance HTTP/HTTPS applications and use Layer 7-specific features, such as X-Forwarded and sticky sessions. You can also use strict Layer 4 load balancing for applications that rely purely on the TCP protocol.



#### Load Balancer Errors

- Classic Load Balancers - if your application stops responding, the ELB (Classic Load Balancer) responds with a 504 error
- This means that the application is having issues. This could be either at the Web Server layer or at the Database Layer.
- Identify where the application is failing, and scale it up or out where possible



#### ELB Exam Tips

- 3 Types of Load Balancers
  - Application Load Balancers
  - Network Load Balancers
  - Classic Load Balancers

- 504 Error means that gateway has timed out. This means that the application not responding within the idle timeout period.
  - Trouble shoot the application. Is it the Web server or Database Server?
- If you need the IPv4 address of your end user, look for the X-Forwareded-For Header.



### 36.Load Balancers & Health Checks

#### Elastic Load Balancers

- Instances monitored by ELB are reported as : InService or OutofService
- Health Checks check the instance health by talking to it
- Have their own DNS name. You are never given an IP address
- Read the ELB FAQ for Classic Load Balancers



### 37. Cloud Watch EC2

#### Exam Tips

- Standard Monitoring = 5 Minutes
- Detailed Monitoring = 1 Minute



#### What can I do with Cloud Watch?

- Dashboards - Create awesome dashboards to see what is happening with your AWS environment
- Alarms - Allows you to set Alarms that notify you when particular thresholds are hit
- Events - CloudWatch Events helps you to respond to state changes in your AWS resources
- Logs - CloudWatch Logs helps you to aggregate, monitor, and store logs.



### 38.The AWS Command Line & EC2 

### 39.Using IAM roles with EC2

- role이 짱인 이유는 로컬에 키를 저장하지 않아도 되기 때문에 보안적으로 안전하다

### 

### 40.S3 CLI & Regions

- EC2를 통해 S3 bucket에 접속하기
- S3 bucket을 생성하고, EC2에 해당 bucket에 접속할 수 있는 IAM role 부여
- EC2에서 IAM role attach

- S3 bucket에 있는 데이터 다운로드
  - aws s3 cp --recursive s3://acloudguru-apsoutheast2 /home/ec2-user



### 41.Using Bootstrap Scripts

#### BashScript

- MyKeyPair.pem
  - chmod 400 MyKeyPair.pem (권한을 400으로 변경 필요)

- ssh ec2-user@51.41.13.14 -i MyKeyPair.pem
- sudo su 
  - root 권한 얻기

이 명령어들을 EC2가 실행될 때 자동으로 실행될 수 있게 작업해보자

- yum update -y
- yum install httpd -y
- service httpd start
- chkconfig httpd on
- cd /var/www/html



나의 S3 bucket List를 볼 수 있는 명령어 (안될 경우 role check)

- aws s3 ls



EC2를 생성할 때 Advanced Details에 스크립트를 붙여넣는다.



### 42. EC2 Instance Metadata

