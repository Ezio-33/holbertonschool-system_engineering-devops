# Infrastructure Web Évolutive

## Added Elements and their Justifications

1. **Additional Server**:
   Added to allow component separation and improve infrastructure scalability.

2. **Clustered Load-balancer (HAproxy)**:
   A second load-balancer is added and configured in a cluster with the existing one to eliminate the single point of failure in load balancing and improve service availability.

3. **Component Separation**:
   The components (web server, application server, database) are now on dedicated servers for the following reasons:

   a. **Dedicated Web Server**:

   - Optimized to handle HTTP requests and serve static content.
   - Allows independent scaling of the web layer.

   b. **Dedicated Application Server**:

   - Focused on executing application code.
   - Facilitates resource optimization for specific application needs.

   c. **Dedicated Database Server**:

   - Optimized for database operations.
   - Improves performance and data security.

## Advantages of this Scalable Architecture

1. **Better Scalability**:
   Each component can be scaled independently according to needs.

2. **Improved Performance**:
   Resources of each server are optimized for their specific task.

3. **Simplified Maintenance**:
   Updates and maintenance can be performed on each component without affecting others.

4. **Enhanced Security**:
   Component separation allows better isolation and implementation of specific security policies.
   The use of different firewalls also enhances security against attacks.

5. **High Availability**:
   The load-balancer cluster eliminates a critical single point of failure.

## Additional Considerations

- This architecture increases infrastructure complexity and costs, but offers better flexibility and optimized performance.
- A backup and disaster recovery strategy should be implemented for each server.
- Monitoring becomes even more crucial to monitor the health and performance of each separate component.
