### IP addressing -> Preston's mini lecture

10.0.0.0/24
32 - 24 = 8
10.0.0

CIDR/Subnet mask = what's not available

-----------------

10.0.1.0/25
32 - 25 = 7
2^7 = 128
10.0.1.127

---------------

subnet mask is the portion you CANT USE

### Class!

- this week we'll cover
  - EC2 instances
  - Lambda
  - different databases
- You can take the AWS exam later if you want. It's not necessary for Capstone.
- Goals:
  - prepare for capstone project
  - be able to put AWS on CV.
- Homework: put request bin on AWS.
-Today:
  - what is coud computeing. why is it important
  - Why AWS,and not another clud provider?
  - IAM
    - policies
    - users
    - roles
    - admin account
  - VPC (not VPS)

  ### Before Cloud
  - "on prem": your own server, small as a laptop, big as a Warehouse full of racks.
  - You need space, cooling, security, IT support, backups
  - Scaling is hard, easy to wrongly predict and get it right
  - Before cloud there were 'hosting-providers'
    - shared hosting
    - dedicated hosting
  - BUT it was still servers. You commited to servers for a monthly or annual contract.
  - CLOUDS change the game Bro. You can be super specific. I want x GBs for x seconds
  - These can be upscaled and downscaled with a button.
  - You only buy and use a portion of a server.
### AWS
  - AWS had 200+ services, so they can basically do anything for you.
  - Also they're really reliable.
  - Downsides:
    - less secrecy
    - Costs -> pay-as-you-go sounds great, but in practice managing this is a lot of work for big companies. Many of them may be underutilized but they're still wracking up bills
    - You can save tens of thousands by tweaking these things. You can also horribly screw yourself over.
    - You can forget to turn things off and they still cost you.
    - They also have an eco-system that pulls you in to using more of them.
    - There are even businesses that work on your behalf to negotiate contracts with AWS.
    - (DON'T DO DEPLOYEMENTS AND TESTING ON FRIDAYS)
    - in general AWS is very reliable, but in June 23 it went down and that had huge ramifications.
    - AWS has 33% of the market share. It's the biggest one, with the largets community
    - We're using a standard account, but there are many different types.

### Demo

- Use the search bar. Save time.
- Go to
  - budgets
  - monthly limit $10

- we've created root user, but we want to have other users:
  - people in our organization
  - Ourself
- "least privileged access"
- users -> Set permissions
- IAM ?
- Users -> real people / non-aws programs
- Groups -> collections of users who are related
- Roles -> when you want to give access to an uncertain number of entities -> role.
- You always have to create access, but for lambdas they can be created with a template all having the same access rights

### policy statements

- these are automatically created when you create something
- Security
  - JSON
  - combines all policies attached to a entity, goes through them and decides whether it's allowed to access or not.
  - Effect = allow/dent
  - Action = what service? => :* eveything
- Explicit deny over-rides everything else. Order does not matter

### inline policy

- attached to each individual user

### managed policy

- for groups

### ARN 

- Amazon Resource Names
- "Bucket" rather than "directory"

### Limits

- there are limits.
  - limit 5000 users per account.
  - 1 user can be in max 10 groups
  - you can create max 300 groups per account

### Access

- ssh (access keys) -> you can have max 2. Because they can be set to inactve/active.
  - for apps
  - via the command line
- username & password -> only one exists

### groups

- contianers for users
- can't have groups within groups
- Good for :
  - management of users
    - add users to group
    - attach policy to group
  - "Resource policy"
