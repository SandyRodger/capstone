### Why EC2 instances are not used for databases

- If the instance goes down, you lose the data, which you NEVER want to do.

### RDS

- one of the most popular DB on AWS
- 'Database as a service' although that's not exaclty right. You get a server, upon which you can run multiple services.
- subnet groups
- cheap version
  - template -> sandbox (single AZ)
  - DB.t4gmicro
  - storage general purpose
  - disable everything else.
  - backup - enable automated -> disable, disable everything

<img width="1069" height="676" alt="Screenshot 2025-09-10 at 16 41 03" src="https://github.com/user-attachments/assets/7201e64c-0136-4d0a-b062-44e15d89c3dc" />

### Individual Exercise - 65 Minutes

Database Setup and Connectivity Testing

RDS Setup

1. Create an RDS PostgreSQL instance. Make sure to select the Sandbox option and disable all options that might incur costs:
Deploy in private subnets
Configure appropriate security groups
Create database subnet group
Note the connection endpoint
2. Test RDS connectivity
From the EC2 instance in the private app subnet test the connection to the RDS instance
psql -h <your-rds-endpoint> -U postgres

3. While connected to the RDS instance, create database for your request bin app.
