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
