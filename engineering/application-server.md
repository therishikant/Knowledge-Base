# Application Server
- An application server is a managed runtime that executes enterprise applications while handling all infrastructure concerns on their behalf.
- The server implements the [[java-ee]] APIs and provides the runtime to execute them.

It sits between:
*   **Operating system / JVM**
*   **Enterprise application code**

Examples:
*   WebLogic
*   JBoss / WildFly
*   WebSphere
*   GlassFish  
  
### Before application servers existed, Java applications:
*   Opened raw database connections
*   Managed threads manually
*   Handled security logic directly
*   Failed unpredictably under load

### What an Application Server provides
*   Thread management
*   Database connection pooling
*   Transaction management
*   Security (authentication, authorization)
*   Messaging (JMS)
*   Lifecycle management (start/stop events)
*   Resource management (JNDI)
*   Clustering and failover (optional)

### Core concept: Containers
An application server runs applications inside **containers**.
Common containers:
*   **Web Container** → Servlets, JSP
*   **EJB Container** → Business logic
*   **Persistence Container** → JPA
*   **Messaging Container** → JMS

Containers manage lifecycle, security, and transactions.

- Application Code        <--YOUR code (business logic)    
- Framework (Spring)      <-- STRUCTURE & WIRING  
- Application Server      <-- INFRASTRUCTURE       
- OS / Hardware                                  

### Examples
- WebLogic
- JBoss / WildFly
- WebSphere

### Resources
- [[weblogic]]
- [[java-ee]]