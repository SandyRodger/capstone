### [Introduction to NoSQL • Martin Fowler • GOTO 2012](https://www.youtube.com/watch?v=qI_g07C_Q5I)

### Srdjan's questons:

- How NoSQL differs from relational databases
  - no schema
- How the different type of NoSQL databases work (document, key-value, etc)
- Use cases for NoSQL databases (why would someone use them)?
- Shortcomings of NoSQL databases

- Any questions you have

### Impedence mismatch

- [02:40] 

### The big change: lots of traffic

- [04:00]
- SQL was designed to work on one machine, not lots of little machines like horizontally spread databases.
- "unnatural acts" to try to do so.

### The NoSQL movement

- [06:00]
- DEeining a thing by what it isnt?!
- Johan Oskarsson set up NoSQL meetup group.

### Definiton of NoSQL

- [07:30]
- It's undefinable.
- But here are some characteristics:
  - non-relational
  - open-source
  - cluster-friendly
  - schema-less
  - 21st century website culture

### Data model

- [09:40]
- 4 data models:
  - document
  - Column-in-family
  - Graph
  - Key-value
    - all of these are schema-less
#### key-value store

- No schema
  - but querying data involves an implicit schema

#### document model

- storage of a whole mass of data, in some kind of structure
- Usually json
- "schema-less" no schema: any stuff you like, you can stuff in there (but that's not the whole truth)

### aggregate oriented databasses

- [15:40]
- These are:
  - Document
  - Column-family
  - Key-value
    - not Graph.
- 'Domain driven design' -> Eric Evens
- How to think about modelling designs
  - When modelling data it makes sense to agggragate similar, but different objects.
- Getting one item from the database.
  - in KV database we are retrieving the value
  - in document database we are retrieving the document

### column_family

- [17:40]
- more complicated than the 2 before.
- easier to retrieve than the others.
- related data stored in one database together
- So retrieving data means you only go to one DB
- BUT if you want to aggragate according to a different column, it's a pain. It's doable -> mapReduce jobs to rearrange all your data, but it's more complicated than relational databases.

### Graph database

- [22:30]
- Nodes and arcs
- good at handling mpving across relationships between things
- Relations is not relationships

### consistency

- [25:50]
- ACID
  - atomic
  - consistent
  - isolated
  - durable
- NoSQL are not this (alhtough graph databases do!)
- They are BASE (but this is bullshit)

- [30:00] write-write conflict
- [33:00] offline lock
  - give each aggragate a version stamp

### two types of consistency

- [38:30]
- Logical & replication
- sharding data -> you still have the same logical consistency problems wyou would get with a single machine.
- hotel room booking example: consistency v availability. It's a choice that must be taken when considering the business. The business have to decide.

### CAP theorem

- [40:00]
- If you have a system that can get a network partition => you must choose between consistent OR available
- If there's no partition possible, so eveything on the sam emachine you don;t need to think about this.
- However the choice isn't 100% binary. There are levels of consistency and availabilty you can tweak.
- A lot of the time what you're really trading is consistency and response-time. Because the more nodes you have involved the more consistent the system is (?)
- it's a business decison. Like AMazon want fast shopping and high availability.
- trADE : CONSISTENCY & RESPONSE-TIME

## Further study

- in memory structures saved dirrectly to disk
- open-source
- caches as being a single point of a dist-sys.
- difference between key-value & document database (blurry difference -it's an approximation)
- What is a database cluster?
