### capstone

- no software engineering experience, although he had done small jobs in the tech space
- "like being married to 3 people without the perks" -> high stres -> lots of decision making.

### job history
- Multiple companies since then
  - 1st: a Start up 'Gatsby' -> fun chaos
  - acquired then on to a later stage start up
  - move to 'Out-school' (always wanted to start a school)
    - company was very chaotic
  - Wistia -> video website. Like youtube, but for marketing.

### Implementation of a daily notification digest

- "Create a notification digest system that will send a daily notification at 5pm local time for the user"
- specs
  - create a notification digest,
  - send to users globally 5pm local time
  - all events that have occured throughout the day/week.
  - **figma design**
- what questions do you ask:
  - what does a notification look life?
  - how are we sorting the items in "new leads"?
  - What is the average usage of a typical user? Number of regular events?
    - mode interface, with redshift
    - columnar databases
    - 1.62 million events last month
    - 3.2 million users in total
    - 2 events epr month ?
  - Is there a message queue?
    - No, no kafka type setup, although they do have queueing systems.
    - There are outlier accounts. Super-huge customers. These don't get included in the statistics, because they would skew the numbers.
    - Currently notifications are in a rails app. There are hooks that are triggered when an event happens like data is stored. This stores data in the database, which has a huge number of entries.
  - Is there a database storing
 
#### solution:
- if you do everything at once and schedule the notification to  go out later. But then it's a lot of work to do in one go.
- It's 2 core problems -> scheduling and creating the digest. They're both expensive in terms of SQL queries.
- SQL EXPLAIN
  - what will the db try to do in order to excecute this query.
### indexing
- We can make our SQL query a little bit faster by using an index. The SQL queries with otherwise be messy and super long
- Statement timeout: if a query takes longer that n, it will get cut.
- question: does the comapny stack restrict solutions you could come up with?
  - yes. The company's been going for 20 years. To change anything would take a significant amount of effort and would ripple out.
### stack
  - MySQL
  - _________
  - Rails
  - Sidekick

###

- on the job it'll feel like a fire-hose, but it will slowly come together.
- You inherit code from other people (9/10 times) so you have to work within those restrictions.
- The junior move is to add a new thing or switch to a new thing, but for the job you need the ability to say based on where we are this is what we could do to support what we're trying to do, and leave ourselves some room to allow us to go in a better direction.
- "prefer doing cursor pagination over limit offset"
- 

### Questions

- how do people fail interviews
