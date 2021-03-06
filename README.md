# microservices

##### characteristics (based on [Martin Fowler](http://martinfowler.com/articles/microservices.html#CharacteristicsOfAMicroserviceArchitecture) )

* **Componentization of Services**: component is a unit of software that is independently replaceable and upgradeable.

* **Organized around business capabilities**

* **Products not projects**

* **Smart Endpoints and dump pipes**

* **Decentralized Governance**

* **Decentralized Data Management**

* **Infrastructure Automation**

* **Design for failure**

* **Evolutionary Design**

##### pre requisites for taking up Microservices(based development)
[based on this article by Martin Fowler](http://martinfowler.com/bliki/MicroservicePrerequisites.html)

* **Rapid provisioning**: you should be able to fire up a new server in a matter of hours.

* **Basic Monitoring**: detecting technical issues (counting errors, service availability, etc) but it's also worth monitoring business issues (such as detecting a drop in orders). If a sudden problem appears then you need to ensure you can quickly rollback

* **Rapid Application Deployment**: you need to be able to quickly deploy them, both to test environments and to production.

* **DevOps Culture**: close collaboration between developers and operations- an important organizational shift is needed. 

## microservices design styles

![overview](overview.png)

**modern application platform**

![modern application architecture](modern application architecture.png)

### API Gateway

[Kong](http://getkong.org/): Open source management layer for APIs built on top of NGINX. Protect your services with authentication and security layers using oauth, key, basic, CORS etc.

[Tyk](https://github.com/lonelycode/tyk)

Tyk is a lightweight, open source API Gateway and enables you to control who accesses your API, when they access it and how they access it. Tyk will also record detailed analytics on how your users are interacting with your API and when things go wrong.
Written in [Go](http://golang.org/) language.

[OpenLoop](http://loopback.io/)

LoopBack is an open source Node.js framework built on top of Express optimized for building APIs for mobile, web, and other devices. Connect to multiple data sources, write business logic in Node.js, glue on top of your existing services and data, connect using JS, iOS & Android SDKs.

**Further reading**

[Build microservices: using an API Gateway.](https://www.nginx.com/blog/building-microservices-using-an-api-gateway/) [Chris Richardson](http://microservices.io/)

### CQRS and Event Sourcing

[Greg Young online tutorial ](http://www.viddler.com/v/dc528842)

This is a recording of an online class covering Domain Driven Design, CQRS, Event Sourcing, and the overall architecture around it.

[chris richardson: Building and Deploying Microservices with Event Sourcing, CQRS and Docker, QCON Jun13, 2015](http://www.infoq.com/presentations/microservices-docker-cqrs)

### Service

Follow 12 rules when implementing a service using [12 factor methodology](http://12factor.net/)

**CircuitBreaker pattern**

[Martin Fowler](http://martinfowler.com/bliki/CircuitBreaker.html)

CircuitBreaker pattern from Michael Nygard’s book ["Release It! Design and Deploy Production-Ready Software"](http://pragprog.com/book/mnee/release-it)

Microsoft Cloud Design patterns: [Circuit Breaker pattern](https://msdn.microsoft.com/en-us/library/dn589784.aspx)

**Bulkhead pattern**

**Timeout pattern**


**Service API (minimum)**

/info

{
   Version: "<major>.<minor>.<github commit #>.<git sha>.data.time,
   StartTimeEpochSecs: 1430515329,
   CurrentTimeEpochSecs: 143117131,
   Uptime: "167h10m2s"
   //service name
   //instance id
}

/connections

{
   currentUsercount: 1,
   currentlyAuthenticatedUsers: [{
      account: '',
      sessionKey:
      sessionDuration:
      publickKeyName:
   ]}
}

/health

### Communication between Services

Request/response - sync : binary RPC like [Thrift](https://thrift.apache.org/) or http or Google's [Protocolbuffers](https://github.com/google/protobuf)

Request/response - async: message passing

Event based : messaging middleware like rabbitmq/kafka

### Shared Services

* Service Discovery

* routing

* scheduling 

* logging

* health management

* metrics

* access control and authorization

    * user auth
        * oauth
        * JSON Web Tokens(JWT)
        
          [Build Secure User Interfaces JSON Web Tokens (JWT)](https://stormpath.com/blog/build-secure-user-interfaces-using-jwts/)
          
          [Token Based Authentication for Single Page Apps (SPAs)](https://stormpath.com/blog/token-auth-spa/)
          
          [use JWT the right way](https://stormpath.com/blog/jwt-the-right-way/)
          
        
    * service-to-service auth

* security

### Monitoring 

### deployment

[Ion Roller from Gilt]

[Bosch from Cloud foundry]

[Empire from Remind]

### Testing

[Testing strategies for microservices development](http://martinfowler.com/articles/microservice-testing/) by [Toby Clemson](http://github.com/tobyclemson)

### SERVICE TYPES

* caching service
* API management and gateway with correlation ID

 An easy way to correlate tasks at different nodes that belong to the same domain-level operation is associating a    correlation ID to the higher-level operation and let this ID flow through the system so you can later reconstruct the whole history of that operation as it went across the system.

* metrics
* monitoring
* Backing services(12factor)
* Metering and Billing

### Dependencies

[michael bryzek interview by infoq](http://www.infoq.com/interviews/michael-bryzek-handling-microservices)

 runtime dependencies
 compile dependencies
 
### References

Sam NewMan. [Answering questions (from Devxx) on Microservices](http://samnewman.io/blog/2015/06/22/answering-questions-from-devoxx-on-microservices/), Jun 22, 2015 	

[Sam Ramji, cloud foundry foundation](https://twitter.com/sramji). [The Makings of a Modern Application Architecture](https://www.youtube.com/watch?v=fiENlfVU7Ys)
