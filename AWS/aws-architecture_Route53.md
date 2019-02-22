## Section 6: Route53



### 53. DNS 101

#### What is DNS?

- If you've used internet, you've used DNS. DNS is used to convert human friendly domain names(such as http://acloud.guru) in to an Internet Protocol (IP) address (such as http://82.124.53.1)
- IP addresses are used by computers to identify each other on the network
- IP addresses commonly come in 2 different forms, IPv4 and IPv6



#### IPv4 vs IPv6

- The IPv4 space is a 32 bit field and has over 4billion different addresses (4,294,967,296 to be precise)
- IPv6 was created to solve this depletion issue and has an address space of 128 bits which in theory is 304,282,366,920,938,463,463,374,607,431,768,211,456 addresses or 340 undercillion address.



#### Top Level Domains

- If we look at common domain names such as google.com, bbc.co.uk, you will notice a string of characters separated by dots(periods). The las word in a domain name represents the "top level domain". The second word in a domain name is known as a second level domain (this is optional though and depends on the domain name.)
- .com, .edu, .gov (top level domain)
- .co.uk, .gov.uk, .com.au (second level domain name whereas dot uk is the top level domain name)

- There top level domain names are controlled by the internet Assigned Numbers Authority(IANA) in a root zone database which is essentially a database of all available top level domains. You can view this database by visiting: (http://www.iana.org/domains/root/db)



#### Domain Registras

- Because all of the names in a given domain name have to be unique there needs to be a way to organize this all so that domain names aren't duplicated. This is where domain registers come in.
- A registra is an authority that can assign domain names directly under one or more top-level domains. These domains are registered with InterNIC, a service of ICANN, which enforces uniqueness of domain names across the Internet. Each domain name becomes registered in a central database known as the WhoIS database.



#### Start Of Authority Record (SOA)

The SOA record stores information about:

- The name of the server that supplied the data for the zone
- The administrator of the zone
- The current version of the data file
- The default number of seconds for the time-to-live file one resouce records.



#### NS Records

- NS stands for Name Server records. They are used by Top Level Domain servers to direct traffic to the Content DNS server which contains the authoritative DNS records.



#### A Records

- An A record is the fundamental type of DNS record. The A in A record A record stands for Address. The A record is used by a computer to translate the name of the domain to an IP address.
- http://www.acloud.guru might point to http://123.10.10.10.60



#### TTL

- The length that a DNS record is cached on either the Resolving Server or the users own local PC is equal to the value of the "TIme TOo Live (TTL)" in seconds. The lower the time to live, the faster changes to DNS records take to propagate throughout the internet.



#### CNAMES

- A Canonicial Name(CName) can be used to resolve one domain name to another. FOr example, you may have a mobile website with the. omain name http://m.acloud.guru that is used for when users browse to your domain name on their mobile devices. You may also want the name http://mobile.acloud.guru to resolve to this same address.



#### Alias Records

- Alias records are used to map resource record sets in your hosted zone to Elastic Load Balancers, CloudFront distributions, or S3 buckets that are configured as website.
- Alias records work like a CNAME record in that you can map one DNS name (www.example.com) to another 'target' DNS name (elb1234.elb.amazonaws.com)
- Key difference - A CNAME can't be used for naked domain names (zone apex record). You can't have a CNAME for http://acloud.guru, it must be either an A record or an Alias.



#### Exam Tips

- ELBs do not have pre-defined IPv4 addresses; you resolve to them using a DNS name.
- Understand the difference between an Alias Record and a CNAME
- GIven the choice, always choose an Alias Record over a CNAME



#### SOA Reocrds

- A start of authority (SOA) record is information stored in a DNS zone about that zone. A DNS zone is the part of a domain for which an individual DNS server is responsible (i.e. the bit that you store A records, C-names etc). Each zone contains a single SOA record.



#### Alias Records

- Alias resource sets can save you time because Amazon Route 53 automatically recognizes changes in the record sets that the alias resource record set refers to.
- For example, suppose an alias resource record set for example.com points to an ELB load balancer at lb1-1234.us-east-1.elb.amazonaws.com. If the IP address of the load balancer changes, amazon Route 53 will automatically reflect those changes in DNS answers for example.com without any changes to the hosted zone that contains resource record sets for example.com



#### Common DNS Types

- SOA Records
- NS Records
- A Records
- CNAMES
- MX Records
- PTR Records



### 54. Route 53 - Register A Domain Name - Lab

- 도메인 네임 등록 



### 55. Different Routing Types On AWS

#### Routing Policies Available On Aws

- SImple Routing
- Weighted Routing
- Latency-based Routing
- Failover Routing
- Geolocation Routing
- Multivalue Answer Routing



### 56. Simple Routing Policy - Lab

#### Simple Routing Policy

- If you choose the simple routing policy you can only have one record with multiple IP addresses. If you specify multiple values in a record, Route 53 returns all values to the user in a random order.



### 57.Weighted Routing Policy - Lab

#### Weighted Routing

- we can specific weighting ex) 20% US-EAST-1, 80% US-WEST-1 즉, Route 53 will send 20% of the traffic to US-EAST-1 and 80% of the traffic to US-WEST-1



#### Lab

- move to route 53
- Create Record Set
- Routing Policy
  - Weight
  - SetID



#### Weighted Routing Policies

- Weighted Routing Policies let you split your traffic based on different weights assigned
- For example, you can set 10% of your traffic to go to US-EAST-1 and 90% to go to EU-WEST-1



### 58.Latency Routing Policy - Lab

#### Latency

- Latency based routing allows you to route your traffic based on the lowest network latency for your end user (i.e. which region will give them the fastest response time)
- To use layency-based routing, you create a latency resource record set for the Amazon EC2 (or ELB) resource in each region that hosts your website. 
- When Amazon Route 53 receives a query for your site, it selects the latency resource record set for the region that gives the user the lowest latency. Route 53 then responds with the value asscociated with that resource record set. 



#### Latency Based Routing

- In this example Route53 will send the traffic to EU-WEST-2 because it. as a much lower latency than AP-SOUTHEAST-2 (Route53 => EU-WEST-2 (54ms), AP-SOUTHEAST-2 (300ms))



#### Lab

- Route53 -> Hosted Zones -> Create Record Set



### 59.Failover Routing Policy - Lab

#### Failover

- In this example Route 53 will send the traffic to AP-SOUTHEAST-2 because it has detected a failure in EU-WEST-2 (route53이 EU-WEST-2로 Active 시도! 하지만 서버가 꺼져있거나, 장애가 있을 경우 다른 서버로 이동 시킴. Passive로 설정되어 있는 AP-Southeast-2로)



### 60.Geolocation Routing Policy - Lab

#### Geolocation

- Geolocation routing lets you choose where your traffic will be sent based on the geographic location of your users (ie the location from which DNS queries originate).
- For example, you might want all queries from Europe to be routed to a fleet of EC2 instances that are specifically configured for your European customers. 
- Theses servers may have the local language of your European customers and prices and displayed in Euros



#### Lab

- Routing Policy: Geolocation으로 설정



#### Tip

- European Customer -> route53 (geolocation) -> EU-WEST-1
- US Customer -> route53 (geolocation) -> US-EAST-1



### 61.Multivalue Routing

#### Multivalue Answer

- If you want to route traffic approximately randomly to multiple resources, such as web servers, you can create one multivalue answer record for each resource and optionally associate an Amazon Route 53 health check with each record.
- For example, suppose you manage an HTTP web service with a dozen web servers that each have their own IP address. No one web server could handle all of the traffic, but if you create a dozen multivalue answer records, Amazon Route 53 responds to DNS queries with up to eight healthy records in response to each DNS query.
- Amazon route 53 gives different answers to different DNS resolvers. If a web server becomes unavailable after a resolver caches a response, client software can try another IP address in the response.



### 62.DNS Exam Tips

#### Simple Routing Policy

- If you choose the simple routing policy you can only have one record with multiple IP addresses. If you specify multiple values in a record, Route 53 returns all values to the user in a random order.



#### Weighted Routing

- 20% US-EAST-1, 80% US-WEST-1
- Route 53 will send 20% of the traffic to US-EAST-1 and 80% of the traffic to US-WEST-1



#### Latency Based Routing

- South Afican User, EU-WEST-2 54ms, AP-SOUTHEAST-2 300ms
- Route53 will send the traffic to EU-WEST-2 because it has a much lower latency than AP-SOUTHEAST-2



#### Failover

- Active EU-WEST-2 (not working), Passive AP-SOUTHEAST-2
- Route53 will send the traffic to AP-SOUTHEAST-2 because it has detected a failure in EU-WEST-2



#### Geolocation

- European Customers -> EU-WEST-2, US Customers -> US-EAST-1
- Route53 will send the European customers to EU-WEST-1 and the US customers to US-EAST-1



#### Mulivalue Answer

- So we've got to use are they going to route 53.
- We've got let's say two records in this 30 to $0.00 132 or two.
- But we have health checks against each of these and each of these will be its own like a rover insight route 53 So unlike with simple way to routing policy where we could only have one we can have multivalue answers.
- We can also have health check against all these answers so if $30.00 0.1 comes out of service it will automatically go to 30.00 doctor and we can have up to eight healthy records in multi-body answer as well.



### Quiz 4: Route53 Quiz

Q.Does Route 53 support MX Records?

- yes



Q.Route53 is named so because

- It was invented in 1953
- Route 66 was already registered with Microsoft
- The DNS Port is on Port 53 and Route53 is a DNS Service (O)
- Only people in marketing can tell you the reason behind its name



Q.Route53 does not support zone apex records (or naked domain names)

- Correct
- Incorrect (O)
- Depends on the circumstances
- Only in Us-East-1



Q.Route53 is Amazon's DNS Service

- True (O)
- False



Q.There is a limit to the number of domain names that you can manage using Route53

- True, There is a hard limit of 10 domain names. You cannot go above this number (X)
  - There is a 50 domain names available by default, however it is a softlimit and can be raised by contacting AWS support
- True and False, There is a limit of 50 domain names however this limit can be raised by contacting AWS support (O)
- False, You can support as many domain names on Route53 as you want, by default



route53 관련글

- https://brunch.co.kr/@topasvga/85