# gRPC
## A high performance, open source universal RPC framework

### Sources
[Introduction to gRPC](https://grpc.io/docs/what-is-grpc/introduction/)<br/>
[A basic introduction to gRPC in Java](https://grpc.io/docs/languages/java/basics/)<br/>
[gRPC - FAQ](https://grpc.io/docs/what-is-grpc/faq/)
[Remote Procedure Call (RPC)](https://searchapparchitecture.techtarget.com/definition/Remote-Procedure-Call-RPC)

### Questions
1. What is gRPC?
2. What is RPC?
3. How does gRPC makes creating distributed applications/services easier?
4. What takes place during a RPC? (hint: 8 steps)
5. What are the five types of RPC?
6. What is protobuf (Protocol Buffers)?
7. What is Serialization?
8. Okay, I get it. Serialization turns 'data' into a 'stream of bytes', but what is "data"? Since computers represent everything as bytes, isn't 'data' also, well, bytes?
9. What is a 'stub' in distributed computing?
10. What is the main difference between the XML and the protobuf formats? (hint: performance)
11. What is the main difference between the JSON and the protobuf formats? (hint: performance)
12. When should JSON be used instead of protobuf?
13. When should protobuf be used instead of JSON?
14. What is protoc and what it does?
15. What is RMI?
16. What is the main difference between RPC and RMI?
17. What, exactly, is generated from a `.proto` file containing a service definition? (in Java)
18. Is gRPC "encoding agnostic"? Justify your answer.
19. Why use gRPC?
20. Why is gRPC better than any binary blob over HTTP/2?
21. Why is gRPC better/worse than REST?
22. Why is it recommended to use proto3 instead of proto2 (the current default protobuf version) with gRPC? (hint: 2 reasons)

### Answers
1. gRPC is a framework for Remote Procedure Call (RPC).
2. Remote Procedure Call (RPC) is a request-response protocol that a program can use to a request a service from a program located in another computer on a network without having to understand the network's details.
3. gRPC makes it easier to create distributed applications/services because it abstracts network/IPC implementation details away from the software integration process (since it allows a client application to call a method on a server application as if it were a local object).
4. <br/>Step 1: The client calls the client stub, passing a procedure and it's parameters in.<br/>Step 2: The client stub marshalls the procedure into a message and makes a system call to send the message.<br/>Step 3: The client's operating system sends the message to the remote machine (server).<br/>Step 4: The server passes the incoming packets to the server stub.<br/>Step 5: The server stub unmarshalls the parameters from the message and starts the execution.</br>Step 6: After execution finishes it returns to the server stub, which marshalls the return values into a message and passes it to the transport layer.<br/>Step 7: The transport layer sends the resulting message back to the client's transport layer, which passes the message back to the client stub.<br/>Step 8: The client stub unmarshalls the return parameters and execution returns to the caller.
5. <br/>1. (Blocking) After making the call, the client's execution is suspended until the server replies.<br/> 2. (Nonblocking) After making the call, the client's execution continues. The server never replies.<br/>3. (Nonblocking) After making the call, the client's execution continues. The server later replies.<br/>4. (Nonblocking) Several nonblocking calls are sent in one batch.<br/>5. (Nonblocking) A broadcast call is made.<br/>
6. Protobuf is a language-neutral, platform-neutral, extensible technology for serializing structured data – think XML, but smaller, faster, and simpler.
7. Serialization is the process of converting a data object into a stream of bytes in order to store or transmit it.
8. Data is not always in a form which can be streamed, a classical example is data containing references to other (local) data.<br/> E.g. if you have an object which contains a reference, that reference as bytes, alone, is of no use. Instead, you must stream the referenced data (by fetching it and bundling it together with the rest of the data, which is another of the marshalling algorithm's responsibilities).
9. A stub is, conceptually, a local façade to which a caller issues a RPC and from which a callee receives one. Stubs are responsible for (1) marshalling/unmarshalling of messages and (2) receiving/sending data from/to the transport layer (or, in other words, abstracting away network implementation details from the communication).
10. XML is a textual format while protobuf is a binary one.
11. JSON is a textual format while protobuf is a binary one.
12. When (1) you want data to be human readable and/or (2) when data from the service is directly consumed by a web browser.
13. When you need (1) type-safety and/or (2) fast serialization/deserialization and/or (3) better overall performance.
14. `protoc` (protocol buffer compiler) is used to compile *.proto* files, generating language-specific code for Protobuf messages and RPC interfaces.
15. RMI (Remote Method Invokation) is an API that allows an object to invoke a method from an object running in another JVM.
16. Suitability.<br/>RPC, as a library, is OS dependent while RMI depends on Java (JVM). Besides that, RPC is procedural while RMI is tightly coupled to Java's object-oriented programming model.
17. After compiling the `.proto` file holding the definition for the service, say, `MyService`: protoc will generate (1) a base class for the server to implement `MyService.MyServiceImplBase` with all the methods defined in the .proto file, and (2) stub classes that a client can use to talk to a `MyService` server.<br/>If a *Message*, say, `MyMessage` is, also, defined in that `.proto` file: protoc will generate a `MyMessage.java` file containing boilerplate code for populating, serializing and retrieving messages of type `MyMessage`.
18. Yes.<br/>gRPC is encoding agnostic because you can use it with JSON (or other format, as long as it's a supported one) and not, necessarily, with Protobuf only.
19. gRPC shines in scenarios where low latency or language agnostic communication are of the essence.
20. A "binary blob over HTTP/2" is, largely, what gRPC is, quintessentially. However, gRPC also provides several high-level features frequently missing in common HTTP libraries (e.g., cascading call-canelation, load balancing and failover).
21. gRPC largely follows HTTP semantics over HTTP/2 but it, explicitly, allows for full-duplex streaming.<br/>Besides that, the fact that in gRPC paths are static (there are no query parameters) eliminates the need to thoroughly parse requests yielding reductions both in latency and complexity.<br/>Last but not least, gRPC's formalized set of errors are more directly applicable to API use cases than the traditional HTTP status codes. 
22. By using proto3 instead of proto2 you (1) gain access to the full range of gRPC-supported languages and (2) avoid compatibility issues proto2 clients talking to proto3 servers and vice-versa.