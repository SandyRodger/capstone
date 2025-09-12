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

 ### trying to get it to work the next day...

-----BEGIN PUBLIC KEY-----
MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEA0QNNXmzq0dFicOCQ527j
3WMDSBYZAy9co0OZwDWRq2Yg+RCtpDzXO181V+ubJdWZ5Kb/FcrzedPfD0XluJzB
9z0OrTYakisTD7jSSCvyD/4qzkeoT6M5D1yxSD92pK+ntTlEqjnnaW9albZNjoeR
U7HenijwfpdEj5UNSfEr3AFxEEXAzjgQhB986rMzzSFGSy+DVjhOhBiZrAMPWb95
M8icxmJ1AwDbRsjaqLOwbT49mkuwHABYTZTmMwNqBiceuS8IreAMzihI3x9xEH0M
XgFFAgh6DJfPGA+0fBvGoHzjuEOuCrQH4N1huLsXdO+J8qMSXfAZwnZTVb9rsG8+
dQIDAQAB
-----END PUBLIC KEY-----

PremiumContentKey
PremiumAccessGroup

E1EC46Z3UVD7M2

aws cloudfront sign \
  --url https://d18d7xhu7u80d9.cloudfront.net/premium/lon35481-teaser-xxl.jpg \
 --key-pair-id K1CMO4AMZIXLU0 \
 --private-key file://private-key.pem \
 --date-less-than 2025-12-31

key: K1CMO4AMZIXLU0
 
https://d18d7xhu7u80d9.cloudfront.net/premium/lon35481-teaser-xxl.jpg?Expires=1767139200&Signature=zBPlmEyE6PQPjBj8aMoyvAaWYqoaRg6uPeOYB~vij1EdCz5-4aKhA2c8EvS45zcg58aj7TXQ1tsG4p~wEm8LhNaex6P70LeNJ0OM0l0xuszKarOmG3-UL~6I4c14~MtC718-EA~8JNL-kLyHyEzdDwijopoH8y0E9D-8Zsnonvs~l~uK-1pj8tUOX5tT0103Iwuy9dMLeQK-GX4b5WWXBW-WNw9begmhAps04NsVZHxEdibA1aO9~ElQ5r3ZOPHEpY2RaymHZjqrKGTf2VYEgqxbGt7taSafR8xVA-j5KrAL8O1J2a5iFlHaEAgMn1BKeO29BAVr9GZdBLX4~ufDFg__&Key-Pair-Id=E1EC46Z3UVD7M

- bug: my origin access was set to public rather than origin access control settings. I will need to be more careful about following instructions.

bug:
<img width="718" height="222" alt="image" src="https://github.com/user-attachments/assets/90bf343b-ed98-4521-9234-6927d68fe613" />

Solution said:
<img width="1301" height="402" alt="image" src="https://github.com/user-attachments/assets/05ee518d-7f0f-4ab8-9758-f33085ed5ac1" /> 
