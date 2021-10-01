# Kubernetes (WIP)

### Sources
> From now on, by `Node` I mean a `Kubernetes Worker Node`.<br/>And, by `node` I mean [the traditional definition of a distributed system's node](https://www.techopedia.com/definition/5307/node#techopedia-explains-node)
[Kubernetes Components](https://kubernetes.io/docs/concepts/overview/components/)<br/>
[Top 50 Kubernetes Interview Questions And Answers for 2021](https://www.edureka.co/blog/interview-questions/kubernetes-interview-questions/)<br/>
[What is a Kubernetes pod](https://www.redhat.com/en/topics/containers/what-is-kubernetes-pod)<br/>
[Top 55 Kubernetes Interview Questions and Answers for 2021](https://www.guru99.com/kubernetes-interview-questions-answers.html)<br/>

1. What is a cluster computing and how is it different from grid computing?
1. What is Kubernetes?
1. How are microservices related to Kubernetes?
1. How is Kubernetes different from Docker Swarm?
1. How is Kubernetes related to Docker?
1. What is load balancing (in computing)? How is it applied in networking?
1. What is a pod? Why does Kubernetes use them?
1. How do pods communicat
1. What is a Node? What are them made of? (hint: 3 components)
1. What is a 
1. What is a 'master node' in Kubernetes?
1. Which addon is strictly required for all Kubernetes cluster to have and what it does?
101. 



### Answers
1. Both of them can be defined as "a set of computers that work together so that they can be viewed as a single system".<br/>However, nodes in a cluster perform the same task while, in a grid, each node runs a different task/application.
1. Kubernetes is an open-source container management tool that holds the responsibilities of container deployment, scaling/descaling of containers and load balancing.
1. Microservices designs require you to change how you build and deploy applications. Combined with the Docker container system, Kubernetes makes deploying and monitoring microservices on a cloud system like AWS much safer and more stable than using home-brewed processes.
1. <br/>In Kubernetes a container can share storage volumes only with containers in the same pod while, in Docker Swarm, containers can share storage volumes with any other container.<br/>Kubernetes natively supports auto-scaling while Docker Swarm doesn't.<br/>Docker Swarm does auto load-balancing between containers in the cluster natively while Kubernetes requires you to manually intervene (or setup some traffic management or *Service Mesh*, e.g. Istio, alongside your clusters).<br/>Kubernetes supports automatic rollbacks for updates while Docker Swarm doesn't.<br/>Kubernetes has a native GUI, the Kubernetes Dashboard while Docker Swarm GUI options are third-party (e.g., Portainer, Swarmpit).<br/>Again, Kubernetes offers built-in logging and monitoring tools while Docker Swarm requires you to use third-party tools (e.g., ELK, Graylog, Splunk).<br/>Kubernetes' setup is much more complicated than Docker Swarm's setup.
1. Docker builds the containers and these containers communicate with each other across the network via Kubernetes. Containers running on multiple hosts can be manually linked and orchestrated using Kubernetes.
1. In *computing*, load balancing refers to the process of distributing a set of tasks over a set of resources (computing units), with the aim of making their overall processing more efficient.<br/>In *networking*, Load balancing is the process of distributing network traffic across multiple servers so that no single server bears too much demand.
1. A Kubernetes pod is both (1) a collection of one or more Linux containers and (2) an abstraction/wrapper around containers. Pods are the smallest units of a Kubernetes application.<br/>
1. A Kubernetes Node is a worker machine and may be either a virtual or a physical machine, depending on the cluster.
1. TODO
1. TODO
1. Cluster DNS.<br/>This addon serves DNS records for the Kubernetes services.

---


### Scratch
What is Infrastructure as Code?<br/>
What is the entrypoint to a K8s cluster?<br/>
What is a master node made of? (hint: 4 components)<br/>
Why doesn't the master node represent a SPoF?<br/>
In which scenarios should we opt for a Deployment instead of a StatefulSet?<br/>
What is a Kubernetes Deployment?<br/>
Which component holds the current status of any K8s component in the cluster? (hint: Cluster brain)<br/>
Why are Databases not commonly hosted inside the Kubernetes cluster?<br/>

