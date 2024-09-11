# Infrastructure Web Distribuée

## Explanation of additional elements

1. **Additional server**: Added for redundancy and load balancing, improving system availability and performance.

2. **Load balancer (HAproxy)**: Distributes incoming traffic between the two servers, optimizing resource utilization and improving service availability.

3. **Separate application server**: Allows for better separation of responsibilities and easier scalability of the application layer.

## Load balancer distribution algorithm

The load balancer is configured with the Round Robin algorithm. This algorithm sequentially distributes requests to each available server in turn. It is simple, fair, and efficient for uniform workloads.

## Load balancer configuration: Active-Active

In this configuration, all servers simultaneously process traffic, maximizing resource utilization.

- **Active-Active**: All servers are operational and process requests simultaneously.
- **Active-Passive** (not used here): One server is active, while the others are on standby and only become active in case of the primary server's failure.

## Primary-Replica database cluster operation

In our Primary-Replica (formerly Master-Slave) configuration:

- The Primary node handles all write operations.
- Replica nodes are synchronized with the Primary and handle read operations.
- In case of Primary failure, a Replica can be promoted to Primary.

## Difference between Primary and Replica node for the application

- **Primary**: Handles all write operations (INSERT, UPDATE, DELETE).
- **Replica**: Used for read operations (SELECT), reducing the load on the Primary and improving read performance.

## Potential issues with this infrastructure

1. **Single points of failure (SPOF)**:

   - The load balancer is a potential SPOF.
   - The Primary database node is a SPOF for write operations.

2. **Security issues**:

   - Lack of a firewall, exposing the infrastructure to potential attacks.
   - No HTTPS, compromising the confidentiality and integrity of data in transit.

3. **Lack of monitoring**:
   - Without a monitoring system, it is difficult to detect and quickly respond to performance, service outage, or security issues.
