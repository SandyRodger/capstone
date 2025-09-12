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
