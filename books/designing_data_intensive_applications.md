# Designing Data Intensive Applications
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
* Append only log
  * Append only writes faster than in-place random access writes 
* Index: additional data structure to retrieve where data is stored
### Hash Indexes
* Hash map: key points to offset in file, simplest index
* Avoid running out of space by compacting segments
  * Each compacted segment has in-memory hash map 
  * Deletion: Update value with tombstone
  * Crash recovery: store hash maps to disk. Don't have to remake hash maps with compaction
  * Partially-written records: checksum
### SSTables and LSM-Trees
* Keys in segments must be sorted
  * Merge (as in the merge in mergsort) on compaction of segments
  * No longer have to keep all keys in hash map, can be sparse
  * Reduce I/O bandwidth (why?)
* Instead of append-only log keep AVL / red-black tree in mem (memtable)
* Crash recovery: keep append-only log on disk so memtable can be restored
* Perf optimizations: bloomfilters
### B-Trees
* Write-ahead log (WAL): append-only file on disk to recover B-Tree state on crash
### B-Trees v LSM Trees
* B-Tree faster on reads, LSM Trees faster on writes
* Write amplificiation: one write to db must write multiple times to disk. Higher write amplification means less throughput.
* LSMs have less write amplification and better throughput.
* Background compaction in LSMs can interfere with read/write performance.
### Secondary Keys
* Unlike primary keys, secondary keys may not be unique. 
### Storing in Index
* Clustered index: row stored directly in index as opposed to pointer to data
* Heap file: where row is stored if pointer is stored in index
* Covered index: store some columns in index but not entire row
### Multi-column indices

# Chapter 4: 

