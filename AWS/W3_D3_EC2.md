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

### setting up an IAM user:

password: spandex9-9


### homework

- preston's note:
```
go to nginx
make a location called /api that points to your localhost server
make a reverse proxy
Preston Macy (Capstone)
3:41 PM
"build": "tsc -b && vite build --mode development",
Preston Macy (Capstone)
8:17 PM
server {

root /var/www/requestbin;
index index.html;

location = / {
try_files $uri $uri/ =404;
}

location /api {
proxy_pass http://localhost:3000;
proxy_http_version 1.1;
proxy_set_header Upgrade $http_upgrade;
proxy_set_header Connection 'upgrade';
proxy_set_header Host $host;
proxy_cache_bypass $http_upgrade;
}
Preston Macy (Capstone)
8:22 PM
postgresql://localhost/mydb?user=other&password=secret
const conString = "postgres://YourUserName:YourPassword@YourHostname:5432/YourDatabaseName";
```

### Steps I have taken:

- Create a new branch of the repo called `aws-ec2-setup`
- Problem: My EC2 instance is not connecting
  - solution attempt:
    - Actions → Networking → Manage IP addresses → Associate Elastic IP → Allocate → Associate.
      - 18.233.73.159
    - make sure that the subnet has an Internet Gateway route:
      - cap1- 3 subnets are associated with the NAT gateway
      - pick subnet "cap4"
### Move your existing instance into a public subnet -> FAIL
Stop your instance (EC2 → Instances → select → Instance state → Stop).
Once stopped:
Actions → Networking → Change subnet → pick a public subnet.
Then: Actions → Networking → Manage IP addresses →
Tick Assign new public IP (or better, allocate and associate an Elastic IP).
Start the instance again.
Security Group: make sure it has inbound rule → SSH (22) from My IP.
Now try Connect → EC2 Instance Connect with username ec2-user (Amazon Linux) or ubuntu (Ubuntu).

### make a new EC2 instance -> FAIL
- my associated subnet: subnet5 is not public. So now I must attach an IGW to my VPC and then update the subnet's route table
  - VPCs -> capstone_test' VPC -> Internet gateways -> `capstone_test` -> ... nothing
  - Subnets -> cap4 -> route table = `rtb-0f2d0fa9ec05685f9`
  - go to that route table -> edit -> add routes -> destination 0.0.0.0/0 -> target internet gateway
  - Enable Auto-assign public IPv4 for the subnet (so new instances automatically get public IPs).

### Change security group seetings to let everyone have access:

The bit you’re asking about (“what CIDR block should I use?”) controls who on the internet can reach your instance.
Common choices for Source (CIDR block):
Only you (safe for SSH):
87.74.227.221/32 (your current IP address).
→ This means only your computer can SSH in on port 22.
Everyone (for web traffic):
0.0.0.0/0
→ This means anyone on the internet can hit your EC2 on that port.
Use this for HTTP (80) and HTTPS (443) if you want a public website.
Don’t usually use it for SSH unless testing.

### A list of my subnets:

- Cap1 - nat - Private
- Cap2 - nat - Private
- Cap3 - nat - Private
- Cap4 - igw - Public
- Cap5 - igw - Public
- Cap6 - igw - Public

- Capstone route table has Cap1, Cap2, Cap3.
- Subnets without explicit associations: Cap4, Cap5, Cap6
- Nat gateway is associated with Cap2

### Questions for Srdjan on Thursday morning:

- Am I doing the homework for Tuesday and Wednesday seperately or as one ->I guess as one, ie thursday's work orverriding the requirements of Wednesday's work.
- In homework instructions for yesterday if says "MongoDB workload on DocumentDB (private subnets)" -> why 'workload' here but not in the postgreSQL
