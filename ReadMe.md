<h1>System Design</h1>

Horizontal vs Vertical Scaling

Horizontal

1) Load Balacing Required
2) Resilient
3) Network Calls(RPCs)
4) Data Inconsistency
5) Scales very well as per users.

Vertical Scaling
1) NO Load Balacing Required
2) Single Point of Failue
3) Inter Process Communications
4) Consistent
5) Hardware Limit


<h3>Load Balacing</h3>
When we want to evenly distribute requests along the N servers.

Consistent Hashing

