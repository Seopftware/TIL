# AWS

[Udemy - AWS Certified Solution Architect 2018](https://www.udemy.com/aws-certified-solutions-architect-associate/)를 기반으로 정리한 내용입니다.

## Section 1: Introduction to the Course

### 1. Introduction & Overview 2018
- 강사 소개
- AWS 성장 과정 및 전문가 과정 소개

### 2. Getting Started - What You'll Need!
- 실습은 Free Tier로 진행


### 3. The Exam Blue Print
AWS cerified solutions architecture
- 130 minutes
- 60 Questions
- Multiple CHoice
- Results are between 100 - 1000 with a passing score of 720
- Aim for 70%
- Qualification is valid for 2 years


## Section 2: AWS-10,000 Feet Overview

### 4. The History OF AWS So Far
- 인스턴스 관리가 쉽다. (terminate 클릭하면 된다. 따로 계약서가 필요하지 않다.)
- AWS officialy launched in 2006
- 2012 First re:Invent Conference

### 5. AWS - 10,000 Foot Overview
- I recommend that you use the U.S East Northern Virginia region.
- The reason for that is this is the oldest region and this is where all the new services come out first.
- There's currently 19 resgions 57 availiability zones around the world
- GovCloud Region is for government customers only.
- Edge Locations are endpoints for AWS which are used for caching content. Typically this consists of CloudFront, Amazon's Content, Delivery Network(CDN)
- ![img](/img/aws architect.png) 

	- Security, Identity & Compliance
	- Network & Content Delivery
	- Compute
	- Storage
	- Database
### 6. Sign Up To AWS Free Tier

### 7. AWS This Week
- "Everything changes and nothing stands still" -Heraclitus

## Section 3: Identity Access Management(IAM)

### 8. IAM 101

what is IAM?
- IAM allows you to manage users and their level of access to the AWS console.
- IAM allows you to set up users groups permissions and roles.

### 9. IAM - Lab
- Going to start getting our hands dirty with AWS.
- IAM is universial. It does not apply to regions at this time.
- The "root account" is simply the account created when first setup your AWS account. It has complete Admin access.
- New Users have NO permissions when first created.
- New Users are assigned AccessKey ID & Secret Access Keys when first created.
- These are not the same as a password. You can't use the Access key ID & Secret Access Key to Login in to the console. You can use this to access AWS via the APIs and Command Line, however.
- You only get to view these once. If you lose them, you have to regenerate them. So save them in a secure location.
- Always setup Multifactor Autentication on your root account.
- You can create and customise your own password rotation policies.


### 10. Create A Billing Alarm - Lab
- How to create billing alarm
- MyAccount => Dashboard or
- CloudWatch => Bills

### 11. IAM Summary

- Identity Access Management Consist Of The Following
	- Users
	- Groups
	- Roles
	- Policies


### Quiz 1: IAM - Quiz
-


### action point
- root 계정에 Multifactor Authentication 적용되어 있는지?
- 각각의 멤버에게 알맞은 접근 권한이 설정되어 있는지? ex)나, cloud front에만 권한이 있어야 한다.



## Reference
- [Udemy - AWS Certified Solution Architect 2018](https://www.udemy.com/aws-certified-solutions-architect-associate/)