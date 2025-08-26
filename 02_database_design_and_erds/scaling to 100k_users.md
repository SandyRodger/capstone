# [scaling to 100k users](https://blog.alexpareto.com/p/scaling-100k)

- often solutions come from massive fires popping up or by identifying bottlenecks
- Many of the main patterns for taking a side project to something highly scalable are relatively formulaic. Here are 5 steps in that formula:

## 1. 1 user : 1 machine

- almost every app has 3 components:
  - an API -> serves requests for the data
  - a client (usually an app / website) -> renders the data for the user
  - a database -> stores persistent data
- It's helpful for scaling to think about the client as completely separate from the API.
- When we first start it's alright for all 3 to run on one server

## 10 Users: split out the database layer
## 100 users: split out the clients
- splitting out entities is a key aspect of building a scalable application. As one part of the system gets more traffic, we can split it out so that we can handle scaling the service based on its own specific traffic patterns.
### 1,000 Users: add a load balancer
### 10,000 users: CDN
- Content Delivery Network: a geographically distributed network of servers that caches and delivers web content, such as images, videos, and files, to users from a location close to their physical location. This process reduces latency and speeds up content delivery, leading to faster website loading times, improved user experience, and reduced load on the origin server
- we probably should have done this at the beginning
- CDN:  (in AWS this is an add-on called Cloudfront, but many cloud storage services offer it out of the box)
- A CDN will automatically cache our images at different data centers throughout the world.
### 100,000 users
Scaling the data layer is probably the trickiest part of the equation. While for API servers serving stateless requests, we can merely add more instances, the same is not true with most database systems. In this case, we’re going to explore the popular relational database systems (PostgreSQL, MySQL, etc.).
### Caching
The most common way to implement a cache is by using an in-memory key value store like Redis or Memcached
### Read Replicas
### Beyond
