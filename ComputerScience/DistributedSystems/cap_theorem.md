CAP Theorem 
====================
# CAP Theorem
* Consistency : Every read receives the most recent write or an error
* Availability : Every request is served
* Partition Tolerance : The system continues to operate despite network partitions
* CAP Theorem states that a distributed system cannot achieve all three.
* Usually we require partition tolerance so we need to choose between consistency (CP) and availability (AP).
* CP systems may not give back response until partition is resolved. 
* AP systems may return stale data until partition is resolved.

# Consistency Patterns
* Weak consistency : System does not guarantee that subsequent reads will return the same value.
* Eventual consistency : System guarantees that if no new updates are made to a given data item, eventually all accesses will return the last updated value.
* Strong consistency : System guarantees that each read receives the most recent write.

* Availability Patterns
* Fail-over : Backup server takes over when primary server fails.
    * Active-passive : Backup server is not used until primary fails. Primary sends heartbeats to backup. If backup does not receive heartbeat, it takes over.
    * Active-active : Both servers are used. Load balancer sends requests to both servers. If one fails, the other takes over.
* Replication : 
    * Master-slave : Master serves reads and writes and replicates writes to slave. Slaves are read-only servers.
    * Master-master : Both servers can serve reads and writes. Both servers replicate writes to each other.
