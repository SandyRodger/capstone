### Google doc with AJ

- Indexes
- What are they?
- A copy of selected columns in a table-like structure which can be searched quickly & efficiently
- An Index is sorted.
- We choose which columns to index by deciding what data is most useful
- An index will have the same number of rows as the table it is referencing.
- There are different structures possible for an index. The most common is a B-tree structure (not to be confused with Binary tree), which makes it easy to find data with range-based scanning and sequential scanning.
- Why are they useful?
- They maximize the query’s efficiency. Because they are sorted we can go directly to the part of the index that matches the search query.
- When learning about indexes the analogy of a book with an index is often used. Instead of checking every page for the data we need we can go to the index to find exactly where it is.
- What are their advantages and disadvantages?
Advantages:
Faster retrieval of data
Instead of searching an entire unsorted table for our data, an searching within a sorted index reduces the amount of time it takes to locate our desired data. We then can know exactly where to find additional data within the main/unsorted table We then have pointer(s) to the  that it references within its original table being scanned to return the desired data
Efficient data access
Indexes are typically stored on disk; however, frequently accessed indexes are cached in RAM for quicker access
Better utilization of system resources
More efficient queries results less overall work for a system (CPU/Memory/I/O), which then allows the system to handle a higher amount of queries
Disadvantages:
There is a performance cost associated with making sure that the index is up-to-date as the dataset changes via modification operations (INSERT, UPDATE, DELETE). For instance if we had a books table, and an index of authors of that table, and added a new entry, book/author, is added  then the DB must update the index as well to maintain data accuracy. This adds overhead to the system (consuming resources) indexes that has to add a reference to this author. Therefore, a balance must be found between leveraging indexes for quick access, and performance degradation as a result of having too many indexes. For this reason it can be inefficient to have too many index tables, and a balance must be found between 



“If you need to access data quickly, you index it. If the performance of data access isn't a concern, you don't index it. That's 90-percent of what you need to know about database indexing.” - Ben Nadel

