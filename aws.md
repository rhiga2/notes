# Amazon Web Service
## Virtual Private Cloud
## Storage Solutions
### Storage Types
Type of storage solutions include:
* **Block Storage**: Files are stored in blocks that have their own address. Changing a character in a file requires only modifying the block where the character resides.
  * **Elastic Block Storage (EBS)**: Supplemental storage attached to EC2 instance. Can only be attached to one EC2 instance at a time. 
* **File System Storage**: Files are storaged in a hierarchy. Changing a character in a file requires modifying the whole file.
  *  
* **Object System Storage**: Files are stored without hierarchy. Similar to file systems changing a character in a file requires modifying the whole file. Each file is given a unique key similar to the path of the file in a file system.
  * **Simple Storage Solution (S3)**: S3 is not attached to any compute instance 
## Databases
### Relational Databases
* **Relational Database Management Systems (RDBMS)**: lets you create, update, and administer a relational database. Examples include MySQL and PostgresSQL. 
* **Amazon RDS**
* Multi-AZ Replication: You can launch multiple DB instances in multiple AZs. RDS manages data replication so that the instances stay in sync.
* Storage Layer of DBs: DB instances use EBS as storage layer 
### Non-Relational Databases
* **Amazon DynamoDB**: NoSQL database that is more scalaable, performant, and has a less rigid schema than RDS, but does not support joins and relations between tables. 
* Items: Rows of table. Each item has a primary key as an identifier. 
* Attributes: Columns of table 

