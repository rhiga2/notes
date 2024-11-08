## Chapter 1: Reliability, Scalability, Maintainability
### Reliability
### Scalability 
### Maintainability

## Chapter 2: Data Models and Query Languages
### Pre-Relational
### Relational DBs and SQL
### NoSQL 
* Example of NoSQL:
  * Key-Value Stores
  * Document DBs
  * Graph DBs

## Chapter 3: Storage and Retrieval
* Goal is to build a key-value store with set and get methods
### Simple append-only
* Append only file
* Index: additional data structure to retrieve where data is stored
### Hash Indexes
* Hash table: key points to offset in file
* Avoid running out of space with compaction
  * Deletion: Update value with tombstone
* Checksum 

