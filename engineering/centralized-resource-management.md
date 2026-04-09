# Centralized Resource Management
- Centralized resource management in an application server is the mechanism by which shared resources such as threads, memory, and database connections are controlled, pooled, and allocated by the server centrally instead of being managed individually by applications.

## What are “resources” here?
- CPU and memory
- Database connections
- Threads
- Network connections
- Transaction managers
- Security and authentication services
- Caching mechanisms

## What does “centralized” mean?
- Instead of each application or component directly creating and managing these resources:
- The application server manages them centrally
- Applications request resources from the server
- The server decides how, when, and how much to allocate

## How centralized resource management works
1. Resource Pooling
   - The server maintains pools (e.g., connection pool, thread pool)
   - Applications borrow and return resources instead of creating new ones
2. Lifecycle Management
   - The server creates, initializes, monitors, and destroys resources
   - Applications don’t worry about cleanup or optimization
3. Policy-Based Allocation
   - Server applies rules like:
   - Max connections per app
   - Thread priorities
   - Timeout limits
4. Monitoring & Tuning
    - Central metrics (usage, load, performance)
    - Easier tuning without changing application code
  
## Common Application Servers Using Centralized Resource Management

- Apache Tomcat
- JBoss / WildFly
- [[weblogic]]
- WebSphere
- GlassFish