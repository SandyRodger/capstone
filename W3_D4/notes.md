## work:

breakout room:
homework:
- very difficult, harder than yesterday's. Then the request bin work will be done.
- spend some time trying to figure out what is going on with AWS

### class

- 3 types of load balancer:
  - App load balancer (ALB) -> the main one you'll use.
  - Netowrk LB (NLB)
    - static IPs
    - traffic with super low latency (more for exams).
  - Gateway LB (GLB) -> even lower level. Network appliances like firewalls.

- LB's job is to accept connections form customers and distrubute them among other computer systems.
- Elastic container systems? EC2 instances
- When you deploy a load balancer you decide which subnet it should be in
- 2 types of app LD:
  - Internal -> private
  - External ("internet-facing")-> public
- choose one
- When you've set up the LB, you are given a DNS record, which points to the 2 nodes. SO when you send a request to the ALB, it uses a strategy (default is Round robin) to choose which instance to send this to.
- So you'll have 2 instances of the same subnet in different public subnets.
- Every node can communicate with every EC2 instance
- **target groups**
- Auto-scaling... we don;t need them now.
  - both out and in.
- what's the point
- **launch template** can be made from an instance
  - right click
  - 'launch more like this'
  - 'image and templates'
  - Scaling policies, so you don't have to do things manually.
  - Scheduled scaling is good for if you know that you will have additional need at a particular point (like a black friday scale0
  - Manual
  - Dynamic -> can be stepped (at 30% remove instance), can be  target-based
  - Cool down period -> when some action is performed wait a bit before doing another thing.
### Hibernation
- saves the RAM of an EC2 instance.
- warm-pools -> servers ready to go. These are servers in a stopped state.c (remember you pay for these even when they're stopped)

### S3 buckets
- it's regional -> so it's "regionaly resilient" if the region goes down ...
  - your data will never leave that region
  - 
- can store unlimited data
- very cheap.
- Perfect for images/videos/files (5 terabytes lmit on object size)
- good for large amounts of data.
- You can't do folders. If you try and make a folder, it's like github

### buckets and objects

- must be globally unique.
- upload and object
- 100 buckets limit
- by default objects are not versioned, but you can choose that. and with video files that can end up being a big ass file.
- There's no deleting in versioning. It just puts a 'delete' marker on it and it's hidden from you. 

### S3 -> static website hosting (CDN)

- tomorrow for the breakout room exercise.
- Point your website to the index document?!
- You can use your custom name for the bucket, but if you want it to link to your website, it has to have the same name as the website.
- Cost: very cheap. If you are doing statuc website hosting then there is also a cost per request.
- Basically using S3, you won't lose a lot of money

### S3 tiers

- unpredictable usage -> intelligent tiering
- glacier deep archive -> takes hours to retrieve the data

### Cloudfront (CDN)

- content delivery network
  - Edge servers near users, they can get it faster because the server's a geographically closer to the suer.
  - AWSCM (AWS certificate manager) interfaces with Cloudfront.
  - This evening for homework we will set up AWS certificates.
  - CDN terms:
    - origin: where the asset comes from/are.
      - Could be a specific S3 bucket.
      - Could be a database via a load-balancer
    - Distribution (break-out exercise today) -> containers for the configuration (origins, behaviors)
    - most configurations 
- security -> you have to be concerned about this
  - by default it should be private
  - OAC -> origin access control. Only allows access via the cloud-front
  - **resource policy** (we learnt about this on monday, but i don;t remember it) -> it's created and added automatically on the first distrbution only.
  - You can make a premium bucket!
  - Edge locations -> aws has 200 globally.
  - But there is also regional cache, there are fewer of these but they are larger!
  - manual invalidations to kill TTLs
  - 

### HWK

- 
