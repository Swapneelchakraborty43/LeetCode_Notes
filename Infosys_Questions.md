**1. Explain Architecture, Event driven architecture?**

-Services donot call each other directly, instead services emit events and other services react to 
those events. (Listner and Queues)

-Event : fact that has happened, not something that needs to be done.

-![img_2.png](img_2.png)

![img_3.png](img_3.png)

- Problems of Synchronous communication.
- 
![img_4.png](img_4.png)

Event Driven Architecture:
![img_5.png](img_5.png)

Advantages of EDA:

![img_6.png](img_6.png)

Main components of EDA:

![img_7.png](img_7.png)

How do events move in EDA?
- Push model: Broker pushes messages. Consumer handles the rate.
- Pull Model: 

-EDA Models:
![img_8.png](img_8.png)

Streaming example: Kafka.

Challenges of EDA:

![img_9.png](img_9.png)






