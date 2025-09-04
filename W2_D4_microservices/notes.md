### API gateway
- in a microservice architecture you always awant an API gateway. No microservice -> no API gateway
- you can have it internally, but typically it controls client to server api requests.
- Srdjan's comparison:
  - What webserver is to the rest of out aplication, the API gateway is to our microservices.
- it's the gateway surrounding your city.
- It acts as a:
  - load balancer
  - health checks
- Deals with North to South traffic (client is North, microservices are south)
- If a service is down we stop sending requests to it => "**circuit breaker**"
- It has sophisticated way to check authentication.
- Different to service mesh because it does service to service communication.

### Side car proxy -> service mesh

- Control plane & side-car = service mesh.
- Handles east-west traffic.
- Where does it live physically?
  - In the pod where the container for the service is.
### Control plane

- Control plane is deployed as a seperate service.
- Istio ?
- They're hard to maintain. They require experienced engineers. Don't add unecessary complexity unless you have to
- **canary** deploy for 5% of users, see how it's received and slowly increase.
  - for example aria
- **blue/green** deployement
