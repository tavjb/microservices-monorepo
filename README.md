# Microservices

## This is a spring-cloud based microservices project that consists of several git repos:

### Infrastructure:
  config-server (https://github.com/tavjb/config-server):
    Includes the spring-cloud-config-server library, provides configuration for the microservices, the
    actual configuration is at: https://github.com/tavjb/microservices-config
    
  discovery-server (https://github.com/tavjb/discovery-server):
    Includes the spring-cloud-eureka-server library, microservices reigster as clients to the discovery service,
    whenever a service requries another service's address, the discovery server provides it, which means services don't have
    to be aware of IPs and ports of eachother, moreover, the discovery server manages multiple instances of each service
  
### Microservices:
  greeting-service (https://github.com/tavjb/greeting-service):
    An application that exposes a simple 'greeting' RESTful api.
    This app is both a config client and a eureka client.
    This app depends on time-of-day-service and communicates with it using a 'feign client' which also controls the load balancing
    which means that each call to the time-of-day-service could arrive at a different instance of the application
    
  time-of-day-service (https://github.com/tavjb/time-of-day-service):
    An application that exposes a simple 'time-of-day' RESTful api.
    This app is both a config client and a eureka client.


To run docker-compose stack: ```docker-compose -p "microservices" up```
