# Microservices

Microservices are small, autonomous programs that function as both data producers and data consumers

At a fundamental level, microservices expose a limited API, which provides a simple set of related functionalities that, by design, are “loosely coupled” with other collaborating services.

## Fundamental Components
1. Message dispatcher (Producer), which **publishes messages to** a service bus
2. Event listener (Consumer), which **receives messages from** a service bus
3. Business logic, which is the **data passing between producers and consumers**

* In addition, most microservice implementations rely upon some type of message broker – typically a library that provides a message queue and an exchange. 
    * You can think of a message queue as a buffer or an array of n length. 
    * An exchange consists of the logic that receives messages from producers and pushes them into the correct queue(s).

* One of the two most common microservice patterns are work queues, which distribute tasks among different workers. We can represent this pattern as follows:

   ![work queue pattern](https://media.licdn.com/dms/image/C4E12AQFsry68grMDqg/article-inline_image-shrink_1500_2232/0?e=2131315200&v=beta&t=IWXzqNzhYofLQu_QpzwB-F84l61fRgbg9kNNe400mE8)

* The second most common pattern is known as publish/subscribe or PubSub. This pattern allows consumers to subscribe to data or events created by a producer. The pattern is shown below.

    ![pubsub pattern](https://media.licdn.com/dms/image/C4D12AQHYfHh8QlqrBg/article-inline_image-shrink_400_744/0?e=2131315200&v=beta&t=7aYdxcNCexvxrAVbh4XAihryucWBRrTkxbBL3yMt6kA)

  * Unlike message queues, where data is pushed to specific consumers, the PubSub pattern allows the producer to queue data without knowing which, if any, consumers will receive the data. Consumers, depending upon their mission, can subscribe to many producers.

Microservices allow flexibility in terms of infrastructure and deployment; application traffic is routed to collections of services that may be distributed across CPU’s, disks, machines and networks as opposed to a single monolithic platform designed to manage all traffic.

### Remote Procedure Calls (RPC)
* Technique for making a local call and having it execute on a remote collaborator
![RPC flow](https://dzone.com/storage/temp/9773666-0.jpg)
* Typically RPC utilizes a delegate as part of the callback process
* The core idea of RPC is to hide the complexity of the remote call



#### References
https://dzone.com/articles/an-introduction-to-microservices