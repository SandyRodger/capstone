### banter

- sharding is like Voldemort
- `Voldemort` Databases
- `cockroach` db.
- Topics get more and more complex
  - Background jobs
  - micro services
- but the good news is you need them less for the System design interviews we will have. They would be for top level interviews

### background jobs

- a job we have decoupled from the normal request/response cycle
- either
  - time based => cron jobs
  - event based => ie handling likes on twitter: someone likes, you incremement the counter
- example of a user signing up
**************************************************************************************************************
### Password
  - password goes to hashing algorithm
    - hashes are a one way street
    - bcrypt library
      - add salt
      - hashed password:
        - hash = the value
        - salt value
        - work factor => how many times the password is hashed. There are many rounds of hashing.
          - an integer in base 64. so if it's 12 it's 12^12.
          - a password with 1 upper char, 1 lower cahr, one punctuation and one number the quantity of possible passwords is impossibly high
**************************************************************************************************************

  - also user should have 'status'
  - Does the email confirmation come immediately?
    - Yes the response goes immediately to the user
    - Then we add a message to the queue to 

**************************************************************************************************************

### message queues

Very common:
- Point to point.

<img width="471" height="218" alt="Screenshot 2025-09-01 at 16 26 13" src="https://github.com/user-attachments/assets/792cc9ee-dac2-4f3d-82a4-83af61322ac5" />

- like a restaurant
- for instance SQS or RabbitMQ
- How does a consumer know something has been added to the queue?
  - push event
- Different queues do this differently
- SQS uses a pull queue with a long polling mechanism

- Either the queue is a pull queue or a push queue

#### Push queue
 
<img width="452" height="251" alt="Screenshot 2025-09-01 at 16 29 27" src="https://github.com/user-attachments/assets/ff9c3e03-4145-4fe7-a6cc-86eb8be8d198" />

- kafka
**************************************************************************************************************

### Kafka

- implements **pub-sub**
- basket-ball example:
  - what to do when there are mutliple queues to deal with a high amount of traffic?
  - The answer is **partitions**, which are like queues.
    - one partiton records data only for one particular event.
  - **consumer group** guarantees that each event will only be processed once within the group.
  - Groups can be subscribed to the same event, like:
    - inventory group
    - email group
    - analytics group
    - fraud detection group
  - **Topic** = a type of event
  - All of this is called a **broker**
- It doesn't matter HOW kafka does all this.
- Queue is point to point
  - but kafka means multiple things can be subscribed
  - When to add a group, when to add more consumers
- How does the producer send the data thta needs to be processed?
- Pubs => 1:M
- Consumer groups
**************************************************************************************************************

- returning to sending emails example
- (5) Dequeue job:
  -  third party, because sending emails is a very complicated thing
  -  then they use a webhook to confirm that the email has been sent.
-  Dead-letter queues -> where messages go when they get stuck in the queue for too long.
-  `kuri` -> dead-letter queue as a service.
-  Queues and caches are used ALL THE TIME (not sharding and some of the other things)
-  DL queues you have to set up, although AWS has their own. 
