# Sytem Scaling

System scaling is the process of upgrading your existing software infrastructure to meet the varying demands of client requests. It involves either vertical scaling (adding more resources to existing servers) or horizontal scaling (adding more servers to share the load) to improve the overall performance and reliability.

## Vertical Scaling

Vertical scaling is also known as scaling up the system. It increases the power of a single machine by adding more resources like CPU, RAM, storage, etc.

This approach is suitable for steady-state resource demands, such as databases, file servers, or web servers with consistent traffic.

## Pros of vertical scaling

1. **Easy implementation:** Since it is upgrading the existing servers and hence it is easier to implement.

2. **Less Complex:** Typically it does not require changes to the application architecture.

## Cons of vertical scaling

1. **Scaling limitation:** Since it upgrading a single server, therefore it can only be scaled to an extent.

2. **Expensive:** Adding more physical hardware can be expensive.

## Horizontal Scaling

Horizontal scaling is also known as scaling out. Instead of adding more resources to a single machine. It involves adding more and more servers and using a load balancer to distribute the client request evenly so that no server is overwhelmed.

This approach is suitable for applications with variable or unpredictable resource demands, where adding more machines can effectively handle the growing load.

## Pros of horizontal scaling

1. **Highly scalable:** Typically there is no limit on adding the number of servers as the application grows.

2. **High fault tolerance:** Since there are a lot of servers to handle the load, therefore if there is any fault, it can be easily handled by redirecting the request to another active healthy server.

## Cons of horizontal scaling

1. **Complex:** Since it involves multiple servers, the application architecture changes quite a bit.

2. **Management:** Managing many servers can be a complex task.

![Scaling](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*gee5Zkih2dZ7tYWRgmRbkw.png)

## Usage of load balancers

Load balancing is the process of distributing the network call requests or traffic of the application across various servers. It helps to evenly distribute the requests or traffic to the various servers improving the overall response time, and availability. It makes the system more efficient.

![Without Load Balancer](/assets/withoutLB.png)

![With Load Balancer](/assets/withLB.png)

## Types of load balancers

1. **Hardware load balancer:** These are physical machines that distribute the application traffic.

2. **Software as a service load balancers:** Softwares like Amazon Elastic Load Balancers, Nginx, HAProxy, Seesaw, Traefik, etc.

## Benefits of load balancer

1. **Scalability:** When the traffic grows, more and more servers can be added.

2. **Better availability:** If any of the servers fail, the load balancer is smart to redirect the traffic to healthy active servers so that continuous response can be found.

3. **Improved Performance:** As when the application grows and the number of users increases, load balancers distribute the traffic in a way that no server is overwhelmed ensuring reduced latency.

## Type of load balancing algorithm

1. **Round-robin:** It is the simplest algorithm that distributes the traffic in an order.

2. **Least Connection:** Traffic is distributed to the server with the least number of current connections.

3. **Least Time:** Traffic is distributed in such a way to the server through some calculations which will provide the fastest response time.

4. **URL Hash:** This algorithm generates a hash value based on the URL present in client requests. The requests are forwarded to servers based on the hash value. The load balancer caches the hashed value of the URL so that all the requests from the same client are forwarded to the same server.

# Conclusion

Systems need to scale as the application and traffic grows. However, there is no right method of scaling, it depends on a lot of factors like if the demand is increasing stably or if there is a huge spike in the growth of the application. Depending on the system requirement and the pros and cons of both horizontal and vertical scaling, we can decide what would be the best way to scale the system.
However, in industries, both qualities of horizontal scaling and vertical scaling are used where each server is scaled by adding more resources, and more number servers like these are scaled out.

# References

1. https://www.cloudflare.com/learning/performance/what-is-load-balancing/
2. https://www.vmware.com/topics/glossary/content/software-load-balancing.html
3. https://betterstack.com/community/comparisons/best-load-balancers/
4. https://www.youtube.com/watch?v=xpDnVSmNFX0
5. https://youtu.be/TO3yGao_Vjs?si=G6aKZy6XlEkkRBmB
6. https://youtu.be/sCR3SAVdyCc?si=NayVhzw0GpQ2bxFX
7. https://youtu.be/dBmxNsS3BGE?si=5KoySR_T_RB5SZSZ
8. https://medium.com/javarevisited/difference-between-horizontal-scalability-vs-vertical-scalability-67455efc91c
