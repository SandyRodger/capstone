### Steps to take now:

- well the app isn't working, and it was working last week. So It'll be a little harder to test. and I don't have the time to get it all running again now.

1. Understand the difference between public and private subnet. Find subnets and see how one has connection to Internet Gateway and that is the public subnet and we deployed webserver there and we also deployed NAT gateway there.
  - The public subnets are associated with the `rtb-0bb4fce26ae1cace9 | public` route table, and that route table has 2 routes listed, one of which is the IGW `igw-0416f60cc5599da34`. Which means it can be accessed from the internet. THis is what makes it public.
    - This IGW has the destination 0.0.0.0/0, which means all outbound & inbound traffic is routed via this gateway
    - These public subnets are the ones that run the web-browser, which is the front-end of the app. So it is appropriate that they are public.
  - The private subnets are associated with a different route table `capstone_route_table`.
    - This route table is not associated with a IGW. However it still has to have access to the internet in order to download dependencies and other things. So it is associated with a NAT gateway, which is like a one way (outbound only) IGW (two way).

2. Private one doesn't have access to IG, and to grant ec2 instances access to internet we had to connect that subnet to NAT gateway
  - This refers to the 4 subnets that comprise the back-end. They needed to not be accessuble by the internet (private) but to still be able to download dependecies via the NAT gateway.
  - In fact the NAT gateway itself sits in a public subnet which is why the subnet route table sends "0.0.0.0/0" to the NAT's ENI. 

3. Next check security groups but delete most, only keep ones that are used web-sg , app-sg , postgreSQL-sg mongo-sg . Try to understand inbound rules in each one of them. Use AI for help for understanding of everything. See why app instance has one security group that is different than web-sg which is attached to web server then check RDS and its security group and how it is different and then check documentdb and its security group.
  - I have 17 security groups. Most of these were created by mistake.
  - I should keep:
    - postgreSQL-sg: accepts only inbound from app-sg on 5432
    - ec2-rds-2 or ec2-rds-1, I'm not sure which
    - app-sg: accepts inbound only from web-sg, on port 3000
    - web-sg: accepts inbound only from 0.0.0/0 on port 80/443
    - mongo-sg: accepts only from app-sg on 27017.

  - I should delete:
    - launch-Wizard-4
    - launch-Wizard-5
    - launch-Wizard-2
    - launch-Wizard-1
    - launch-Wizard-3

4. Once you understand all of that you can, if you have time, check the Nginx configuration in web server (also ask AI to explain it to you and what each part means).

 
 
This should be enough. After that you can remove everything
