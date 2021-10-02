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
17. What, exactly, is generated from a `.proto` file (in Java)?
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
9. A stub is, conceptually, a local façade to which a caller issues a RPC and from which a callee receives one. Stubs are responsible for (1) marshalling/unmarshalling egressing/ingressing messages and (2) receiving/sending data from/to the transport layer (or, in other words, abstracting away network implementation details from the communication).<br/>![what-is-a-stub](https://user-images.githubusercontent.com/79336695/135722178-61e3dee9-761c-4f93-bc9e-3ff41622b91d.png)
10. 
