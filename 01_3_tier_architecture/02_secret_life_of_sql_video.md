### The secret life of SQL video

#### Rule 1: any columns involved in queries should be covered by an index

- ...(but avoid redundant/unused indexes)
- ... and sometimes it's better to use an index prefix.
- When to use an index prefix?
  - long data type
  - querying data that works well with prefix (like, give me all names beginning with 'a')
- How long should we make the prefix?
  - long enough to differentiate values in this field
  - base if off of real data if possible
- What do we gain from using an index prefix:
  - It takes less space
  - you gain the ability to index big data types
  - you can get the same performance improvement as using a full index if you craft it carefully.

#### Rule 2: Use an OR to return records satisfying one or more conditions

- figure out with EXPLAIN
- When to break this rule:
  - if the table is really big, so a full table scan isn;'t performant
  - the use of OR is preventing any index from being used

#### Rule 3: if there's an index over all the fields in your query, you're all set

- when to break the rule: except when the query planner doesn't know which index to use, in which case tell it.
  - FORCE INDEX
  - USE INDEX
  - IGNORE INDEX
- Can be a problem i fthe index is deleted later

#### WHen are we going to break the rule of not having redundant data across tables

-  Additional reads (JOINS) are causing noticeable performance degradation
-  High ratio of reads to writes
-  So we decide to denormalise data and have redundant data across tables

#### Rule 4: avoid redundant data across tables
-  except when you are JOINing on another table for almost every request, and it's getting costy and you have high volumes of reads to writes for this data
