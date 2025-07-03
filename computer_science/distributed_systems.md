# Transactions
## Race Conditions
* Dirty Read: One client sees an uncommited write.
* Dirty Write
* Read Skew
* Lost Updates
* Write Skew: Concurrent writes lead to invariant being violated.
* Phantom Reads: Write in one query changes the read results in another query.
* 

## Snapshot Isolation
* Transactions do not see partial effects of concurrent transactions.
* 

## Write-Write Conflicts
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

## Serializability
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
 
# Problems with Distributed Systems
## Faults and Partial Failures

 
