[CS75 (Summer 2012) Lecture 9 Scalability Harvard Web Development David Malan](https://www.youtube.com/watch?v=-W9F__D3oY4)
(1hr 45mins)
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
- They can also be set up in software instead of buying hardware

### Break
[46:00]
#### the need for sticky session
- sticky session: even if you visit a session multiple times you're still going to end up on the same back end server.
  - storing everything in cookies is impractical and inprivate. But you could save the IP of the visitor. The downside of this is the IP might change and it's a privacy thing.
  - We can still implement the idea by issueing a random number (like a hand-stamp) and having the load-balancer remember it.
    - it's a little more work on the load balancer, but we're not putting ANY states on the user computer.
    -  Plus they can't spoof the cookie to do anything bad.
  -  So load-balancers can be configured to send out a cookie. (in the `setCookie` header)
[51:00] A word on PHP
- (and interpreted langages in general) get a bad rep for performance because they tend to not be as performant as a compiled language (like C++)
- PHP acceleration: we can combat this by using this.
  - it saves the html in `.php` files so doesn't have to generate them from new every time.
  - python does the same thing with .py files
  - It's easy and free to enable.
#### caching
[53:00]
- can be bad if the data is state
- [53:30] memcached ("mem-cash-D")
  - looks at craigslist.
  - They are saving the html and storing it on disk, as opposed to storing the data in the database and retrieving it each time to genereate the page dynamically.  
  - So this is a type of caching. The upside is that web-servers lke apache are really good at just spitting out bits.
  - The downside of this is there's redundancy because you're saving a lot of duplication.
  - Also if you want to change the appearance of the page, you would have to tinker with each page. You may jave to re-generate all 10,0000 (or wtv) pages.
#### PHP definition (chatGPT)
- PHP (now a recursive acronym for PHP: Hypertext Preprocessor) is a popular, open-source, server-side scripting language primarily used for web development to create dynamic websites and applications. It executes on the server to process code, generate dynamic HTML content, handle databases, and manage user interactions, making it the backbone of content management systems like WordPress. PHP code can be embedded directly within HTML, allowing for interactive and user-friendly web pages.
### MySQL Query cache
- [59:00]
- provides this caching for identical queries
### memchached
[01:00:00]
- a memory cache
- (Facebook uses it a lot)
  - becasue it gets way more reads thann writes
- Saves whatever you want in RAM
- Disk -> slow
[01:02:00]
- MySQL is a server, so it's always running
- key value stores are much faster than databases
[01:04:00]
- cache gets too big
- do a garbage collection
- Expire objects based on when they were put in. (FIFO)
### MySQL
[01:08:00] 
- the storage engine: the underlying format to store youre data.
- Heap engine
#### replication
[01:11:00]
- master-slave connection (network connection)
- The slave exists to copy the master database
- slaves can easily replace the master if it fails.
- slaves can be backups, but they can also balance read requests
- The downside is...
  - what is one dies? There is still a single-point of failure, because if one server dies we can't perform writes until a new server is loaded.
  - So let's have 2 masters: code if server1 connect fails, go to server2
### multi-tier architecture
-[01:18:00]
- still not perfect:
  -  The mySQL master could fail
  -  The load balancer's could fail
-  Load-balancers -> when you buy them you typically get 2:
  -  active-active
    -  they send heartbeats to each other. if one ever stops hearing the other's, it assumes it has to deal with everything.
   - passive-active
### partitioning
[01:22:00]
### high availability
[01:23:30]
- this is the name for 2 machines checking each others' heartbeats
### overview
[01:25:00]
- sticky-sessions: the load-balancer listens (at an http level) and adds a session token which enables it to remember where that client was in terms of servers
- if the user makes a persistent change and later comes back on a different computer -> problem:
  - we could connect the databases with master:master replication
- (I'm slightly losing the thread...)
[01:34:00]
- what if the power goes out
- cloud computing is just outsourcing your services.
### global load balancing

 [01:37:00] Geography based load-balancing
 - the more users and revenue you have, the harder these problems become
- Q: what type of internet traffic should be coming outside in to the server building if I'm hosting a website?
  - tcp80 & 443 & port 22 for SSH
### firewalls

[01:43:00]
- there's no need for randos to be making SQL queries from outside
- follow the principle of least-prviledge.
