# Infrastructure Web Sécurisée et Surveillée

## Explanation of additional elements

1. **Firewalls (3)**:
   Added to filter incoming and outgoing traffic, protecting the infrastructure against unauthorized access and potential attacks.

2. **SSL Certificate**:
   Added to enable HTTPS encryption, ensuring the confidentiality and integrity of data exchanged between users and the website.

3. **Monitoring Clients (3)**:
   Added to collect data on the performance, security, and health of each server and the load balancer.

## Role of firewalls

Firewalls serve to:

- Filter incoming and outgoing network traffic
- Block unauthorized access
- Establish a demilitarized zone (DMZ)

## Why traffic is served over HTTPS

Traffic is served over HTTPS to:

- Encrypt the data exchanged between the client and the server
- Ensure the integrity of transmitted data
- Authenticate the website to users
- Protect the confidentiality of user information

## Importance of monitoring

Monitoring is used to:

- Monitor the health and performance of servers
- Quickly detect problems or outages
- Analyze resource usage trends
- Determine evolving needs

## Data collection by the monitoring tool

The monitoring tool collects data by:

- Installing agents on each server and the load balancer
- Retrieving system metrics (CPU, memory, disk, network)
- Analyzing application logs
- Performing availability and performance checks

## Monitoring the QPS (Queries Per Second) of the web server

To monitor the QPS of the web server:

- Configure the monitoring tool to collect web server logs
- Implement specific metrics to count requests
- Create dashboards to visualize real-time QPS
- Configure alerts for specific QPS thresholds

## Potential issues with this infrastructure

1. **SSL termination at the load balancer**:

   - Traffic between the load balancer and servers is not encrypted
   - Increases the workload of the load balancer
   - Can create a single point of failure for security

2. **Single MySQL server for writes**:

   - Single point of failure for write operations
   - Risk of data loss in case of failure
   - Limits the scalability of write operations

3. **Servers with the same components**:
   - Lack of resource specialization
   - Difficulty optimizing each server for specific tasks
   - Risk of uniform overload on all servers during traffic spikes
