[talk](https://www.youtube.com/watch?v=bG9AQ9ce5Zo)
### CAP theorem:

- can only have 2 of the following three:
  - Consistency:
    - every read receives the most recent write or an error
  - Availability:
    - every request receives a non-error response
  - Partition tolerance
    - the system functions despite detwork partitions

### srdjan's presentation

- it is incorrect to say you only have 2 out of 3.
- It is correct to say you have to choose between A or C
- If there's a break between US and Europe servers you can either stop writes and maintain consistency or allow writes and then the two servers are inconsistent
- Consistency is necessary for banking apps
- Tinder is an example of both -> matches have to be consistent but... (another example)
- Ticket master:
  - booking a seat must be consistent
  - so if 2 servers can't communicate then it refuses to book that seat because it doesn't know if that seat is free.
- If you want consistency you choose a SQL database
  - If you want availability you want MongoDB (DOUBLE CHECK THIS)
  - If you want low latency you want another database.

### transactions in SQL ?

- a grouping of SQL statements treated as one single unit.

```sql
BEGIN TRANSACTION
  UPDATE   ACCOUNT   SET   BALANCE = BALANCE = 200 where ID=1
  UPDATE account SET balance = balance + 200 WHERE id=2
COMMIT;
```

#### ACID

- referring to SQL only
- different databases support different ideas around this, but if you want strong consistency you're going to go for SQL.
- Atomic
  -"atomicity"
  - All or nothing.
  - If any part fails everything fails.
- Consistency
  - after transaction is commited, data is still in a valid state. (ie constraints)
- Isolated
  - the statements are executed sequentially.
  - Even if in reality the operations happen concurrently, the guarantee is that the outcome is as if they had happened sequentially
  - Lowering isolation level means transactions could effect each other.
  - There are performance gains with this, but [above]
- Durable
  - the effects of a committted transaction are permanently stored.

### BASE

- no one says this. It's just eventual consistency (the E ) that you haave to remember.

### URL shortener

- tinyurl.com
- Only works for websites that don;t need authentication
- It's on the exam (what exam?)
- Until you see this solution it's impossible to figure it out.
- How to make one:
  - Use cases:
    - shorten URL
    - Redirect to longer URL
  - Optional use cases:
    - analytics
    - user account management
  - Services:
    - POST /url (orginal_url, user_id)
    - GET /:shortened_url redirection
  - Metrics:
    - 300 mill URL per month (10 mill per day)
    - 100,000 seconds in a day
    - 100URLs per second
    - 300 mil URLs in a month * 500 bytes
      - 500 bytes for a URL
  - Dynamo DB s good for key-value pairs. SO we can use these for mapping the URLs to the short URLs

#### How do we store all the 8 char urls?

- hashing is one way, but encoding is 2 way.
- base 62 a-z, A-Z, 0-9

### Crazy math about figuring out how many random URLs you have to generate

- you might want to practice this before interviews
- but you don't want a pattern that can be figured out.
