# [System Design Interview Prep: CDNs](https://www.tryexponent.com/blog/cdns-content-delivery-networks)

- a bunch of servers close to the users

## Problem Background
- much more performant:
- better speed and load times
- also give us scalability => so can deal with traffic spikes
- More reliabiltiy as they can deliver even if the origin server geos down
- Firewalls provided too
- save on bandwidth
- Better scalability

- ### cons:

- - can be expensive
  - tricky to set uop
  - there's a first-request delay
  - debugging is hard becasue the bug couuld be in many different places

## What are CDNs?
### popular CDNs
- Cloudflare CDN
- AWS Cloudfront
- GCP Cloud CDN
- Azure CDN
- Oracle CDN
### How do CDNs work?

#### Push CDN

- content owner has to manually push down content before the server serves it.
- Good at:
  - serving large files. Ensure that the content will be available at each node of the CDN
  - 
- bad at:
  - Set up is initially more complicated
  - continued maintenance  is more

#### Pull CDN

- this is the default one when we're talking about CDNs
- set up a pool of files to be available for caching on the CDN
- When a request is made the CDN sends out the file.
- So the first pull is high cost, then it's less.
- A resource which is popular in Asia is only cached there, US servers will have different resources
- Disadvantage:
  - first pull latency.
  - asset is not automatically propagated to all the servers.

### hybrid approaches
  - companies do a mixture of both.

### ...

- CDNs serve static files
- but if you want to serve dynamic files, these are just servers, they can run code, so you can do it there.
