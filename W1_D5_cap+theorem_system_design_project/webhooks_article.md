# [Webhook failure scenarios](https://hermanradtke.com/webhook-failure-scenarios/)

- it's easy to get started, but it can go wrong in quite a few ways

### Terminology

- client -> the program that sends the webhook request
- origin -> the serveice that processes and then responds to the webhook request.

### Unhealthy Origin

- the most common failure
- the client sends a valid request, but receives a 500 HTTP response
- so many things can change or go wrong on the server:
  - updates
  - databases becoming unavailable
  - deploying a new verson of the service

### Invalid Requests

- the client sends a request that doesn't fit the origin's specifications
- could be a typo

### Network Error

- The client sends the request but it gets lost on the way.
- So many reasons for this to happen:
  - dns: can't find the IP address
  - tcp: error, like the origin has an unrecoversable error and 

### Origin Timeout
### Origin dropped Request
### Simple, not easy

