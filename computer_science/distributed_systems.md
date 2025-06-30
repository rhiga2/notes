# Transactions
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
