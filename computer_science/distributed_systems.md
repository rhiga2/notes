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
* Single threaded execution cannot be interactive (transaction cannot be multiple requests). Usually transactions is a stored procedure.
*   
