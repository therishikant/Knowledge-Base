1\. WebLogic
--------------------------

- WebLogic Server was a [[java-ee]] (later Jakarta EE) compliant [[application-server]] developed to run, manage, and scale enterprise Java applications reliably. 

2\. Core design philosophy
--------------------------

WebLogic had three foundational ideas:

1.  **[[container-managed-lifecycle]] lifecycle**
    *   WebLogic decided when applications started and stopped
2.  **[[centralized-resource-management]]**
    *   JDBC, JMS, security, threads were shared and pooled
3.  **Declarative configuration**
    *   Behavior was defined through config, not hard-coded

This was the reason lifecycle events and shutdown hooks existed.

3\. How WebLogic was structured (Architecture)
----------------------------------------------

### Domain (Top-level boundary)

A WebLogic Domain was the highest unit of configuration. It contained everything needed to run applications.

Inside a domain:
#### Admin Server
*   Was the control plane
*   Managed configuration
*   Provided the admin console
*   Did not handle business traffic
    
#### Managed Servers
*   Were runtime workers
*   Actually ran applications
*   Handled:
    *   Client requests 
    *   Transactions
    *   Database access
        
#### Cluster (Optional)
*   A logical group of Managed Servers
*   Used for:
    *   Load balancing
    *   Failover
    *   High availability  

**Note:**  Application ran only on Managed Servers.

5\. What happened when WebLogic started
---------------------------------------
### Server startup flow (simplified)
1.  JVM started
2.  WebLogic bootstrap classes initialized
3.  Core services started:
    *   Thread pools
    *   JNDI
    *   Transaction Manager
    *   Security services
4.  Managed Server connected to Admin Server
5.  Server entered RUNNING state

At this point, WebLogic was ready to deploy applications.

6\. What happened when an application was deployed
--------------------------------------------------

When Application was deployed:
1.  WebLogic created a classloader hierarchy
2.  Application descriptors were read:
    *   application.xml
    *   weblogic.xml
3.  Resources were linked (JDBC, JMS)
4.  Application components were initialized:
    *   Servlets
    *   EJBs
    *   Listeners
        
5.  Application lifecycle events were fired:
    *   PRE_START
    *   POST_START

After this, the application was available to receive traffic.

7\. How request processing worked
---------------------------------

At runtime:
1.  A request arrived (HTTP, JMS, etc.)
2.  WebLogic accepted it through a listener
3.  A thread was taken from a managed pool
4.  Context was established:
    *   Security
    *   Transaction 
5.  Application logic executed
6.  Response was returned
7.  Thread was released back to the pool

The application never owned threads or connections—WebLogic did.

8\. How WebLogic managed resources
----------------------------------

WebLogic maintained **pools**, not per-request resources:
*   JDBC connection pools
*   JMS session pools
*   Thread pools

9\. When shutdowns occurred
---------------------------
Shutdowns could be triggered by:
*   Admin stopping a Managed Server
*   Node Manager restart
*   Server crash
*   Application redeployment
*   OS or JVM termination

From WebLogic’s perspective, shutdowns were **normal events**, not failures.

10\. What happened during shutdown (critical part)
--------------------------------------------------
### WebLogic shutdown sequence
1.  Shutdown signal was received
2.  Server state moved to SHUTTING\_DOWN
3.  **New requests were stopped**
4.  **Application lifecycle events were fired**:
    *   PRE\_STOP
5.  WebLogic waited for in-flight work (grace period)
6.  Application was stopped
7.  Resources were cleaned
8.  JVM exited

If applications did nothing during PRE\_STOP, WebLogic had no guarantee that:
*   Threads would stop
*   Transactions would finish
*   Resources would be released

11\. What went wrong without graceful shutdown
----------------------------------------------
Without proper handling:
*   WebLogic waited until timeout
*   Forced thread interruption occurred
*   Transactions rolled back abruptly
*   Database locks remained
*   Shutdown times increased

This was the root cause of **slow, unsafe shutdowns**.

## Resources
1. [[java-ee]]
2. JDBC 
3. JMS
4. Threads
5. [[application-server]]