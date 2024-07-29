# Microservices Design Patterns Part 2

🚀 [Strangler Pattern](#strangler-pattern) <br>
🚀 [Saga Pattern](#saga-pattern) <br>
🚀 [CQRS Pattern](#command-query-responsibility-segregation-cqrs)

## Strangler Pattern
- `Strangler Pattern` is an architectural approach during the migration of a monolithic application to a microservice-based architecture.
- This pattern involves replacing parts of a monolithic application with microservices over time.
- This pattern is particularly suitable for legacy systems with complex codebases that are challenging to refactor entirely.
- In order to implement strangler pattern, we need to follow 3 steps:<br>
    ⏭ _Transform_<br>
    ⏭ _Co-exist_<br>
    ⏭ _Eliminate_<br><br>

    ![Strangler Pattern](./assets/images/strangler-pattern.jpeg)

    ### Advantages of Strangler Pattern<hr>
    😎 **_Incremental Migration:_**<br>
        This pattern mitigates risks associated with complete system rewrites and minimizes disruptions by allowing a gradual migration process.<br>

    😎 **_Flexibility:_**<br>
        Organizations can independently refactor and update specific parts of the system based on business priorities.<br>

    😎 **_CoExistence:_**<br>
        The monolithic application and microservices coexist harmoniously, ensuring the system remains operational during the migration.

    ### Disadvantages of Strangler Pattern<hr>
    🤢 **_Complexity:_**<br>
        This migration process can introduce complexity due to the coexistence and interaction between monolith and microservices application. <br>

    🤢 **_Increased Network Calls:_**<br>
        The introduction of microservices can lead to an increase in network calls, potentially impacting system performance and latency.

## Saga Pattern
- Implementing `database per service` has a drawback to maintain consistent business transactions that span multiple services.
- Therefore `Saga Pattern` is a way to manage the data consistency(maintain ACID properties) across microservices in distributed transaction. 
- A saga is a sequence of local transactions that updates each services and **_publishes a message or event_** to trigger the next transaction step. 
- If a step fail, the saga executes the compensating transactions that reverse the previous transactions.<br><br>

    ![Saga Pattern](./assets/images/Saga-Pattern.png)

- There are two ways of coordination sagas:<br>

    ✈ **_Choreography:_** <br>
        Each local transaction publishes domain events that trigger local transactions in other services.<br>

    ✈ **_Orchestration:_** <br> 
        An orchestrator (object) tells the participants services what local transactions to execute.

    ### Advantages of Saga Pattern<hr> 
    😎 **_Maintain Data Consistency:_** <br>
        It enables the application to maintain data consistency across multiple services without using distributed transactions.

    ### Disadvantages of Saga Pattern<hr>
    🤢 **_Lack of automatic transaction rollback:_** <br>
        A developer must design compensating transactions that explicitly undo changes (in case of failure) made earlier rather than relying on automating rollback feature of ACID transactions. 
    
    🤢 **_Lack of Isolation:_** <br>
        The lack of isolation means that there’s risk that the concurrent execution of multiple sagas and transactions can use data anomalies.

## Command Query Responsibility Segregation (CQRS)
- **Context:** <br> 
    When implement _Microservices architecture pattern_ and the _Database per service_ pattern. As a result, it is no longer straightforward to implement queries that join data from multiple services.
- **Problem:** <br>
    How to implement a query that retrieves data from multiple services in a microservice architecture?
- **Solution:** <br>
    Define a view database, which is a read-only replica that is designed to support that query. The application keeps the replica up-to-date by subscribing to Domain events published by the services that own data. <br><br>

    ![CQRS Pattern](./assets/images/CQRS.png)

    ### How to Sync database with CQRS design pattern? <hr>
    Synchronizing databases in a system that follows the CQRS (Command Query Responsibility Segregation) pattern can be challenging due to the separation of the write and read sides of the application.
    But we can ensures it using the following:

    #### Event Sourcing
    - Event Sourcing involves capturing all changes of application state as a sequence of events. These events are stored in an event store and can be replayed to rebuild the state of the application at any point in time.

    - In a CQRS architecture, the write model generates events when commands are processed, and the read model subscribes to these events to update its state.

    - **_Benefits:_** <br>
        - Event sourcing provides a complete audit trail of all changes to the application’s state, which can be useful for debugging and compliance purposes. 

        - It also enables scalability and fault tolerance, as events can be replayed to rebuild the state in case of failure.

    - **_Challenges:_** <br>
        - Event sourcing introduces complexity, as developers need to design the events and event handlers carefully to ensure consistency and correctness. 

        - It also requires additional infrastructure for storing and replaying events.
    
    #### Messaging Systems
    - Messaging Systems such as Kafka, or RabbitMQ can be used to decouple the synchronization process between the write and read sides of application. 

    - The write model publishes events to a message queue, and the read model consumes these events to update its state.

    - **_Benefits:_** <br>
        - Messaging Systems provide a flexible and scalable way to synchronize databases, as they can handle large volumne of events and distribute them across multiple consumers.

        - They also enable asynchronous communication, which can improve overall system performance. 

    - **_Challenges:_** <br>
        - Implementing messaging systems can introduce complexity, as developers need to ensure that messages are processed in the correct order and that data consistency is maintained. 

        - It also requires additional infrastructure for managing and monitoring the message queues.