### EC2: Elastic computing cloud

- it uses power/memory/network/storage to execute some operations
  - it just gives you CPU and RAM
- AWS lambda also does this (it's a serverless function - we'll cover it later this week)
- It's a server
- It gives you access to virtual machines
  - infrastucture as a service

### elastic IP

- a static IP that never changes.

### IGW versus NAT GW

- IGW has a map with kv pairs
- NAT gateway is a one way street out.
- All ipv6 addresses are public?

- Egress-only internet gateway

## stop start instance

- it gives you a different address, because the EC2 instance is set up on a new server.

### instances can be

- running
- stopped
- terminated

### What are we billed for?

- CPU
- Memory
- Network
- Storage (if you pause, you still pay for this)
  - EFS
  - EBS storage(ephemeral)
  - instance storage

### AMI

- Amazon machine image
- Images your code.
- Use these to create EC2 instances.
- They're like templates
- perfect for server-style apps. that run all the time
- You can run Docker images on EC2 instance, but don't. You should use ECS (plastic ... ...)

### Types

- General purpose EC2 instance -> the default
  - steady work-load
- Compute optimised
- Memory optimized
- Accelerated computing:
  - 3D rendering (high gpu requirements)
- storage optimized -> provide large amounts of super fast storage
- You can tell what they are based on the first letter.
- M -> memory (ie M5dn8xlarge)

...

- `iops` input/output per second -> how many different things we can do in a second.
- `thoughput` -> how much data we can move in a second.
  - (bandwidth is the Network, throughput is just data)

### EBS

- a type of storage
- block storage(?)
- strictly operates in one AZ.
- general purpose SSD storage -> gp2 and gp3
- always use gp3 (cheaper & newer)
- Provisioned iops
- EXAM QUESTION: provisioned iops is the only version that you can attach to multiple instances. ("multi-attach")
- Cold HDD
- SD1
- SC1 -> for archiving (?)

- IP masquerading

## S3 buckets

- snapshots. You have to pay for them

### Lazy loading

- the first data access request is slow
- FSR (Fast Snapshot Restore) is the solution, but it costs more.

### EFS -> elastic file store

- uses mount-targets -> 1 per AZ

### Spot instances:

- you set the maximum price you want to pay and if the demand exceeds that the instance dies
- like a weak bridge, cheap to build but flimsy

- reserve something for 3 years. but if you don;t need it for that long you;'ll burn money
- dedicated host: for licencing things (whatever that means)

### cluster placement groups
### spread placement groups
### partition placement groups

- everything is 'on demand' until you want something else
