# Google Cloud Pub/Sub

### Sources
> From now on, by `Pub/Sub` I mean the `Google Cloud Pub/Sub` and by `pub/sub messaing` or (or simply `pub/sub `) I mean the publisher/subscriber model.
[What is Google Cloud Pub/Sub?](https://cloud.google.com/pubsub/docs/overview#integrations)
[What is Pub/Sub messaging?](https://blog.stackpath.com/pub-sub/)
[Everything You Need To Know About Publish/Subscribe](https://ably.com/topic/pub-sub)
[Publish–subscribe pattern](https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern)
[The pros and cons of the Pub-Sub architecture pattern](https://www.redhat.com/architect/pub-sub-pros-and-cons)
[Messaging Confusion: Pub/Sub vs Multicast vs Fan-Out](https://stackoverflow.com/questions/8261654/messaging-confusion-pub-sub-vs-multicast-vs-fan-out)
[Message Exchange Patterns (MEPs)](https://garba.org/article/general/soa/mep.html#publishsubscribe)


### Questions
1. What is Pub/Sub?
2. In which ways can Pub/Sub be used for/as? Give at least 3 use cases.
3. Fill in the blanks: pub/sub messaging is a form of `____________` `_______`-to-`_______` communication used to enable `_____`-`______` architectures or to enhance `__________` and `_____________` architectures.
4. How does Pub/Sub work?
5. A pub/sub model allows messages to be broadcasted asynchronously across multiple sections of the applications. Which core component facilitates this functionality? Justify your answer.
6. What is a Topic?
7. What is a Message?
8. What is a Publisher?
9. What is a Subscriber?
10. What are the benefits of pub/sub messaging? Justify your answer.
11. What are the downsides of pub/sub messaging? Justify your answer.
12. Is it correct to say that the pub/sub pattern is, basically, a *Message Queue* handled by a *Mediator* called *Message Broker*? Justify your answer.

### Answers
1. Pub/Sub is a flexible, reliable, real-time messaging service for independent applications to publish and subscribe to asynchronous events.
2. Pub/Sub can be used:<br/>for streaming analytics and data integration pipelines to ingest and distribute data;<br/>as a messaging-oriented middleware (MOM) for service integration;<br/>as a queue to parallelize tasks;
3. pub/sub messaging is a form of asynchronous service-to-service communication used in to enable event-driven architectures or to enhance serverless and microservices architectures.
4. <br/>1. Publishers send events to the Pub/Sub service, without 
5. A Topic.<br/>The publisher will push messages to a Topic and the Topic will immediately push those messages to all of it's subscribers.
6. An intermediary channel that maintains a list of subscribers to relay messages to that are received from publishers.
7. Serialized messages sent to a topic by a publisher which has no knowledge of the subscribers.
8. An application that publishes a message to a topic.
9. An application that registers itself with the desired topic in order to receive the appropriate messages.
10. 1. **Loose coupling**<br/>Publishers are never aware of the existence of subscribers so that both systems can operate independently of each other. This methodology removes service dependencies that are present in traditional coupling. For example, a client generally cannot send a message to a server if the server process is not running. With pub/sub, the client is no longer concerned whether or not processes are running on the server.<br/>2. **Scalability**<br/>Pub/sub messaging can scale to volumes beyond the capability of a single traditional data center thanks to parallel operations, message caching, tree-based routing etc.
11. 1. **Testing can be a challenge**<br/>Because interactions are asynchronous, testing is not a matter of making a request and then analyzing the result. Rather a message must be sent into the system, and then the test needs to observe the behavior of the process(s) under test to see when and how it handles the message.<br/>2. **Message delivery issues**<br/>A publisher in a pub/sub system may assume that a subscriber is listening, when in fact it is not.<br/>3. **Load surges and Slowdowns**<br/>Network elasticity mechanisms must be put in place to handle periods when subscriber requests saturate network throughput followed by periods of low message volume (underutilized network bandwidth).<br/>4. **Security concerns**<br/>Not only the broker stands as a powerful vector for distributed attacks but, also, a subscriber might be able to receive data that it is not authorized to receive.<br/>An authorized publisher may be able to introduce incorrect or harmful messages into the pub/sub system.
12. It is partially correct. The definition failed to mention one very important aspect of pub/sub: *Topics*.<br/>Topics are of the essence for the Publish/Subscriber Message Exchange Pattern (MEP) as they enable the *Fan-out*/*Fan-in* messaging patterns, which are core to Pub/Sub as a pattern.
