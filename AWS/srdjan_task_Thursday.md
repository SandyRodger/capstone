### Steps to take now:

- Understand the difference between public and private subnet. Find subnets and see how one has connection to Internet Gateway and that is the public subnet and we deployed webserver there and we also deployed NAT gateway there
- Private one doesn't have access to IG, and to grant ec2 instances access to internet we had to connect that subnet to NAT gateway
- Next check security groups but delete most, only keep ones that are used web-sg , app-sg , postgreSQL-sg mongo-sg . Try to understand inbound rules in each one of them. Use AI for help for understanding of everything. See why app instance has one security group that is different than web-sg which is attached to web server then check RDS and its security group and how it is different and then check documentdb and its security group
- Once you understand all of that you can, if you have time, check the Nginx configuration in web server (also ask AI to explain it to you and what each part means).
- This should be enough. After that you can remove everything
