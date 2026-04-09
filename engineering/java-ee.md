# Java EE

- Java EE was a specification for building enterprise Java applications.
- Java EE = contract
- Application Server = implementation

## What it included
- It provided standard APIs for:
    - Web applications (Servlets, JSP) 
    - Business logic (EJB)
    - Database access (JPA)
    - Messaging (JMS)
    - Transactions
    - Security
  
## Why it existed
- It existed to:
    - Standardize enterprise Java development
    - Ensure applications were portable across servers
    - Let application servers (like WebLogic) handle infrastructure

## How it worked
  - Developers wrote applications using Java EE APIs
  - Application servers implemented those specifications
  
## Who provided the actual working code?
| Specification 1 | Implemented by 2 |
|-----------------|------------------|
| Servlet API     | WebLogic / Tomcat|
| EJB             | WebLogic         | 
| JPA             | Hibernate        |
| JMS             | Weblogic JMS     |
| Transections    | Weblogic         | 



## Resources
[[application-server]]
[[weblogic]]