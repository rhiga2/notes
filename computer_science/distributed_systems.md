Distributed Systems 
======================
# Data Models and Query Languages
## Pre-relational (TODO)
## Reliational
### Structured Query Language (SQL) (TODO)
* SELECT-FROM-WHERE
* JOINs
* Subquerying 
## Post-relational (NoSQL)
* Why is relational DBs not enough?
  * Impedence: Not every object fits well in structured tables. Objects with nested data.
  * Schemas can evolve overtime. NoSQL can provide schema flexibility. 
  * Can be easier and more cost effective to retrieve. For example, if you always need object of type A with object of type B you can store both in the same document essentially pre-joining data, whereas relational DBs often store A and B in separate tables and join at runtime.  
* Examples of NoSQL data models include:
  * Key-value stores (i.e. DynamoDB)
  * Document DBs (i.e. MongoDB): Stores documents in json/yaml/xml format.
  * Wide-column stores: Stores that have column-families. A row can have some columns in a column-family, thus data is usually sparse.   
  * Graph DBs
## Encoding Data
* Data is stored in many formats depending on the context:
  * In-memory storage: often uses in-memory data structures such as objects in OOP. 
  * Long-term storage in databases: uses relational format, column-oriented format, key-value format, JSON/XML format for document storage, 
  * Data transferred in microservices: often uses binary encodings such as Protobuf, Avro, Thrift. Binary encodings are compact and save on bandwidth. 
  * The process of encoding data into binary is called serialization.  
  * Data transferred over APIs: Often uses human-readable format like JSON/XML. This is because external developers must be able to understand the format of the data in order to use the APIs in their own application. 
  * Data transferred in asyncronous message queues: Uses JSON/XML or uses binary encoding. 
* Forward and Backward Compatibility
  * Forward: Data is forward compatible if it is compatible with new code.
  * Backward: Data is backward compatible if it is compatible with old code.     

# Distributed Storage
## Replication
* There are three types of replication architectures:
	* Single-leader: Reads can happen on any node, but only the leader can accept writes. 
 	* Multi-leader: Each regional cluster has its own leader that accepts writes.
  * Leaderless
## Partition
## Transactions
### Race Conditions
* Dirty Read: One client sees an uncommited write.
* Dirty Write
* Read Skew
* Lost Updates
* Write Skew: Concurrent writes lead to invariant being violated.
* Phantom Reads: Write in one query changes the read results in another query.
* 

### Snapshot Isolation
* Transactions do not see partial effects of concurrent transactions.
* 

### Write-Write Conflicts
* Lost writes: concurrent writes clobber one another
* Atomic write: object is locked during read-modify-write cycle of an update
* App-side locking logic
* Auto-detection of lost updates: concurrent writes allows, retries update when lost write detected
* Compare-and-set: check if current value = old read before updating
* Conflict resolution: some dbs allow multiple latest copies. App code needed to resolve and merge.
  * Example include last write wins (prone to lost updates) 
* Write skew: concurrent writes lead to invariant being violated.
  * May involve multiple objects (i.e. moving multiple pieces to same position in a board game).
  * We can explicitly lock multiple rows that the transaction depends upon.
  * Phantom: write in one query changes the read results in another query.  
  * Materializing conflicts: create lock even there is no corresponding object being stores in DB (i.e. time slots, board game positions).

### Serializability
* Serializability: Executing concurrent transactions as if they occurred one after another.
* Three methods
  * Single thread execution
  * Two-phase locking
  * Optimistic concurrency control techniques
* Single threaded execution: Everything occurs in a single thread
  * Cannot be interactive (transaction cannot be multiple HTTP requests). Usually transactions is a stored procedure.
  * May have parallel execution as long as transactions touch different single partitions
  * Cross-partition coordination is slow
* Two-phase locking: writers can block readers and readers can block writers.
  * In snapshot isolation, only writers block writers
  * Shared lock can be acquired by many, but exclusive lock must wait for all shared locks to be released. No shared lock can be acquired if exclusive lock is active.
  * Exclusive aqcuired during transactions must be held until the end. 
  * Can be very slow, easy to overload 2PL with slow transactions
  * Risk of deadlocking. If deadlock is detected, then one of the transactions will be aborted.
  * Predicate lock: locks that are not defined on an object but on a condition (i.e. meeting room + time range)
  * Index-range lock: group multiple things to share lock.
* Serializable Snapshot Isolation (SSI)
  * Pessimistic concurrency control tries to prevent serializability violations, where as optimistic concurrency control lets transactions run concurrent and aborts transactions that violate seriazability.
  * Transactions usually read value first then decides to take action. The read value before taking action is called a premise.
  * SSI runs on snapshot isolation but extends it to include serializability. 
  * Two cases:
    * Stale snapshot: Transaction A modifies a value from 0 to 1 but does not commit immediately. Transaction B reads 0 in its consistent snapshot and increments it. Before B commits, A commits its update. At B’s commit, SSI detects a conflict (because B’s read version was overwritten by A), and may abort B to preserve serializability.
    * Snapshot before stale before commit: SSI uses a conflict-tracking mechanism (like a tripwire) to detect if concurrent transactions’ snapshots create a dangerous conflict pattern. If so, the system aborts one transaction — usually letting the first committer win — to maintain serializability.
  * Performance varies significantly by rate of aborts, thus it helps to keep transactions small.
 
# Distributed Systems Concepts
## Problems
* There are several issues concerning distributed systems including:
  * Partial Failures and Faults: some nodes in a cluster are bound to fail. 
  * Unreliable Networks: messages and connections between nodes may be dropped or timeout.
  * Unreliable Clocks: Two nodes may read different times. Clocks may skew overtime. Relying on different clocks to determine order of requests is unreliable.
  * Process Pauses: Processes can be preempted. Process is given exclusive update access. If it pauses and timeouts, another node may be given same priviledge. When the pause ends, we may have situations where both nodes think it owns the the exclusive access.

## Consistency
### Linearizability
* In distributed storage with replication,

## System Models, Safety, and Liveness
* Safety properties ensure nothing bad will occur. Safety properties often are specified by invariants that will never be violated.
* Liveness properties ensure something good will eventually occur. Liveness properties are specified by promises that will eventually ve satisfied. 

## Causality and Sequence Number Ordering


# Batch Processing
## MapReduce
* Join algorithms
  * Sort-merge joins
  * Broadcast hash joins
  * Partitioned hash joins
## Beyond Mapreduce
* Problems with mapreduce
  * Lack flexbility since not every data processing job needs to map-sort-reduce in that order. 
  * Not optimized to store intermediate state (aka materialization). Intermediate state between mapreduce jobs is published to HDFS, which can be overkill.
  * Cannot implement iterative "repeat until done" algorithms.
  * Lacks interactive (REPL) data exploration capabilities.
  * Creating mapreduce jobs is often done through imperative programming. 
* Data flow engines (i.e. Spark)
  * Often keep intermediate computational results in memory avoiding frequent disk writes like in mapreduce.  
  * Operators are functions that process data. Data engines define data processing jobs as operators chain together. They are a generalization on mapreudce since they can implement mapreduce computation but is more flexible.  
  * Spark Resilient Distrubted Databases can recover data by tracking lineage and recomputing the lost data. No need to fully materialize intermediate state to HDFS.
 * Declarative programming APIs are easier to use and query optimizers that make computation more efficient than imperative implementations.

# Stream Processing
* Difference to batch processing
  * Data is unbounded and incremental
  * Results need to be in near real-time.
* Message Passing System
  * What happens if the producer sends messages faster than consumption rate?
  * What happens during node crashes?
  * Direct messaging systems, application code must handle lost messages. Often does not account for producer or consumer crashes. 
  * Message brokers
    * Communication becomes asynchronous
    * Load balancing v fan out
  * Partitioned Logs
    * Messages are appended and consumers keep track of offset. Messages are not deleted when a consumer reads them. 
    * Circular buffer on disk. Old records will eventually get deleted.
    * Allows us to replay old data (not too old that the data was deleted).
    * This is similar to replication logs where the leader is the broker and followers are consumers. 
* Message Passing Applied to DBs
  * Change data capture (CDC) acts similar to message passing systems. Write to DB triggers CDC.
  * Changes are queued in a log of data changes and then consumed by search index and data warehouse.
  * Log compaction and consistent snapshot makes it so that the log does not become infinitely large.
  * Event sourcing is similar to CDC but CDC is a stream of mutable operations on a DB, event sourcing is a stream of immeutable events on an applicaiton. 
  * Event sourcing cannot be log compacted in the same way.
  * 


 
