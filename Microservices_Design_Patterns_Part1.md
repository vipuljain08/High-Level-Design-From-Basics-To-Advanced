# Microservices Design Patterns Part 1

- [Monolithic Architecture](#monolithic-architecture)
- [Microservice Architecture](#microservice-architecture)
- [Microservice Phases](#microservice-phases)
- [Decomposition Pattern in detailed](#decomposition-pattern-in-detailed)

## Monolithic Architecture
- A `Monolithic Architecture` is a traditional model for building applications in a single unit, self contained and independent from other applications. 
- It couples all of the business concern in a single codebase. Therefore to make change in any service requires building and deploying the entire application repeatedly that makes updates and deployment time-consuming. 
- Monoliths can be convenient in early stage of project `SDLC` for ease of code management, faster development and deployment.

## Microservice Architecture
- A `Microservice Architecture` relies on multiple independently deployable services. Means, these services have their own business logic and database with a specific goal. 
- Updating, testing, deployment and scaling these independently services are easy to manage.
- Microservices are loosely coupled, means we can update one service without impacting another.

![Monolith_Vs_Microservice](./assets/images/Monolith%20Vs%20Microservice%20image.png)

## Microservice Phases
- `Decomposition`
    - Decompose by business capabilities
    - Decompose by sub-domain
- `Database`
    - Database per service.
    - Database shared between services.
- `Communication`
    - Restful APIs
    - gRPC
    - Web Sockets (Event Streaming)
- `Integration`
    - API Gateway
- `Deployment`
    - Containerization with **_Docker_** or **_Kubernetes_**
    - Serverless Architecture with **_AWS Lambda_** or **_Azure Functions_** or **_Google Cloud Functions_**
    - Virtual Machines (VMs)

## Decomposition Pattern in detailed
Decomposition Pattern helps us how to decompose monolith application into multiple smaller microservices. <br>

Various strategies we can follow:
<br>
- On Business Capabilities
    > Aligning microservices with business capabilities ensures that each service is focused on delivering specific business functionalities, facilitating easier management, scalability, and alignment with business goals.

    **Example -> _Ecommerce Application_**
    ```
    - Authentication Service
    - Product Management Service
    - Order Management Service
    - Account Management Service
    - Payment Gateway Service
    ```

- On Domain Driven Design: 
    > By applying DDD, you structure your microservices around bounded contexts that reflect the domain's complexities, ensuring clear boundaries and reduced coupling.

    **Example -> _User Management_**
    - **Domain Model:** User, Profile, Address, Role
    - **Responsibilities:** User registration, login, password management, profile updates.
    - **Microservices:** User Service

    **Example -> _Product Management_**
    - **Domain Model:** Product, Category, Price, Specification
    - **Responsibilities:** Managing product listings, categories, product searches
    - **Microservices:** Product Service, Category Service

    **Example -> _Order Management_**
    - **Domain Model:** Order, Cart, OrderItem, ShippingAddress
    - **Responsibilities:** Managing Shopping carts, Order Creation, Order Tracking
    - **Microservices:** Order Service, Cart Service

    **Example -> _Payment Management_**
    - **Domain Model:** Payment, Transaction
    - **Responsibilities:** Processing payments, refunds
    - **Microservices:** Payment Service

    **Example -> _Inventory Management_**
    - **Domain Model:** StockItem, Warehouse, Quantity
    - **Responsibilities:** Managing inventory levels, stock updates, warehouse locations
    - **Microservices:** Inventory Service, Warehouse Service
    
    **Example -> _Shipping Management_**
    - **Domain Model:** Shipment, Carrier, TrackingNumber
    - **Responsibilities:** Managing shipments, tracking, calculating shipping rates
    - **Microservices:** Shipping Service

    **Example -> _Customer Management_**
    - **Domain Model:** Ticket, Conversation, Message
    - **Responsibilities:** Handling customer inquiries, managing support tickets, responding to complaints
    - **Microservices:** Customer Support Service
<br>    
<br>
```
👏 Treating each major part of the domain as a separate bounded context in microservices architecture ensures that the system is well-organized, scalable, and maintainable.
    
👏 By defining clear boundaries and responsibilities for each microservice, you can build a robust and flexible e-commerce application that can adapt to changing business requirements and handle complex interactions seamlessly.
```
