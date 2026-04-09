# Container-managed lifecycle 

- Container-managed lifecycle is when a [[framework]] or [[application-server]] controls the creation, initialization, usage, and destruction of application components.

## What is a “container”?
- A container is a runtime environment provided by a framework or application server, such as:
    - Servlet container (Tomcat, Jetty)
    - EJB container (WildFly, WebLogic)
    - Spring container
    - CDI container

## What does “lifecycle” mean?
- The lifecycle refers to stages an object goes through, such as:
    - Creation
    - Initialization
    - Usage
    - Cleanup / destruction

## You don't do

```java

MyService service = new MyService();
service.init();
service.doWork();
service.destroy();

```

## Examples by technology
### 1. Servlets (Java EE / Jakarta EE)

```java
@WebServlet("/hello")
public class HelloServlet extends HttpServlet {

    public void init() { }          // container calls this
    protected void doGet(...) { }   // container calls this
    public void destroy() { }       // container calls this
}
```

### 2. Spring Framework
```java
@Component
public class OrderService {

    @PostConstruct
    public void init() {}

    @PreDestroy
    public void destroy() {}
}
```

## Pros of container-managed lifecycle
- Reduces boilerplate code
- Improves consistency and safety
- Enables advanced features like:
  - Dependency injection
  - Transaction management
  - Security
  - Thread management
  - Scalability
- Promotes clean and maintainable architecture