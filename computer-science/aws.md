# Amazon Web Service
## Identity and Access Management
## Compute
## Virtual Private Cloud
### Subnets
## Storage Solutions
### Storage Types
Type of storage solutions include:
* Block Storage: Files are stored in blocks that have their own address. Changing a character in a file requires only modifying the block where the character resides.
  * Elastic Block Storage (EBS): Supplemental storage attached to EC2 instance. Can only be attached to one EC2 instance at a time. 
* File System Storage Files are storaged in a hierarchy. Changing a character in a file requires modifying the whole file.
  *  
* Object System Storage: Files are stored without hierarchy. Similar to file systems changing a character in a file requires modifying the whole file. Each file is given a unique key similar to the path of the file in a file system.
  * Simple Storage Solution (S3): S3 is not attached to any compute instance 
## Databases
### Relational Databases
* Relational Database Management Systems (RDBMS): lets you create, update, and administer a relational database. Examples include MySQL and PostgresSQL. 
* Amazon RDS: AWS database solution that launches instances and uses EBS as the storage layer.  
* Multi-AZ Replication: You can launch multiple DB instances in multiple AZs. RDS manages data replication so that the instances stay in sync.
### Non-Relational Databases
* Amazon DynamoDB: NoSQL database that is more scalaable, performant, and has a less rigid schema than RDS, but does not support joins and relations between tables. 
* Items: Rows of table. Each item has a primary key as an identifier. 
* Attributes: Columns of table
## Monitoring
### Metrics
* Time series data such as CPU utilization, latency, memory consumption, etc...
* Namespace
* Dimensions: key-value pair attached to metric. Helps to search for metrics
### Logs
* Text data generated from application such as stack traces, thread dumps, heap dumps, etc...
* Log Event
* Log Stream
* Log Groups
### CloudWatch
* Centralized location for logs and metrics from application or infrastructure
* Accepts custom logs and metrics 
## Load Balancing and Autoscaling
### Elastic Load Balancer
* Highly available, regional, and automatically scalable
* Listener: ports and protocols that client connects to
* Target Group: EC2 instances, ip addresses, AWS lambdas, etc ... to route requests to
* Rule: how requests are routed target. For example, round robin routing algorithm or least outstanding request routing algorithm
### EC2 Autoscaling
