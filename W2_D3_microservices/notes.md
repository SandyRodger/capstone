### Ido's Etsy talk

#### Database stuff

SQL
sharded database environment (1000 shards) across MySQL databases.
Horizontal
But no stateless. Which elads to significant complications
- What are these shardless ddbs?
  - each db has the same scheema, but the rows are different
  - DIfferent users stored across different shards
  - User's id is the **shardifying key**
- a lot of complexity come with sharded databases
- They are still vulnerable:
  - some hot key
  - tricky query
    - slows things down
- There was a seperate database for storing data about the shards (index database)
- This means we lose some strengths of relational dbs
  - we can;t use foreign keys
  - have to be super careful about joins.
  - Schema changes have to run across each of thos hundreds of shards.

### The sharded dbs are vulnerable & complicated

- They try to take care of most of the work in the application layer.
- 

### Questions:

- wide column databases?
  - not at Etsy, although they are used in analytics
  - They are a little too slow for Etsy
  - Also the pages aren't static
- How did the transition to working at a large company go?
  - 'onboarding' it's a lot
  - especially if you;re joining a company that has a large code base
  - learning ot read other peiple's code take a minute
  - a while to be productive
  - Etsy were understanding that there is a while it takes to get up to speed
  - THere should be resources to help you
- (Ryan) WIth a sharded db how do you determine which data goes where?
  - this is why Etsy had this lookup table. ALternatives to that would be hashing or a "modulo type of thing"
  - The problem is if you ever have to change all of that. SO you avoid the problem by keeping the lookup table.
  - Yes it costs to maintain that, but if for instance a shop grows to an enormous size and their listings  are carrying a lot of work. It becomes much easier to just move that shop up to another shard. You haven't effected everyone else.
  - which eases the hotspots
- (Tyler) LAMP stack -> did you need to know PHP?
  - No. Even 5 years ago it wasn't considered a hot language
  - In the interview they needed just a bit of JS and Python.
  - But there's an understanding that if you don;t know the language but know the concepts then you ca pick them up quickly
  - Also PHP from 5 years ago is totally different to how it is now
- Sharding difficulty: how quickly can you respond to a hotspot
  - It almost never happens.
  - If health metrics start looking really bad, the first thing people will ask is, 'did some deployment go bad?'
  - So it's seldom the correct culprit. But this is why thye now do dry runs of changes.
  - Another way to improve metrics is change caching.
  - But if something is slowing down the website it can't be left like that for a day.
- (Teddy) Redis -> how do you use it's features
  - they had been using memcached.
  - 2 main uses
    - cache layer -> I have this key, ehres the value for it
    - a materialised data layer
  - Microservices:
    - They use no microservices.
    - Etsy is one monolith!
    - It just has a ton of different routes.
    - Then when a web-server gets a request for a specific route it know where to send that
  - (salah) what could be some solutions to the shard lookup database.

- (Zane) Etsy is a monolith, but that comes with problems, how do you deal with these?
    - they have a strange deployment strategy.
- (wilson) can you expect this architecture to be the same in 2 years?
  - Yes, it works pretty well.
  - The bottle nexck was the index database. Becuase if that went down no one could look things up.
  - Part of the strength is that the architecture is so simple.
- Saurabh: Has ai changed the interview process:
  - Last he checked in February it had not changed.
  - There are new roles to do with AI, but 6 months ago it was
    - Stage 1: leet code
    - on-site: different intervies, system design
    - debug something with me
    - given these requirements how would you structure a data store to deal with this.
    - Very PEDACy
- sal: micro-services:
  - no microservices. Stupidly so. There are talks online about it
  - The main pain-point before was just knowing where all the code was. But now that PHP has more native support for name_spaces, it's a lot better
