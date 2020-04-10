# spring-jms-app

## JMS Specification and MOM

- Set of interfaces and terms implemented by provider
- Message-Oriendted middleware
- JMS providers furnish implementations in APIs
- A few types of MOMs(ActiveMQ, RabbitMQ, JBossMQ etc.)

## Two Messaging Domain Types
- **Point to Point (PTP)**
    - PTP operates around Queues
    - MSG is published to a specific queue by a producer
    - MSG is read and removed by a consumer
    
- **Publish/subscribe (pub/sub)**
    - pub/sub operates around Topics
    - MSG is published to a specific topic on MOM by a producer
    - MSG is read by one or more subscribers

## JMS 1.1 vs Spring JMS API
- Spring JMS API is not a MOM provider
- Spring JMS API is an abstraction layer to JMS 1.1
- Spring JMS API needs a MOM API to communicate to a MOM

## Using JMS 1.1 Specification
    1. Create the JNDI initial context
    2. Obtain a ConnectionFactory from the JNDI context
    3. Obtain a queue from the ConnectionFactory
    4. Create a Session object from the queue
    5. Create a Sender or Receiver object from the Session object
    6. Sender or Receiver object can send or receive a message
    7. Close all the JMS resources used for processing the message 
    
## Using Spring JMS API
    1. Abstracts the first 5 steps and the last step into one
    2. Manages the number of JMS resources needed to send and receive
    
### Spring Framework Template Class APIs
```
- JDBC -> JdbcTemplate
- JNDI -> JndiTemplate
- JMS -> JmsTemplate
    - JMS messaging operations distilled into send and receive message tasks
    - Makes development easier by abstracting all connection, session, and JNDI contexts

These are transactional and excellent at managing resources to open and close connections
```