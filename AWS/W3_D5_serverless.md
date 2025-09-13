### class notes

- serverless is different from traditional architechture,
- in traditional:
  - cost of managing
  - security risk
- serverless doesn't mean no servers. It just means it's abstracted away and you don't have to think about them.
- They are functions that operate in 

- **event bridge** handles system events
- 2 types of event:
  - pattern matching rules
  - schedule based rule (cron job)

  - short polling v long polling
    - for SQS: choose short, it's cheaper

### Lambda functions
- 1st decision; choose runtime (language: python, ruby JS)
- If you're going to use containers use ECS
- 2nd decision: resources: how many resources is it going to have.
  - Lambda can run for mximum 15 minutes. After that it will be dropped.
- Lambda functions are stateless
- If your lambda function is timing out you need to allocate more memory. This is something you get a feel for from experience. You never want to be close to 15 minutes though.
- Cloud watch allows you to read metrics for this.

### How lambda excecutes your code: 

- when it runs for the first time it;s the "cold start"
  - creates environment
  - allocates resources
  - downloads necessary packages
    - 100s of milliseconds
- It can also re-use this which is called the 'warm start'
- You are given some tmp )temporary disc space) when you stgart a lambda. If your function needs to reference the data, it can use this storage.
- Any code declared outside the function...
- THIS IS IMPORTANT IF YOU NEED LAMBDAS FOR THE CAPSTONE PROJECT, WHICH A LOT OF STUDENTS DO.
- 'provision concurrency' !? costs extra. does something.
### cloudwatch
- Cloudwatch -> a service used for monitoring and logging
  - performance metrics
  - logs
- cloud-watch alarms -> triggers an alarm when something happens.
- Native metrics collection
  - anything running in AWS cna be handled automatically by cloudwatch agents.
  - Even if you don't set it up, it can track EC2 instances.
  - But more specific things like memory aren't tracked automatically
- Cloudwatch logs
- Cloudwatch agent

### Elastic Transcoder

<img width="1440" height="900" alt="Screenshot 2025-09-12 at 17 34 03" src="https://github.com/user-attachments/assets/caef9ee8-2912-46d6-808d-e7b5e12a8536" />

### how to upload your modules to lambda

1. zip? yes but max 50mb
- or s3 bucket link to do zip, then you get 250mg
2. For more complex uploads use 'layers' -> some modules clumped together. Every lambda function can access a layer.
3. 3rd way => for huge numbers of modules. Deploy on docker containers (up to 10 mg) but we won;t use this

### ECR

elastic container registery 

### break out exercise:

- name: capstone_first_lambda
- 
