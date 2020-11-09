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
