<h1>System Design</h1>

Horizontal vs Vertical Scaling

Horizontal

1) Load Balacing Required
2) Resilient
3) Network Calls(RPCs)
4) Data Inconsistency
5) Scales very well as per users.

Vertical Scaling

1) No Load Balacing Required
2) Single Point of Failue
3) Inter Process Communications
4) Consistent
5) Hardware Limit


</br><h3>Load Balacing</h3>
When we want to evenly distribute requests along the N servers.


</br>Consistent Hashing

Consistent Hashing is a technique where we take a ring of servers
We create virtual servers i.e we take a server and then take multiple hash functions
Now whenever there is any incomign request then with each request we will have multiple options because of hash funciton to go to servers.
So even if a single server goes down then the load is evenly distributed.

</br>Messaging Queue

Message Queue is a concept where the incomfing requests are stored into a DB before reaching to actual servers for request completions
This type of queue is required when we need a queue to hold things .example Pizza shop order coming in.

</br>Monolith vs Microservice 

Monotith is less scalable - Microservice are very much scalable
Single point of failure - No single point of failure
Single system handle everythin - Multiple system have there individual responsiblity.

</br>Sharding

Paritioning the load between multiple servers.
It have a problem of Joins, which is very tough.

</br>Distrubuted Caching

Benefits of using Caching ?
1) Save Network Calls
2) Save Recomputations
3) Reduce DB Load
4) Speedup Responses

Cache Policy -> How to insert and delete data from the cache.
1) LRU
2) RFU

Write Through and Write Back Cache


System Design

Requirement Section
    Functional Requirements
        Instead of just lines, we can write as apis
        Ex: 
        Add new Board createUser(userId, userObject) userId
    

    Non Functional Requirements 
        Requirements which we don't have to take in account
        Assumptions 

Scaling
    Bandwith Estimation
    Storage Requirement

CAP Theorem
    CP System 
    AP System

Choosing and Reason to Choose it

DataBase Designing
    While Designing DB , do not write all the details of tables, just write the important one and leave the rest as per the time.
Tip:Learn the limits of the particular db, its limits etc.

While Designing the Diagram of System Design
1) Can use Draw.io or google board
2) Talk about the tradeoffs in the system
3) Talk about regions and other things which you are doing.

1) Caching - Put the cache in between Microservices
2) Search
3) Recommendation System
4) SideCar - Put a sidecar box in the API for sending metric to external API for loggging.
5) Notification 
6) Service Discovery
7) Inter service communication is via queue if response comes in more time approx 1 ms, else we can make is synchronous.
8) Service Registery -> Where all microservices register itself
9) API Gateway
10) Circuit Breaking -> Circuit breaking is a portion create in the side of microservice.
    It supports that if a service which the current node is calling, gets fail. then the circuit breaker in the current node
    can do various operation instead of returning error.
    1) Can return cached response.
    2) Can redirect the request to another alternative (temp) API.
    3) Help in recovering the failed node -> it keeps checking the failed node , if it has come up or not.
11) Service Mesh - 
    It is an extra component which runs parallel to every Microservice which helps in. We can use Sidecar pattern, where every microservice will have an instance of Service mesh.
    We make call to another microservice via the service mesh, In short we will call the service mesh and it will inturn call the other api. 
    - Load Balancing
    - Service Discovery
    - Metrics
    - Retry
    - Circuit Breaking
    - Timeout

Microservice Deployment Pattern
Things which we want to achieve
- Scalabitliy and throughput
- Reliable & Available
- Isolation
- Resource Limit
- Monitor
- Cost Effective

Patterns
1) Multiple Services per Host -> run more than one MC on single VM.
    Adv:
        Efficient resource utilization
        Fast Deployment
    Dis:
        Poor Isolation
        No resource limit
        Dependency conflict

2) Service per Containers/VM
Adv:
    Isolation & Secure
    Manegable
    Fast
    AutoScaling
Dist:
    Slow(Only with VMs not with containers)

3) Serverless
Adv:
    Focus on code only
    No worries about scaling
    Pay as you go
Dis:
    Runtime support
    Expensive
    Vendor lock
    Debugging pain
    Stateless and short running process only.

## Distributed Transactions
1) 2 Phase
2) 3 Phase
3) Saga
 
## Chaios Enginerring

## Chap Netflix

