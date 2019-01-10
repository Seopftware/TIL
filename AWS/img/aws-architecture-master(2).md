## S3 - 101
S3 provides developers and IT teams with secure, durable, highly-scalable object storage. Amazon S3 is easy to use, with a simple web services interface to store and retrieve any amount of data from anywhere on the web.

S3 is a safe place to store your files.

It is Object-based storage.

The data is spread across multiple devices and facilities.


### S3 - The basics

- S3 is Object-based (i.e. allows you to upload files.)
- Files can be from 0 Bytes to 5 TB.
- There is unlimited storage.
- Files are stored in Buckets.
- S3 is a universial namespace. That is, names must be unique globally.
- https://s3-eu-west-1.amazaonaws.com/aclodudguru
- When you upload a file to S3, you will receive a HTTP 200 if the upload was successful.

### Data Consistency Model For S3

- Read after Write consistency for PUTS of new Objects.
- Eventual Consistency for overweite PUTS and DELETES (can take some time to propagate)

### S3 is a Simple Key-value Store

S3 is Object based. Objects consist of the following
- Key (name) : This is simply the name of the object
- Value (data) : This is simply the data and is made up of a sequence of bytes.
- VersionID : Important for versioning
- Metadata : Data about data you are storing
- Subresources: 
	- Access Control Lists
	- Torrent

### S3 - The Basics
- Built for 99.99% availbility for the S3 platform.
- Amazon Guarantee 99.9 availibity.
- Amazon guarantee 99.99999% durability for S3 information.
- Tiered Storage Available
- Lifecycle Management
- Versioning
- Encryption
- Secure your dara using Access
- Control Lists and Bucket Policies


### S3 - Storage Tiers / Classes

- S3 Standard: 99.99% availbility, 99.99% durability, stored redundantly across multiple devices in multiple facilities, and is designed to sustain the loss of 2 facilities concurrently.
(durable, immediately available, frequently accessed)
- S3 - IA: (Infrequently Accessed) For data that is accessed less frequently, but requires rapid access when needed. Lower fee than S3, but you are charged a retrieval fee.
(durable, immediately available, infrequently accessed)
- S3 One Zone - IA: want a lower-cost option for infrequently accessed data, but do not require the multiple Availiabilty Zone data resilience.
(even cheaper than IA, but only in one availability zone.)
- Glacier: Very cheap, but used for archival only. Expedited, Standard or Bulk. A Standard retrieval time takes 3 - 5 hours.
(Archived data, where you can wait 3-5 hours before accessing.)

### S3 - Charges
Charged for
- Storage
- Requests
- Storage Management Pricing
- Data Transfer Pricing
- Transfer Acceleration

What is S3 Transfer Acceleration?
- Amazon S3 Transfer Acceleration enable fast, easy and secure transfers of files over long distance between your end users and an S3 bucket.
- Transfer Acceleration takes advantage of Amazon CloudFront's globally distributed edge locations. As the data arrives at an edge location, data is routed to Amazon S3 over an optimized network path.

### Tips for S3
- Object-based storaged only (for files.)
- Not suitable to install an operating system on.

## Create an S3 Bucket - Lab