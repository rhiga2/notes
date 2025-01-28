Designing Data Intensive Applications
=====================================
# Reliability, Scalability, Maintainability
## Reliability
## Scalability 
## Maintainability

# Data Models and Query Languages
## Pre-Relational
## Relational DBs and SQL
## NoSQL 
* Example of NoSQL:
  * Key-Value Stores
  * Document DBs
  * Graph DBs

## Storage and Retrieval
* Goal is to build a key-value store with set and get methods
## Simple append-only
* Append only log
  * Append only writes faster than in-place random access writes 
* Index: additional data structure to retrieve where data is stored
## Hash Indexes
* Hash map: key points to offset in file, simplest index
* Avoid running out of space by compacting segments
  * Each compacted segment has in-memory hash map 
  * Deletion: Update value with tombstone
  * Crash recovery: store hash maps to disk. Don't have to remake hash maps with compaction
  * Partially-written records: checksum
## SSTables and LSM-Trees
* Keys in segments must be sorted
  * Merge (as in the merge in mergsort) on compaction of segments
  * No longer have to keep all keys in hash map, can be sparse
  * Reduce I/O bandwidth (why?)
* Instead of append-only log keep AVL / red-black tree in mem (memtable)
* Crash recovery: keep append-only log on disk so memtable can be restored
* Perf optimizations: bloomfilters
## B-Trees
* Write-ahead log (WAL): append-only file on disk to recover B-Tree state on crash
## B-Trees v LSM Trees
* B-Tree faster on reads, LSM Trees faster on writes
* Write amplificiation: one write to db must write multiple times to disk. Higher write amplification means less throughput.
* LSMs have less write amplification and better throughput.
* Background compaction in LSMs can interfere with read/write performance.
## Secondary Keys
* Unlike primary keys, secondary keys may not be unique. 
## Storing in Index
* Clustered index: row stored directly in index as opposed to pointer to data
* Heap file: where row is stored if pointer is stored in index
* Covered index: store some columns in index but not entire row
## Multi-Column Index
* Concatenated Index
 * Index such as lastname-firstname cannot find people by first name.  
* Multi-dimensional indexing (R-Trees, etc...)
## Full-Text Search and Fuzzy Indexing
* Edit Distance Automaton: Automaton to search for words within a certain distance
## In-Memory Databases
* Faster, but often less durable. More expensive to store in memory per byte than with disk.
## Transaction Processing v Analytics 
* Online transaction processing (OLTP): Reads, writes, and processes a small number of records at a time. Often times random-access.
* Online analytics processing (OLAP): Aggregation and analysis on large number of records at a time.
 * Data warehouse: Databases optimized for OLAP
 * Extract-load-transform: Getting data from one or many transaction DBs into data warehouse
* Star vs Snowflake Schema
## Column-Oriented Storage
* Row-oriented: Values in the same row are located next to each other in storage. Ideal for OLTP
* Column-oriented: Values in the same column are located close in storage. Ideal for OLAP that accesses few columns
 * Column compression: bitmap encoding of columns
* Sort-order: We need to specify primary, secondary, tertiary columns to determine sort. Cannot sort rows independently if we want to reconstruct the rows. Can lead to better compression in primary sorted column.
## Aggregations on Data
* Virtual view v materialized view: Materialized view actually stores copy of aggregations on to disk. Virtual view just expands the query.
* Materialized views don't make sense in write-heavy OLTP as write also needs to update the view.
* Data cubes

# Encoding and Evolution
## Data flows
* RPCs and REST APIs
* Message queues
* DBs

# Replication 

# Partitioning
## Key-Range Partitioning 
## Hash-Based
* Ensures uniformity, cannot do range queries 
## Dynamic Partitioning
* Splitting and merging
* Often involves human-in-the-loop since it also involves lots of data transfer
## Request Routing
* Service discovery: Which node to connect to?
* Options: round-robin routing (connect to node, node may ask another node that has partition), partition tier (specialized node for routing to connect parttition), or client is aware of correct partition.
* How does the routing learn about partition changes?
* Consensus
* Zookeeper

# Transactions
* Reads and writes that form a logical unit. Either all operations are executed or none. 
