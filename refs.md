## General serverless & cloud trends

[Albuquerque Jr, Lucas F., et al. "Function-as-a-Service X Platform-as-a-Service: Towards a Comparative Study on FaaS and PaaS." ICSEA 2017 (2017): 217.](https://thinkmind.org/index.php?view=article&articleid=icsea_2017_9_30_10096)
The present work has proposed to perform a **comparative evaluation between FaaS and PaaS** service delivery models regarding performance, scalability and costs issues in support of mobile applications based on microservices. The conclusions obtained showed that FaaS presented an equivalent performance, a more efficient scalability and the costs influenced by workload type.

[CNCF Serverless WG whitepaper (2017)](https://github.com/cncf/wg-serverless)
This paper describes a new model of cloud native computing enabled by emerging "serverless" architectures and their supporting platforms. It defines what serverless computing is, highlights use cases and successful examples of serverless computing, and shows **how serverless computing differs from (and interrelates with) other cloud application development models** such as IaaS, PaaS and container orchestration or Containers-as-a-Service (CaaS).

[Baldini, Ioana, et al. "Serverless Computing: Current Trends and Open Problems." (2017)](https://arxiv.org/abs/1706.03178)
There has not been a corresponding degree of interest in the research community. We feel strongly that there are a wide variety of technically challenging and intellectually deep problems in this space, ranging from infrastructure issues such as optimizations to the cold start problem to the design of a composable programming model. There are even philosophical questions such as the fundamental nature of state in a distributed application. Many of the open problems identified in this chapter are real problems faced by practitioners of serverless computing today and solutions have the potential for significant impact.

Open research problems:
- What are the **boundaries** of serverless? A fundamental question about serverless computing is of boundaries: is it restricted to FaaS or is broader in scope? How does it relate to other models such as SaaS and MBaaS?
- Is **tooling** for serverless fundamentally different from existing solutions? As the granularity of serverless is much smaller than traditional server based tools we may need new tools to deal well with more numerous but much shorter living artifacts.
- Can **legacy code** be made to run serverless? The amount of existing code that must continue running is much larger than the new code created specifically to run in serverless environments [...] to what degree existing legacy code can be automatically or semi-automatically decomposed into smaller-granularity pieces to take advantage of these new economics.
- Will there be **patterns** for building serverless solutions? How do we combine low granularity basic building blocks of serverless into bigger solutions? How are we going to decompose apps into functions so that they optimize resource usage? For example how do we identify CPU-bound parts of applications built to run in serverless services? Can we use well-defined patterns for composing functions and external APIs? What should be done on the server vs. client (e.g., are thicker clients more appropriate here)? Are there lessons learned that can be applied from OOP design patterns, Enterprise Integration Patterns, etc.?

[Fox, Geoffrey C., et al. "Status of Serverless Computing and Function-as-a-Service (FaaS) in Industry and Research." (2017)](https://arxiv.org/abs/1708.08028)
- definition of FaaS and Serverless as a cloud-native platform for **short-running, stateless** computation and **event-driven** applications which **scales up and down** instantly and automatically and charges for **actual usage** at a millisecond granularity
- unlike SaaS or PaaS that are always running, but scale on-demand, serverless workloads run on-demand, and consequently, scale on-demand
- great for end developers as they will not need to know scaling and distributed computing
- debugging was identified as a near term critical problem

[Adzic, Gojko, and Robert Chatley. "Serverless computing: economic and architectural impact." (2017)](http://www.doc.ic.ac.uk/~rbc/papers/fse-serverless-17.pdf)
This paper presents two case industrial studies of early adopters, showing how migrating an application to the Lambda deployment architecture **reduced hosting costs** – by between 66% and 95% – and discusses how further adoption of this trend might **influence common software architecture design practices**.
- Actual Utilisation, not Reserved Capacity
- Distributed request-level authorization: a request to a Lambda function is equally untrusted whether it comes from a client application directly or from another Lambda function. Two sequential requests from the same client might connect to the same Lambda instance, or completely different ones. As the serverless platforms no longer have a gatekeeper server process, using the traditional model where back-end resources implicitly trust servers is not viable. This means that it is perfectly acceptable, even expected, to allow client applications to directly access resources traditionally considered ‘back-end’.
- Different Services Billed According to Different Utilisation Metrics: given the fact that different AWS services are billed according to different utilisation metrics, it is possible to significantly optimise costs by letting client applications directly connect to resources.
- a better summary here https://blog.acolyer.org/2017/10/19/serverless-computing-economic-and-architectural-impact/
- related blog text https://gojko.net/2017/02/23/serverless-migration-lesson.html
  - Critical to **embrace the platform**, not just the Lambda service. Crucially, this means not using Lambda to just host traditional apps cheaper. Sure, it is perfectly possible to run traditional web applications inside Lambda containers with minor modifications, you just need to move state somewhere else. There are even libraries out there that will allow you to run Node.js Express apps or Java Spring Apps inside Lambda easily. On one hand, that is quite a compelling way to start using the new architectures. On the other hand, the benefits of that approach are quite questionable. A big part of Patrick Debois’ keynote at the ServerlessConf 2016 in London was how just pushing things to Lambda won’t make things magically cheaper and faster, quite the opposite.
  - There are three typical aspects of letting the platform take over the responsibilities of a server: Use distributed authorization, Let clients orchestrate workflows, Allow clients to directly connect to AWS resources


[Varghese, Blesson, and Rajkumar Buyya. "Next generation cloud computing: New trends and research directions." (2018)](https://www.sciencedirect.com/science/article/pii/S0167739X17302224)
The use of serverless computing will increase given that billions of devices will need to be connected to the edge of the network and data centers. It will not be feasible to have idle servers in resource constrained environments. The challenges that will hinder the widespread adoption of serverless computing will be the **radical shift in the properties of an application** that a programmer will need to focus on; not latency, scalability and elasticity, but those that relate to the modularity of an application, such as **control and flexibility**. Another challenge is developing programming models that will allow for **high-level abstractions** to facilitate serverless computing. The effect and trade-offs of using traditional external services along with serverless computing services will need to be investigated in orchestrating future cloud-based systems.

[van Eyk, Erwin, et al. "The SPEC Cloud Group’s Research Vision on FaaS and Serverless Architectures." (2017)](https://atlarge-research.com/pdfs/spec-vision-serverless-faas17wosc_accepted.pdf)
However useful, serverless and FaaS suffer from a community problem that faces every emerging technology, which has indeed also hampered cloud computing a decade ago: lack of clear terminology, and scattered vision about the field. In this work, we address this community problem. We **clarify the term serverless**, by reducing it to cloud functions as programming units, and a model of executing simple and complex (e.g., workflows of) functions with operations managed primarily by the cloud provider. We propose a research vision, where 4 key directions (perspectives) present 17 technical opportunities and challenges.

[Buyya, Rajkumar, et al. "A Manifesto for Future Generation Cloud Computing: Research Directions for the Next Decade." (2017)](https://arxiv.org/abs/1711.09123)
[...] with serverless computing and FaaS there is the **need for developing novel patterns** to define services that combine traditional external services along with the serverless computing services. Here the effect and trade-offs of orchestration of such service mixes need to be investigated systematically. The influence of the underpinning choice of Cloud resources (e.g., on-demand, reserved, spot, burstable) need also to be examined.

[Baldini, Ioana, et al. "The serverless trilemma: function composition for serverless computing." (2017)](https://dl.acm.org/citation.cfm?id=3133855)
While an attractive economic proposition, serverless computing currently lags behind the state of the art when it comes to function composition. This paper addresses the challenge of programming a **composition of functions**, where the composition is itself a serverless function. We demonstrate that engineering function composition into a serverless application is possible, but requires a careful evaluation of trade-offs. To help in evaluating these trade-offs, we identify three competing constraints: functions should be considered as black boxes; function composition should obey a substitution principle with respect to synchronous invocation; and invocations should not be double-billed.

[Sbarski, P., and S. Kroonenburg. "Serverless Architectures on AWS With examples using AWS Lambda." (2016)](https://www.manning.com/books/serverless-architectures-on-aws)
A more technical book on various AWS-specific patterns

[Lynn, Theo, et al. "A Preliminary Review of Enterprise Serverless Cloud Computing (Function-as-a-Service) Platforms." (2017)](https://www.researchgate.net/profile/Pierangelo_Rosati/publication/321753133_A_Preliminary_Review_of_Enterprise_Serverless_Cloud_Computing_Function-as-a-Service_Platforms/links/5a2feb7d458515a13d851ec0/A-Preliminary-Review-of-Enterprise-Serverless-Cloud-Computing-Function-as-a-Service-Platforms.pdf)
This paper provides an overview and multi-level feature **analysis of seven enterprise serverless computing platforms**. It reviews extant research on these platforms and identifies the emergence of AWS Lambda as a de facto base platform for research on enterprise serverless cloud computing.
- Reference [6,p.1] defines serverless computing as “a software architecture where an application is decomposed into ‘triggers’ (events) and ‘actions’ (functions), and there is a platform that provides a seamless hosting and execution environment.”

[Lloyd, Wes, et al. "Serverless Computing: An Investigation of Factors Influencing Microservice Performance." (2017)](https://pdfs.semanticscholar.org/8ee9/de812815ec238ac210af34fb0b154f773bf8.pdf)
We identify four states of serverless infrastructure including: **provider cold, VM cold, container cold, and warm** and demonstrate how microservice performance varies up to 15x based on these states.

[Pozdniakova, Olesia, and Dalius Mazeika. "Systematic Literature Review of the Cloud-ready Software Architecture." (2017)](http://search.proquest.com/openview/b416fd036171a1519fb099eff914c9ad/1?pq-origsite=gscholar&cbl=2040245)
This systematic literature review aims to summarize information available in studies related to **cloud-ready applications architecture** development by answering to the following research questions:
- Question 1. What is a cloud-ready application and how it differs from conventional applications?
- Question 2. What non-functional requirements are raised for cloud-ready applications?
- Question 3. What architectures are currently used for cloud-ready application?

[Hohpe, Gregor, and Bobby Woolf. "Enterprise integration patterns: Designing, building, and deploying messaging solutions." (2004)](http://www.enterpriseintegrationpatterns.com/index.html)
A collection of integration & messaging patterns.

## FaaS runtime

[Hendrickson, Scott, et al. "Serverless computation with openlambda." (2016)](https://dl.acm.org/citation.cfm?id=3027047)
We present **OpenLambda**, a new, open-source platform for building next-generation web services and applications in the burgeoning model of serverless computation. We describe the key aspects of serverless computation, and present numerous **research challenges that must be addressed in the design and implementation** of such systems.

[McGrath, Garrett, and Paul R. Brenner. "Serverless computing: Design, implementation, and performance." (2017)](http://ieeexplore.ieee.org/abstract/document/7979855/)
We present the design of a novel performance-oriented serverless computing platform implemented in. NET, deployed in Microsoft Azure, and utilizing Windows containers as function execution environments. Implementation challenges such as function scaling and container discovery, lifecycle, and reuse are discussed in detail. We propose metrics to evaluate the execution performance of serverless platforms and conduct tests on our prototype as well as AWS Lambda, Azure Functions, Google Cloud Functions, and IBM's deployment of Apache OpenWhisk.

[Oakes, Edward, et al. "Pipsqueak: Lean Lambdas with Large Libraries." (2017)](http://ieeexplore.ieee.org/abstract/document/7979853/)
Lean microservices that depend on **large libraries will start slowly and harm elasticity**. In this paper, we explore the challenges of lean microservices that rely on large libraries in the context of Python packages and the OpenLambda serverless computing platform.

[Spillner, Josef. "Snafu: Function-as-a-service (FaaS) runtime design and implementation." (2017)](https://arxiv.org/abs/1703.07562)
Snafu, or Snake Functions, is a modular system to host, execute and manage language-level functions offered as stateless (micro-)services to diverse external triggers. The system interfaces resemble those of commercial FaaS providers but its implementation provides distinct features which make it overall useful to research on FaaS and prototyping of FaaS-based applications. This paper argues about the system motivation in the presence of already existing alternatives, its design and architecture, the open source implementation and collected metrics which characterise the system.

## Economic aspects

[Eivy, Adam. "Be Wary of the Economics of" Serverless" Cloud Computing." (2017)](http://ieeexplore.ieee.org/abstract/document/7912239/)
The economic benefits of serverless computing heavily depend on the execution behavior and volumes of the application workload. Serverless has the potential to be a great abstraction offering economic advantages for simple workflows, however it's important to **model the economic impact of your architecture** and operation choices.

[Villamizar, Mario, et al. "Cost comparison of running web applications in the cloud using monolithic, microservice, and AWS Lambda architectures." (2017)](https://link.springer.com/article/10.1007/s11761-017-0208-y)
A cost comparison of a web application developed and deployed using the same scalable scenarios with three different approaches: 1) a monolithic architecture, 2) a microservice architecture operated by the cloud customer, and 3) a microservice architecture operated by the cloud provider. Test results show that microservices can help reduce infrastructure costs in comparison with standard monolithic architectures. Moreover, the use of services specifically designed to deploy and scale microservices, such as AWS Lambda, **reduces infrastructure costs by 70% or more**, and unlike microservices operated by cloud customers, these specialized services help to guarantee the same performance and response times as the number of users increases.

[Leitner, Philipp, Jürgen Cito, and Emanuel Stöckli. "Modelling and managing deployment costs of microservice-based cloud applications." (2016)](http://ieeexplore.ieee.org/document/7881628/)
An approach to **model the deployment costs**, including compute and IO costs, of Microservice-based applications deployed to a public cloud. Our model, which we dubbed CostHat, supports both, Microservices deployed on traditional IaaS or PaaS clouds, and services that make use of novel cloud programming paradigms, such as AWS Lambda. Further, we have used this model to implement tooling that warns cloud developers directly in the Integrated Development Environment (IDE) about certain classes of potentially costly code changes. This enables its use in real-time for developer tooling which continually re-evaluates the costs of an application in the background, while the developer is working on the code.

[Kuhlenkamp, Jörn, and Markus Klems. "Costradamus: A Cost-Tracing System for Cloud-Based Software Services." (2017)](https://link.springer.com/chapter/10.1007/978-3-319-69035-3_48)
Cloud providers offer a range of fully managed infrastructure services that enable a “serverless” architecture and development paradigm. Following this paradigm, software services can be built on compositions of cloud infrastructure services that offer fine-granular pay-per-use pricing models. It remains an open challenge to make use of fine-granular pricing models for improving cost transparency and reducing cost of service operations. As a solution, we present Costradamus, a cost-tracing system that implements a generic cost model and three different tracing approaches. With Costradamus, we can derive cost and performance information per API operation.

[Spillner, Josef. "Exploiting the Cloud Control Plane for Fun and Profit." (2017)](https://arxiv.org/abs/1701.05945)
Cloud providers typically charge for their services. There are diverse pricing models which often follow a pay-per-use paradigm. The paper shows how to **exploit the control plane of AWS Lambda** to implement stateful services practically for free and under some circumstances even guaranteed for free which if widely deployed would cause a monetary loss for the provider. It also elaborates on the consistency model for AWS Lambda.


## FaaSification

[Spillner, Josef. "Transformation of Python Applications into Function-as-a-Service Deployments." (2017)](https://arxiv.org/abs/1705.08169)
New cloud programming and deployment models pose challenges to software application engineers who are looking, often in vain, for tools to automate any necessary code adaptation and transformation. Function-as-a-Service interfaces are particular non-trivial targets when considering that most cloud applications are implemented in non-functional languages. Among the most widely used of these languages is Python. This starting position calls for an **automated approach to transform monolithic Python code into modular FaaS units** by partially automated decomposition.


## Scientific workflows

[Malawski, Maciej, et al. "Serverless execution of scientific workflows: Experiments with HyperFlow, AWS Lambda and Google Cloud Functions." (2017)](https://www.sciencedirect.com/science/article/pii/S0167739X1730047X)
Scientific workflows consisting of a high number of interdependent tasks represent an important class of complex scientific applications. In this paper we take a look at serverless infrastructures, which are designed mainly for processing background tasks of Web and Internet of Things applications, or event-driven stream processing. We evaluate their applicability to more compute- and data-intensive scientific workflows and discuss possible ways to repurpose serverless architectures for execution of scientific workflows.Our findings indicate that **the simple mode of operation makes this approach easy to use**, although there are costs involved in preparing portable application binaries for execution in a remote environment. In this paper we considered directions in enhancing security, expressing applications, managing efficiently and developing sustainable systems for next generation cloudcomputing.

[Jonas, Eric, et al. "Occupy the cloud: distributed computing for the 99%."(2017)](https://arxiv.org/abs/1702.04024)
The authors argue that a serverless execution model with stateless functions can enable **radically simpler, fundamentally elastic, and more user-friendly distributed data processing** systems.

[Spillner, Josef, Cristian Mateos, and David A. Monge. "FaaSter, Better, Cheaper: The Prospect of Serverless Scientific Computing and HPC." (2018)](https://link.springer.com/chapter/10.1007/978-3-319-73353-1_11)
Scalable web applications, low-latency mobile backends and on-demand provisioned databases are typical cases for which cloud services on the platform or infrastructure level exist and are convincing when considering technical and economical arguments. Applications with specific processing demands, including high-performance computing, high-throughput computing and certain flavours of scientific computing, have historically required special configurations such as compute- or memory-optimised virtual machine instances. With the rise of function-level compute instances through Function-as-a-Service (FaaS) models, the fitness of generic configurations needs to be re-evaluated for these applications. We analyse several **demanding computing tasks with regards to how FaaS models compare** against conventional monolithic algorithm execution. Beside the comparison, we contribute a refined FaaSification process for legacy software and provide a roadmap for future work.

## Edge computing

[Glikson, Alex, Stefan Nastic, and Schahram Dustdar. "Deviceless edge computing: extending serverless computing to the edge of the network." (2017)](https://dl.acm.org/citation.cfm?id=3078497)
In this paper, we propose a novel computing paradigm - **Deviceless Edge Computing** that extends the serverless paradigm to the edge of the network, enabling IoT and Edge devices to be seamlessly integrated as application execution infrastructure. We also discuss open challenges to realize Deviceless Edge Computing, based on our experience in prototyping a deviceless platform.

[Baresi, Luciano, Danilo Filgueira Mendonça, and Martin Garriga. "Empowering Low-Latency Applications Through a Serverless Edge Computing Architecture." (2017)](https://link.springer.com/chapter/10.1007/978-3-319-67262-5_15)
The exponential increase of the data generated by pervasive and mobile devices requires disrupting approaches for the realization of emerging mobile and IoT applications. Although cloud computing provides virtually unlimited computational resources, low-latency applications cannot afford the high latencies introduced by sending and retrieving data from/to the cloud. In this scenario, edge computing appears as a promising solution by bringing computation and data near to users and devices. However, the resource-finite nature of edge servers constrains the possibility of deploying full applications on them. To cope with these problems, we propose a **serverless architecture at the edge**, bringing a highly scalable, intelligent and cost-effective use of edge infrastructure’s resources with minimal configuration and operation efforts.

[Nastic, Stefan, et al. "A Serverless Real-Time Data Analytics Platform for Edge Computing." IEEE Internet Computing 21.4 (2017): 64-71.](http://ieeexplore.ieee.org/document/7994559/)
Here, a novel approach implements cloud-supported, real-time data analytics in edge-computing applications. The authors introduce their **serverless edge-data analytics platform** and application model and discuss their main design requirements and challenges, based on real-life healthcare use case scenarios.

## Use cases

[Ast, Markus, and Martin Gaedke. "Self-contained web components through serverless computing." (2017)](https://dl.acm.org/citation.cfm?id=3154849)
Web Components are an essential building block for modularizing large and complex web applications into smaller pieces. Many Web Components are not self-contained because they require to integrate their business logic into your backend or to use externally hosted third-party services. In this paper, we describe an approach of how to utilize Serverless Computing to enable self-contained web components by deploying Web Component business logic as cloud-hosted functions.

[Fouladi, Sadjad, et al. "Encoding, Fast and Slow: Low-Latency Video Processing Using Thousands of Tiny Threads." NSDI. 2017.](https://www.usenix.org/conference/nsdi17/technical-sessions/presentation/fouladi)
ExCamera is a cloud-based video-processing framework that we envision as the backend for interactive video applications. It can edit, transform, and encode a video, including 4K and VR material, with low latency. The system makes two major contributions: a framework to run general-purpose parallel computations on a commercial “cloud function” service with low latency, and a video encoder built with this framework that achieves fine-grained parallelism without harming compression efficiency.

[Ishakian, Vatche, Vinod Muthusamy, and Aleksander Slominski. "Serving deep learning models in a serverless platform." (2017)](https://arxiv.org/abs/1710.08460)
In this work we evaluate the suitability of a serverless computing environment for the inferencing of large neural network models. Our experimental results show that while the inferencing latency can be within an acceptable range, longer delays due to cold starts can skew the latency distribution and hence risk violating more stringent SLAs.

[Yan, Mengting, et al. "Building a chatbot with serverless computing." (2016)](https://dl.acm.org/citation.cfm?id=3007217)
In this work, we present the architecture and prototype of a **chatbot using a serverless platform**, where developers compose stateless functions together to perform useful actions. We describe our serverless architecture based on function sequences, and how we used these functions to coordinate the cognitive microservices in the Watson Developer Cloud to allow the chatbot to interact with external services.


## Cloud migration

[Jamshidi, Pooyan, Aakash Ahmad, and Claus Pahl. "Cloud migration research: a systematic review." (2013)](http://ieeexplore.ieee.org/abstract/document/6624108/)
This paper aims to identify, taxonomically classify, and systematically compare existing research on cloud migration.The findings clearly highlight that cost saving, scalability, and efficient utilization of resources as well as flexibility are key drivers to migrate application to the cloud.

[Balalaie, Armin, Abbas Heydarnoori, and Pooyan Jamshidi. "Migrating to cloud-native architectures using microservices: an experience report." (2016)](https://link.springer.com/chapter/10.1007/978-3-319-33313-7_15)
The existing approaches on cloud migration does not mostly consider cloud-native architectures as their first-class citizens. As a result, the final product may not meet its primary drivers for migration. In this paper, we intend to report our experience and lessons learned in an ongoing project on **migrating a monolithic on-premise software architecture to microservices**.


## Others

[Horner, Nathaniel, and Ines Azevedo. "Power usage effectiveness in data centers: overloaded and underachieving." (2016)](https://www.sciencedirect.com/science/article/pii/S1040619016300446)
A series of bottom-up estimates has generally found that data centers use on the order of **1–2% of U.S. and global electricity consumption**. Server utilization in data centers is generally very low. In addition to the designed overhead, there is also an issue of “comatose” servers—those that are no longer needed but are still running because no one can positively determine that the data is old or wants to risk pulling the plug: “[a]necdotal evidence indicates that 10–30% of servers in many data centers are using electricity but no longer delivering computing services. These servers have not yet been decommissioned and are probably not counted in installed base statistics. In many facilities nobody even knows these servers exist....” (Koomey, 2011, 7). Figures for comatose servers may be even higher. A sample at a LexisNexis data center revealed that three-fourths of installed servers used, on average, 10% of their capacity (Glanz, 2012). Both intentional overcapacity and failure to consolidate and decommission old equipment result in **very low utilization rates**.

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
