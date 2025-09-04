- [Read how Instagram scaled to 14 mil users](https://read.engineerscodex.com/p/how-instagram-scaled-to-14-million)
- Read - sections 1-4 of the [Apex writeu](https://apex-api-proxy.github.io/)p (stop before section 5 - Design and Architecture). 
Sections 1-3 will give you a good breakdown of microservices, while section 4 will introduce service meshes and API proxies (used in Homework section below)
Service Meshes, API Gateways, and Message Queues represent 3 different microservice communication patterns. Feel free to either read or watch videos on these. If you feel comfortable with the concepts after doing either the reading or watching the videos, don't feel like you need to do the other for completeness.
- Read -[Service Mesh VS API Gateway VS Message Queue](https://arcentry.com/blog/api-gateway-vs-service-mesh-vs-message-queue/)
- [service mesh video](https://youtu.be/vh1YtWjfcyk)
- Video - [What is a Service Mesh?](https://www.youtube.com/watch?v=QiXK0B9FhO0)
  - sidecars to offload communication heavy-lifting.
  - control tower
  - Control tower + sidecar = service mesh
  - Istio + Envoy
- Video - [What is an API Gateway?](https://www.youtube.com/watch?v=vHQqQBYJtLI)
  - needs:
    - SSL certificates
    - Authentication
    - Authorization
  - These are seperate to business logic. It's the API gateway.
  - Feature 4: routing
  - Feature 5: 
- Video - [What is a Message Queue and where is it used?](https://www.youtube.com/watch?v=oUJbuFMyBDk%C2%A0)
