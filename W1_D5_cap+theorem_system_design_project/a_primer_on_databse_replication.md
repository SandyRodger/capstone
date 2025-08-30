# [A Primer on Database Replication](https://www.brianstorti.com/replication/)

## background
- sending data around the world is limited by many things including the speed of light.
## What & why
- we want to keep a copy of the same data in multiple places
## CAP theorem
- really it's only consistency versus availabilty
## latency
- high response times could be caused by something other than latency, so know what you're trying to fix.
## Asynchronous replication
- Cons:
  - weakens durability guarantees
  - exposed to replication lags
## synchronous replication
- first replicate the data, then send a confirmation to the client
## not 8, not 80
- middle ground: some users can replicate synchronously
- AKA 'semi-synchronous replication'
## Single leader Replication
- the most common
## The challenges of an automatic failover
- it's hard to be sure the leader is dead.
## multi-leader replication
## dealing with conflicts
## DDL replication
## The topolofies of multi leader set-up
## leaderless replication
## Quorums
## replication lag
## reader-your-writes consistency
## Monotonic Reads consistency
## Bounded Staleness consistency
## Delayed replicas
## Replication under the hood
## Statement-based replication
## Log Shipping replication
## Diving deeper
