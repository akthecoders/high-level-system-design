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


