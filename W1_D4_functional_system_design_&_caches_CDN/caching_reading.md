# Mastering the art of caching for system design interviews

## What is it?

- It's French bruv.
- caching is temporarily storing frequently accessed data in a cache, which is faster to access than the original source of the data.
- The cache is a high-speeed storage layer that sits between the application and the original source of the data
- Analogy: It's like a travelling library that takes books to remote villages so these people don't have to each travel to the city to get books

<img width="344" height="207" alt="Screenshot 2025-08-29 at 11 30 53" src="https://github.com/user-attachments/assets/1983894a-901f-4525-95aa-d2a4d03f9d50" />

- There are different ways to cache. Here are some popular ways:
  - in-memory caching
  - disk caching
  - database caching
  - CDN caching

### In-memory caching

- stores data in the main memory of the computer, which is faster to access than disk storage.

### Disk caching

- stores data on the hard disk
- slower that main memory
- faster than retrieving data from the remote source

### Database caching
- seems like a contradiction, what it means is: using the memory on the database server:
  - analogy of a bookshelf outside the main library.
- stores frequently accessed data in the database itself
- reduces the need to access external storage

### CDN caching

- stores data on a distributed network of servers
- reduces the latency of accessing data from remote locations

## Why is caching important?

- Improves performance + user experience
- Reduces response time + latency of operations
- Results in faster + more efficient processing

### How does it help?

- **Improve system performance**: reduces the number of times data needs to be fetched from the source. So the app is faster and more responsive.
  - ie it only takes 20 minutes for a villager to get a book, instead of 3 hours
- **reduce network load**: minimizes the amount of data that needs to be transmitted over the network. It's stored locally so you don't have to fetch data from the original source
  - ie each book travels along the road once, instead of every single time a villager wants a book
<img width="340" height="207" alt="Screenshot 2025-08-29 at 11 25 53" src="https://github.com/user-attachments/assets/5a976f78-9bef-46c9-9891-21a42fc8e0e1" />
- **Increased scalability** it makes an app more scalable by reducing the load on the original source.
  - so now the librarians in the main library have more time to organise travelling libraries because they aren't having to serve individual villagers all day.
- **Better user experience** faster response times and reduced latency can lead to a better user experience
  - the country's literacy levels improve because reading for pleasure becomes so easy.

### Types of caching

1. In-memory-caching
- faster than disk-storage
- good for data that can fit into the available memory (?!) -> "In-memory caching is useful for frequently accessed data that can fit into the available memory."
- Commonly used for:
  - API responses
  - session data
  - web-page fragments
- Often implemented with:
  - cache library:
    - Memcahced
    - Redis
  - custom caching logic in the app
2. Disk caching
- slower than main memory, but faster than not caching
- Good when:
  - data is too large to fit in memory
  - data needs to persist between application restarts
- commonly used for:
  - db queries
  - file system data
3. Database caching
4. CDN caching
5. DNS caching

### Cache replacement policies
1. Least Recently Used
2. Least Frequently used
3. FIFO
4. Random Replacement

### Comparison of different replacement policies

-LRU and LFU are more effective but have a performance cost due to complexity

### Cache invalidation strategies
- write through cache : write to cache and DB simultaneously. total consistency and protection from crashes. Higher latency for writes.
  - over-write
- write around cache : write directly to storage bypassing the cache
  - so cache record gets deleted? (implied)
  - This is the exception becasue we aren't saving to the cache
- write back cache : data is only written to the cache. Data is only written to permanent storage under certain conditions
  - update the cache and then update the database when a X (like cache is full)
- write behind cache: similar to above, but data is written to permanent storage at specified intervals.
  - when you write data you're saying "I am going to invalidate anything on the cache relating to that data"
### Cache invalidations methods
- purge: everything related to a URL
- refresh: always retrieves from origin server and refreshes the cache.
- ban: any cached content matching the criteria is removed
- time-to-live: after some time the data is removed
- stale-while-revalidate: "Well here's what I got, let me just check it's the latest one"
### Cache performance metrics
- It's important to measure performance:
- hit rate: percentage of requests that the cache can cover without having to ask original source
- miss rate: the opposite of the above
- cache size: the amount of memory/storage allocated for the cache
- cache latency: time it takes to access data from the cache. Lower cache latency means it's faster and more effective
### Conclusion
