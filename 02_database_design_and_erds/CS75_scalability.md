[CS75 (Summer 2012) Lecture 9 Scalability Harvard Web Development David Malan](https://www.youtube.com/watch?v=-W9F__D3oY4)

- VPSes
  - ...versus shared web-host: You still share resources, but you get your own seperate section.
    - But the VPS companies will have access to your data
  - They take a super fast server and chop it up with a hypervisor.
- [06:30] AWS EC2 can be used as a VPS which can scale up.
- [07:00] vertical scaling
  - physical limit: financial or hardware.
- [08:00] CPUs.
- A laptop with Quad core (like this one) can do 4 things at a time.
- Chopping up bigger servers into VPSes.
- [11:00] SATA drives, SAS, PARA
  - 720 RPM is the rate of the hard drive.
  - 15000 RPMs for SAS drives.
  - SSD (solid state drives) are smaller and faster.

### Horizontal scaling

- [13:45]
- [15:00] load-balancing, balancing the load for the back-end servers
  - the DNS returns the IP of the load-balancer
  - now the back end servers don't need public IP addresses
  - Private IP addresses are invisible to the whole world
  - Also the IPv4 addresses are running out.
- [23:00] Is a load balancer just a fancy DNS server
  - "round robin"
- [35:00] RAID
  - Redundant Array of Independent Disks
  - Stripe data across these drives.
  - [41:00] RAID is good practice even with desk-tops
### What else can we do to prevent single point of failure?
[41:50]
- shared storage:
  - Fibre Channel
  - Iscuzzy
  - MySQL -  a nice candidate because it's already a separate server.
  - Network File System (NFS)
- The most obvious way to mitigate the risk that your one file server goes down is - just get 2
  - syncing them (replication) is tricky, but doable
- [45:00] load balancers are over priced discussion. Could be 100,000 dollars. because of support contracts and the like.

### Break
[46:00]
- sticky session: even if you visit a session multiple times you're still going to end up on the same back end server
  - storing everything in cookies is impractical and inprivate. But you could save the IP of the visitor. The downside of this is the IP might change and it's a privacy thing. We can still implement the idea by issueing a random number and ahving the load-balancer rememeber it. Plus they can't spoof the cookie to do anything bad.
[51:00] PHP
- PHP acceleration
- PHP (now a recursive acronym for PHP: Hypertext Preprocessor) is a popular, open-source, server-side scripting language primarily used for web development to create dynamic websites and applications. It executes on the server to process code, generate dynamic HTML content, handle databases, and manage user interactions, making it the backbone of content management systems like WordPress. PHP code can be embedded directly within HTML, allowing for interactive and user-friendly web pages.
[55:00] caching -> saving the HTML so they don't have to generate it again.
