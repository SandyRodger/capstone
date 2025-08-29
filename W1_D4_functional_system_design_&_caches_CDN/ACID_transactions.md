[video](https://www.youtube.com/watch?v=VRm2UMsFVz0)

- transaction is a unit of work executed to
  - retrieve
  - insert
  - remove
  - update
- this piece of work means runnning queries in a database
- In RDBMS all transactions must be ACID:
  - Atomic
  - Consistent
  - Isolated
  - Durable
### example: bank transfer

- check sufficient funds
- subtract from payers account
- add to receivers account
- mark transfer as successful

### Atomic

-"atomicity"
- All or nothing.
- If any part fails everything fails.

### Consistency

- after transaction is commited, data is still in a valid state. (ie constraints)

### Isolated

- the statements are executed sequentially.
- Even if in reality the operations happen concurrently, the guarantee is that the outcome is as if they had happened sequentially
- Loweing isolation level means transactions could effect each other.
- There are performance gains with this, but [above]
### Durable

- the effects of a committted transaction are permanently stored.
