# Spring

- Spring provides a clean way to build enterprise applications by managing object creation, dependencies, and cross-cutting concerns without polluting business logic.
- **Key idea:** Spring manages application structure, not infrastructure.

### Before Spring:
  - Tight coupling (new keyword everywhere)
  - Business logic mixed with infrastructure
  - Hard to test code
  - Heavy container APIs (EJB)

### Core principles of spring
1. [[inversion-of-control]] (IoC)
   - Spring controls object creation and lifecycle, not the developer.
2. [[dependency-injection]] (DI)
   - Dependencies are injected instead of being created by the class.

### Spring Container
The Spring Container:
- Creates beans
- Injects dependencies
- Manages lifecycle

Types:
- ApplicationContext (most used)
- BeanFactory (basic)

### Beans
A Spring Bean is any object managed by Spring.
Defined using:
- @Component
- @Service
- @Repository
- @Controller

### Aspect-Oriented Programming (AOP)

AOP handles cross-cutting concerns like:
- Transactions
- Security
- Logging
- Caching

Example:

```Java
@Transactional
public void placeOrder() { }
```

Keeps business logic clean.

### Spring Modules (High Level)
- Spring Core – IoC & DI
- Spring AOP – Cross‑cutting concerns
- Spring JDBC / ORM – DB access
- Spring MVC – Web applications
- Spring Security – Authentication & authorization

### Spring Solved Vendor Lock-In
Application-server-based code depended on:

- WebLogic APIs 
- WebSphere config
- Server-specific behavior

Spring introduced abstraction layers:

| Spring Abstraction        | Hides             | 
|---------------------------|-------------------|
|PlatformTransactionManager | JTA, JDBC         |
|JdbcTemplate               |Raw JDBC           | 
|JpaRepository              |JPA provider       |
|Spring Security            | Server security   |

#### Same app runs:
- In Tomcat
- In JBoss
- Locally
- In the cloud

### Spring vs Application Server

| Application Server       | Spring                     |
|--------------------------|----------------------------|
| Manages infrastructure   | Manages application code   |
| Threads, pooling         | Object wiring              |
| Heavy, vendor‑specific   | Lightweight, portable      | 

 