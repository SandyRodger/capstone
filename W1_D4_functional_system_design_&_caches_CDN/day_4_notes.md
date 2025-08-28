## Day 4 notes:

### helpful measurements:

- a database can handle 1,000 queries per second (read, write, whatever) -> but we're going to concentrate on the read queries, assuming that the write queries are handled by the write server.
- App server maybe 200 - 300 requests per second
- webserver 100,000 to 1,000,000 -> so you don;t need to worry so much about this. Because it's doing a very simple thing. It's designed to do a simple thing fast.
- (everything we talk about here is per second).
- assume read to write ratio is 100:1
  - so yes read/writes take different times, but we concentrate on reads.
### How to divide by 10000

100,000 seconds in a day (rounded up)
2, 000, 000, 000
20 thousand per second
- pick numbers so it's always just adding or removing zeroes.
- 
### Metrics Formula
- every number is an assumption - unless they tell you!
1. Start with an (high) amount of monthly active users (MAU)

200 MAU

2. Take a percentage that are daily active users (DAU)

100 millions id the nice round number of estimated users. (Daily active users DAU)
  - Twitter(X) for instance now is 100 million

3. Come up with an average number of daily requests that a single active user would make:

- 10 ?


4. Get total number of requests in a day by multiplying DAU X number of daily requests for a single active user.

- peak load
  - slack's is super low, maybe 2x
  - ticket master when Taylor Swift tickets go online are 100,000x

5.Get an overall QPS for the application by dividing total number of requests in a day by 100,000 (a day actually consists of 86,400 seconds, but we're rounding up for simplicity)
6. Determine a read/write ratio that makes sense for the application.
7. Apply a read/write ratio to QPS to get read and write QPS.
8. Multiply these by your peak load multiplier to get peak read/write QPS
9. Determine how many databases you need based on the QPS numbers



## Where Do Metrics Fit In?
- With the interviewer, clarify requirements and scope the main use cases you want to design for this interview
- Services breakdown (less common in real interviews)
- ERD and/or schema design
- Design the services to meet their functional requirements (ex: "the system must do x") with the SQL statements use to interact with the database
- Estimation of Metrics (less common in real interviews)
  - it's impressive if it comes up!
- Scaling to n-tier architecture (driven by metrics)
- Further scaling paths, including caching considerations, database options, background jobs, horizontal partitioning, etc.

###
1 million is megabytes (6 zeroes)
1 billion is gigabyte (9 zeroes)
1 trillion is terabyte (12 zeroes)

### write heavy apps:

- games
- stock trading
- telemetry
- they don't use SQL.

