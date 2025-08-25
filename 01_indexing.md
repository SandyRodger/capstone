Indexes
What are they?
Table-like structure that can be created based on one or multiple columns (if supported) sometimes called a "compound" index.
Creating index tables allows us to look at what information is most often used/retrieved, and to create index tables that make that data readily available. 
Indexes are pointers to data (column or columns) in the table they reference
When designing an index you can design the way the index is structured to make look-up more efficient. The most common structure is a B-tree structure (not to be confused with Binary tree), which makes it easy to find data with range-based scanning and sequential scanning. There are many other index designs available.

Why are they useful?
They maximise the query’s efficiency
We can use index tables to collate all of the row ids that match a particular data point. For instance in an author_idx table we would have a row for a particular author which would contain references to all rows with that author in the dataset.

What are their advantages and disadvantages?
Advantages:
Faster retrieval of data
Instead of searching an entire table for data, an index reduces the amount of data being scanned to return the desired data
Efficient data access
Indexes are typically stored on disk; however, frequently accessed indexes are cached in RAM for quicker access
Better utilization of system resources
More efficient queries results less overall work for a system (CPU/Memory/I/O), which then allows the system to handle a higher amount of queries
Disadvantages:
There is a performance cost associated with making sure that the index is up-to-date as the dataset changes. For instance if a new author is added then the index has to add a reference to this author. For this reason it can be inefficient to have too many index tables



“If you need to access data quickly, you index it. If the performance of data access isn't a concern, you don't index it. That's 90-percent of what you need to know about database indexing.” - Ben Nadel



