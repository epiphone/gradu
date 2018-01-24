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

### [van Eyk, Erwin, et al. "The SPEC Cloud Group’s Research Vision on FaaS and Serverless Architectures." (2017)](https://atlarge-research.com/pdfs/spec-vision-serverless-faas17wosc_accepted.pdf)

However useful, serverless and FaaS suffer from a community problem that faces every emerging technology, which has indeed also hampered cloud computing a decade ago: lack of clear terminology, and scattered vision about the field. In this work, we address this community problem. We **clarify the term serverless**, by reducing it to cloud functions as programming units, and a model of executing simple and complex (e.g., workflows of) functions with operations managed primarily by the cloud provider. We propose a research vision, where 4 key directions (perspectives) present 17 technical opportunities and challenges.

### [Buyya, Rajkumar, et al. "A Manifesto for Future Generation Cloud Computing: Research Directions for the Next Decade." (2017)](https://arxiv.org/abs/1711.09123)

[...] with serverless computing and FaaS there is the **need for developing novel patterns** to define services that combine traditional external services along with the serverless computing services. Here the effect and trade-offs of orchestration of such service mixes need to be investigated systematically. The influence of the underpinning choice of Cloud resources (e.g., on-demand, reserved, spot, burstable) need also to be examined.

### [Baldini, Ioana, et al. "The serverless trilemma: function composition for serverless computing." (2017)](https://dl.acm.org/citation.cfm?id=3133855)

While an attractive economic proposition, serverless computing currently lags behind the state of the art when it comes to function composition. This paper addresses the challenge of programming a **composition of functions**, where the composition is itself a serverless function. We demonstrate that engineering function composition into a serverless application is possible, but requires a careful evaluation of trade-offs. To help in evaluating these trade-offs, we identify three competing constraints: functions should be considered as black boxes; function composition should obey a substitution principle with respect to synchronous invocation; and invocations should not be double-billed.

### [Sbarski, P., and S. Kroonenburg. "Serverless Architectures on AWS With examples using AWS Lambda." (2016)](https://www.manning.com/books/serverless-architectures-on-aws)
A more technical book on various AWS-specific patterns

### [Lynn, Theo, et al. "A Preliminary Review of Enterprise Serverless Cloud Computing (Function-as-a-Service) Platforms." (2017)](https://www.researchgate.net/profile/Pierangelo_Rosati/publication/321753133_A_Preliminary_Review_of_Enterprise_Serverless_Cloud_Computing_Function-as-a-Service_Platforms/links/5a2feb7d458515a13d851ec0/A-Preliminary-Review-of-Enterprise-Serverless-Cloud-Computing-Function-as-a-Service-Platforms.pdf)
This paper provides an overview and multi-level feature **analysis of seven enterprise serverless computing platforms**. It reviews extant research on these platforms and identifies the emergence of AWS Lambda as a de facto base platform for research on enterprise serverless cloud computing.
- Reference [6,p.1] defines serverless computing as “a software architecture where an application is decomposed into ‘triggers’ (events) and ‘actions’ (functions), and there is a platform that provides a seamless hosting and execution environment.”

### [Lloyd, Wes, et al. "Serverless Computing: An Investigation of Factors Influencing Microservice Performance." (2017)](https://pdfs.semanticscholar.org/8ee9/de812815ec238ac210af34fb0b154f773bf8.pdf)
We identify four states of serverless infrastructure including: **provider cold, VM cold, container cold, and warm** and demonstrate how microservice performance varies up to 15x based on these states.

## Other materials

- blog posts etc.
  - https://martinfowler.com/articles/serverless.html
- technical conferences:
  - GOTO 2017 https://gotocph.com/
    - *Serverless: the future of architecture*
      - lambda is to computing what S3 is to storage
      - cannot under- or overprovision
      - embrace 3rd party services; compute as glue
      - write stateless single-purpose funcs; 1 or 0 data transformations (?)
      - design push-based event-driven pipelines
      - create thicker more powerful front-ends (leveraging JWT for auth to remove middle man); UI might talk directly with your db, protected actions as lambdas (?)
      - serverless monolith vs micro: each service has its own db and API
      - from monolith to micro without thinking about infra
    - *Designing for the serverless age*
      - technical vs financial view
      - many things we take for granted are now solutions to constraints that no longer apply
      - 66% savings moving from Heroku; bigger savings possible when moving from less cost-effective platforms
      - pay not for reserved capability but for milliseconds, actual usage
      - get a bunch of stuff automatically: monitoring logging security etc. NoOps
      - optimize for quick start over quick failover; lazy load everything
      - cbeaper to run expensive experiments
      - play arbitrage with different pricing models
      - no need for gatekeepers (server between user and db for example), use request-level auth. Three tier adds latency and costs
      - push to client, keep state in users' browsers
  - EMIT 2017 http://www.emitconference.com/
  - Serverlessconf (https://serverless.com/blog/serverless-conf-2017-nyc-recap/)
