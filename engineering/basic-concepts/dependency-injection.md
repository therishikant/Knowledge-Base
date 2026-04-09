# Dependency Injection (DI)

## What
Inject dependencies instead of creating them

## Why
- Reduce tight coupling
- Improve testability

## Example
Service → uses Repository (injected)
```java
    @Service
    class OrderService {
        OrderService(PaymentService paymentService) { }
    }
```

## Used In
- Spring

## Solves
- Problems in EJB (tight coupling)

## Trade-offs
- Harder to understand initially

## 🔗 Links
- [[Inversion_of_Control]]
- [[Spring]]
- [[Tight_Coupling]]