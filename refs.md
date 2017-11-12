### [Baldini, Ioana, et al. "Serverless Computing: Current Trends and Open Problems." (2017)](https://arxiv.org/abs/1706.03178)
There has not been a corresponding degree of interest in the research community. We feel strongly that there are a wide variety of technically challenging and intellectually deep problems in this space, ranging from infrastructure issues such as optimizations to the cold start problem to the design of a composable programming model. There are even philosophical questions such as the fundamental nature of state in a distributed application. Many of the open problems identified in this chapter are real problems faced by practitioners of serverless computing today and solutions have the potential for significant impact.

Open research problems:
- What are the **boundaries** of serverless? A fundamental question about serverless computing is of boundaries: is it restricted to FaaS or is broader in scope? How does it relate to other models such as SaaS and MBaaS? 
- Is **tooling** for serverless fundamentally different from existing solutions? As the granularity of serverless is much smaller than traditional server based tools we may need new tools to deal well with more numerous but much shorter living artifacts.
- Can **legacy code** be made to run serverless? The amount of existing code that must continue running is much larger than the new code created specifically to run in serverless environments [...] to what degree existing legacy code can be automatically or semi-automatically decomposed into smaller-granularity pieces to take advantage of these new economics.
- Will there be **patterns** for building serverless solutions? How do we combine low granularity basic building blocks of serverless into bigger solutions? How are we going to decompose apps into functions so that they optimize resource usage? For example how do we identify CPU-bound parts of applications built to run in serverless services? Can we use well-defined patterns for composing functions and external APIs? What should be done on the server vs. client (e.g., are thicker clients more appropriate here)? Are there lessons learned that can be applied from OOP design patterns, Enterprise Integration Patterns, etc.?

### [Fox, Geoffrey C., et al. "Status of Serverless Computing and Function-as-a-Service (FaaS) in Industry and Research." (2017)](https://arxiv.org/abs/1708.08028)

- definition of FaaS and Serverless as a cloud-native platform for **short-running, stateless** computation  and **event-driven** applications which **scales up and down** instantly and automatically and charges for **actual usage** at a millisecond granularity 
- unlike SaaS or PaaS that are always running, but scale on-demand, serverless workloads run on-demand, and consequently, scale on-demand
- great for end developers as they will not need to know scaling and distributed computing
- debugging was identified as a near term critical problem

### [Adzic, Gojko, and Robert Chatley. "Serverless computing: economic and architectural impact." (2017)](http://www.doc.ic.ac.uk/~rbc/papers/fse-serverless-17.pdf)

This paper presents two case industrial studies of early adopters, showing how migrating an application to the Lambda deployment architecture **reduced hosting costs** – by between 66% and 95% – and discusses how further adoption of this trend might **influence common software architecture design practices**.
- Actual Utilisation, not Reserved Capacity
- Distributed request-level authorization: a request to a Lambda function is equally untrusted whether it comes from a client application directly or from another Lambda function. Two sequential requests from the same client might connect to the same Lambda instance, or completely different ones. As the serverless platforms no longer have a gatekeeper server process, using the traditional model where back-end resources implicitly trust servers is not viable. This means that it is perfectly acceptable, even expected, to allow client applications to directly access resources traditionally considered ‘back-end’.
- Different Services Billed According to Different Utilisation Metrics: given the fact that different AWS services are billed according to different utilisation metrics, it is possible to significantly optimise costs by letting client applications directly connect to resources.
- a better summary here https://blog.acolyer.org/2017/10/19/serverless-computing-economic-and-architectural-impact/
- related blog text https://gojko.net/2017/02/23/serverless-migration-lesson.html
  - Critical to **embrace the platform**, not just the Lambda service. Crucially, this means not using Lambda to just host traditional apps cheaper. Sure, it is perfectly possible to run traditional web applications inside Lambda containers with minor modifications, you just need to move state somewhere else. There are even libraries out there that will allow you to run Node.js Express apps or Java Spring Apps inside Lambda easily. On one hand, that is quite a compelling way to start using the new architectures. On the other hand, the benefits of that approach are quite questionable. A big part of Patrick Debois’ keynote at the ServerlessConf 2016 in London was how just pushing things to Lambda won’t make things magically cheaper and faster, quite the opposite.
  - There are three typical aspects of letting the platform take over the responsibilities of a server:
    - Use distributed authorization
    - Let clients orchestrate workflows
    - Allow clients to directly connect to AWS resources


### [Eivy, Adam. "Be Wary of the Economics of" Serverless" Cloud Computing." (2017)](http://ieeexplore.ieee.org/abstract/document/7912239/)

The economic benefits of serverless computing heavily depend on the execution behavior and volumes of the application workload. Serverless has the potential to be a great abstraction offering economic advantages for simple workflows, however it's important to **model the economic impact of your architecture** and operation choices.

### [Villamizar, Mario, et al. "Cost comparison of running web applications in the cloud using monolithic, microservice, and AWS Lambda architectures." (2017)](https://link.springer.com/article/10.1007/s11761-017-0208-y)

A cost comparison of a web application developed and deployed using the same scalable scenarios with three different approaches: 1) a monolithic architecture, 2) a microservice architecture operated by the cloud customer, and 3) a microservice architecture operated by the cloud provider. Test results show that microservices can help reduce infrastructure costs in comparison with standard monolithic architectures. Moreover, the use of services specifically designed to deploy and scale microservices, such as AWS Lambda, **reduces infrastructure costs by 70% or more**, and unlike microservices operated by cloud customers, these specialized services help to guarantee the same performance and response times as the number of users increases.

### [Varghese, Blesson, and Rajkumar Buyya. "Next generation cloud computing: New trends and research directions." (2017)](http://www.sciencedirect.com/science/article/pii/S0167739X17302224)

The use of serverless computing will increase given that billions of devices will need to be connected to the edge of the network and data centers. It will not be feasible to have idle servers in resource constrained environments. The challenges that will hinder the widespread adoption of serverless computing will be the **radical shift in the properties of an application** that a programmer will need to focus on; not latency, scalability and elasticity, but those that relate to the modularity of an application, such as **control and flexibility**. Another challenge is developing programming models that will allow for **high-level abstractions** to facilitate serverless computing. The effect and trade-offs of using traditional external services along with serverless computing services will need to be investigated in orchestrating future cloud-based systems.
