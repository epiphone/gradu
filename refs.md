# Aihe A: web-sovelluksen migraatio serverless-arkkitehtuuriin

### [Fox, Geoffrey C., et al. "Status of Serverless Computing and Function-as-a-Service (FaaS) in Industry and Research." (2017)](https://arxiv.org/abs/1708.08028)

- definition of FaaS and Serverless as a cloud-native platform for **short-running, stateless** computation  and **event-driven** applications which **scales up and down** instantly and automatically and charges for **actual usage** at a millisecond granularity 
- unlike SaaS or PaaS that are always running, but scale on-demand, serverless workloads run on-demand, and consequently, scale on-demand
- great for end developers as they will not need to know scaling and distributed computing
- debugging was identified as a near term critical problem

### [Baldini, Ioana, et al. "Serverless Computing: Current Trends and Open Problems." (2017)](https://arxiv.org/abs/1706.03178)

### [Adzic, Gojko, and Robert Chatley. "Serverless computing: economic and architectural impact." (2017)](http://www.doc.ic.ac.uk/~rbc/papers/fse-serverless-17.pdf)

This paper presents two case industrial studies of early adopters, showing how migrating an application to the Lambda deployment architecture **reduced hosting costs** – by between 66% and 95% – and discusses how further adoption of this trend might **influence common software architecture design practices**.
- Actual Utilisation, not Reserved Capacity
- Distributed request-level authorization: a request to a Lambda function is equally untrusted whether it comes from a client application directly or from another Lambda function. Two sequential requests from the same client might connect to the same Lambda instance, or completely different ones. As the serverless platforms no longer have a gatekeeper server process, using the traditional model where back-end resources implicitly trust servers is not viable. This means that it is perfectly acceptable, even expected, to allow client applications to directly access resources traditionally considered ‘back-end’.
- Different Services Billed According to Different Utilisation Metrics: given the fact that different AWS services are billed according to different utilisation metrics, it is possible to significantly optimise costs by letting client applications directly connect to resources.
- a better summary here https://blog.acolyer.org/2017/10/19/serverless-computing-economic-and-architectural-impact/
- related blog text https://gojko.net/2017/02/23/serverless-migration-lesson.html

### [Eivy, Adam. "Be Wary of the Economics of" Serverless" Cloud Computing." (2017)](http://ieeexplore.ieee.org/abstract/document/7912239/)

The economic benefits of serverless computing heavily depend on the execution behavior and volumes of the application workload. Serverless has the potential to be a great abstraction offering economic advantages for simple workflows, however it's important to **model the economic impact of your architecture** and operation choices.

### [Villamizar, Mario, et al. "Cost comparison of running web applications in the cloud using monolithic, microservice, and AWS Lambda architectures." (2017)](https://link.springer.com/article/10.1007/s11761-017-0208-y)

A cost comparison of a web application developed and deployed using the same scalable scenarios with three different approaches: 1) a monolithic architecture, 2) a microservice architecture operated by the cloud customer, and 3) a microservice architecture operated by the cloud provider. Test results show that microservices can help reduce infrastructure costs in comparison with standard monolithic architectures. Moreover, the use of services specifically designed to deploy and scale microservices, such as AWS Lambda, **reduces infrastructure costs by 70% or more**, and unlike microservices operated by cloud customers, these specialized services help to guarantee the same performance and response times as the number of users increases.

### [Varghese, Blesson, and Rajkumar Buyya. "Next generation cloud computing: New trends and research directions." (2017)](http://www.sciencedirect.com/science/article/pii/S0167739X17302224)

The use of serverless computing will increase given that billions of devices will need to be connected to the edge of the network and data centers. It will not be feasible to have idle servers in resource constrained environments. The challenges that will hinder the widespread adoption of serverless computing will be the **radical shift in the properties of an application** that a programmer will need to focus on; not latency, scalability and elasticity, but those that relate to the modularity of an application, such as **control and flexibility**. Another challenge is developing programming models that will allow for **high-level abstractions** to facilitate serverless computing. The effect and trade-offs of using traditional external services along with serverless computing services will need to be investigated in orchestrating future cloud-based systems.

# Aihe B: lähdekoodin avustettu modularisointi

## Combining structural and semantic source code analysis

### [Bavota, Gabriele, et al. "Improving software modularization via automated analysis of latent topics and dependencies." (2014)](http://dl.acm.org/citation.cfm?id=2559935)

Oftentimes, during software maintenance the original program modularization decays, thus reducing its
quality. One of the main reasons for such architectural erosion is suboptimal placement of source-code classes
in software packages. To alleviate this issue, we propose an automated approach to help developers improve
the quality of software modularization. Our approach **analyzes underlying latent topics in source code as
well as structural dependencies to recommend (and explain) refactoring operations** aiming at moving a class
to a more suitable package. The topics are acquired via Relational Topic Models (RTM), a probabilistic topic
modeling technique.
- the proposed approach avoids the creation of a whole new remodularization (and the consequent creation/removal of existing packages), proposing a set of move class operations that can be applied independently from each other
- the results achieved indicated that more than 70% of the recommendations provided by R3 with high confidence level were considered meaningful by developers
- remodularization/refactoring technique based only on software quality metrics is not sufficient
- the final word about any refactoring operation should be left up to developers, discouraging the implementation of fully automated refactoring tools

### [Chhabra, Jitender Kumar. "Improving modular structure of software system using structural and lexical dependency." (2017)](http://www.sciencedirect.com/science/article/pii/S0950584916301951)

An approach that considers various types of structural as well as lexical dependencies along with their relative importance to remodularize the Object-Oriented (OO) systems. The main goal of the paper is to generate remodularization solutions that can reflect the developers' perspective (as visible in the well-modularized software system) of remodularization, which is highly desirable in software evolution.

### [Rathee, Amit, and Jitender Kumar Chhabra. "Software Remodularization by Estimating Structural and Conceptual Relations Among Classes and Using Hierarchical Clustering." (2017)](https://link.springer.com/chapter/10.1007/978-981-10-5780-9_9)

A technique of software remodularization by estimating conceptual similarity among software elements (Classes). The proposed technique makes use of **both structural and semantic coupling measurements** together to get much more accurate coupling measures. In particular, the proposed approach makes use of lexical information extracted from six main parts of the source code of a class, namely comments, class names, attribute names, method signatures, parameter names and method source code statements zone. Simultaneously, it also makes use of counting of other class’s member functions used by a given class as a structural coupling measure among classes. Structural coupling among software elements (classes) are measured using **information-flow based coupling metric** (ICP) and conceptual coupling is measured by **tokenizing source code and calculating Cosine Similarity**. Clustering is performed by performing **Hierarchical Agglomerate Clustering** (HAC).

### [Saeidi, Amir, et al. "On the Effect of Semantically Enriched Context Models on Software Modularization." (2017)](https://arxiv.org/abs/1708.01680)

Many of the existing approaches for program comprehension rely on the linguistic information found in source code, such as identifier names and comments. Semantic clustering is one such technique for modularization of the system that relies on the informal semantics of the program, encoded in the vocabulary used in the source code. **Treating the source code as a collection of tokens loses the semantic information** embedded within the identifiers. We try to **overcome this problem by introducing context models for source code identifiers** to obtain a semantic kernel, which can be used for both deriving the topics that run through the system as well as their clustering. Both of the context models give results that are superior to the plain vector representation of documents. The proposed approach in introducing a context model for source code identifiers paves the way for building tools that support developers in program comprehension tasks such as application and domain concept location, software modularization and topic analysis.
- syntactic analysis of source code allows us to extract contextual information about identifiers such as dependency relationships between identifiers and their type information


## Semantic/text-based methods

### [Palomba, Fabio, et al. "A textual-based technique for smell detection." (2016)](http://ieeexplore.ieee.org/abstract/document/7503704/)

In this paper, we present TACO (Textual Analysis for Code Smell Detection), a **technique that exploits textual analysis to detect a family of smells of different nature and different levels of granularity**. We run TACO on 10 open source projects, comparing its performance with existing smell detectors purely based on structural information extracted from code components. The analysis of the results indicates that TACO's precision ranges between 67% and 77%, while its recall ranges between 72% and 84%. Also, TACO **often outperforms alternative structural approaches** confirming, once again, the usefulness of information that can be derived from the textual part of code components.
- most previous work on code smell detection relies on structural metrics, such as size and complexity metrics
- in this paper, we introduce a textual-based technique that (i) exploits the textual information contained in source code elements and (ii) relies on textual similarity between code elements characterizing a code component
- we found some complementarity between textual and structural information, suggesting that their combination could be beneficial to obtain better detection accuracy

### [Chong, Chun Yong, and Sai Peck Lee. "Automatic Clustering Constraints Derivation from Object-Oriented Software Using Weighted Complex Network with Graph Theory Analysis." (2017)](http://www.sciencedirect.com/science/article/pii/S0164121217301772)
Classic unsupervised software clustering techniques have proven to be useful to aid in recovering a high-level abstraction of the software design of poorly documented or designed software systems. However, there is a lack of work that integrates constrained clustering for the same purpose to help improve the modularity of software systems. Nevertheless, due to time and budget constraints, it is laborious and unrealistic for domain experts who have prior knowledge about the software to review each and every software artifact and provide supervision on an on-demand basis. We aim to fill this research gap by proposing an automated approach to derive clustering constraints from the implicit structure of software system based on graph theory analysis of the analysed software.


## Optimization-based methods

### [Mansoor, Usman, et al. "Multi-objective code-smells detection using good and bad design examples." (2017)](https://link.springer.com/content/pdf/10.1007%2Fs11219-016-9309-7.pdf)

Code-smells are identified, in general, by using a set of detection rules. These rules are manually defined to identify the key symptoms that characterize a code-smell using combinations of mainly quantitative (metrics), structural, and/or lexical information. We propose in this work to consider the **problem of code-smell detection as a multi-objective problem where examples of code-smells and well-designed code are used to generate detection rules**. To this end, we use multi-objective genetic programming (MOGP) to find the best combination of metrics that maximizes the detection of code-smell examples and minimizes the detection of well-designed code examples.

### [Paixao, Matheus, et al. "An Empirical Study of Cohesion and Coupling: Balancing Optimisation and Disruption." (2017)](http://ieeexplore.ieee.org/abstract/document/7892940/)

A multiobjective evolutionary approach that **minimises disruption while maximising cohesion/coupling improvement**. This allows developers to balance reticence to disrupt existing modular structure, against their competing need to improve cohesion and coupling. The multiobjective approach is able to find modular structures that improve the cohesion of developers’ implementations by 22.52%, while causing an acceptably low level of disruption (within that already tolerated by developers).

## Mining version histories

### [Palomba, Fabio, et al. "Mining version histories for detecting code smells." IEEE Transactions on Software Engineering 41.5 (2015)](http://ieeexplore.ieee.org/abstract/document/6963448/)

While most of the detection techniques just rely on structural information, many code smells are intrinsically characterized by how code elements change overtime. In this paper, we propose Historical Information for Smell deTection (HIST), an approach **exploiting change history information to detect instances of five different code smells**.


## Program comprehension & visualization

### [Sangal, Neeraj, et al. "Using dependency models to manage complex software architecture." ACM Sigplan Notices. Vol. 40. No. 10. ACM, 2005.](https://dl.acm.org/citation.cfm?id=1094824)
An approach to managing the architecture of large software systems is presented. Dependencies are extracted from the code by a conventional static analysis, and shown in a tabular form known as the **Dependency Structure Matrix** (DSM). A variety of algorithms are available to help organize the matrix in a form that reflects the architecture and highlights patterns and problematic dependencies.

### [Mahmoud, Anas, and Gary Bradshaw. "Semantic topic models for source code analysis." (2017)](https://link.springer.com/article/10.1007/s10664-016-9473-1)

The textual content of source code, embedded in its identifiers, comments, and string literals, tends to be sparse in nature. This prevents classical topic modeling techniques, typically used to model natural language texts, to generate proper models when applied to source code. We propose a **novel approach for topic modeling designed for source code**. The proposed approach exploits the basic assumptions of the cluster hypothesis and information theory to discover semantically coherent topics in software systems. The results show that our approach produces stable, more interpretable, and more expressive topics than classical topic modeling techniques without the necessity for extensive parameter calibration.

### [Falleri, J-R., et al. "Automatic extraction of a wordnet-like identifier network from software." (2010)](http://ieeexplore.ieee.org/abstract/document/5521783/)

A large part of the time allocated to software maintenance is dedicated to the program comprehension. Many approaches that uses the program structure or the external documentation have been created to assist program comprehension. However, the identifiers of the program are an important source of information that is still not widely used for this purpose. In this article, we propose an approach, based upon Natural Language Processing techniques, that automatically extracts and organizes concepts from software identifiers in a WordNet-like structure that we call *lexical views*. These lexical views give useful insight on an overall software architecture and can be used to improve results of many software engineering tasks.
- automatically construct an ontology from the software system, by extracting concepts from identifier names in the source code and organizing the identifiers into a WordNet-like structure; comprises of techniques such as tokenization of names and part-of-speech tagging

### [Beck, Fabian, Jan Melcher, and Daniel Weiskopf. "Identifying modularization patterns by visual comparison of multiple hierarchies." (2016)](http://ieeexplore.ieee.org/abstract/document/7503712/)
An interactive visualization approach that compares the current modularization of a system to several software clustering results. We discuss typical modularization patterns that indicate criteria used for structuring the software or suggest opportunities for partial remodularization of the system.

### [Sun, Xiaobing, et al. "Using Hierarchical Latent Dirichlet Allocation to Construct Feature Tree for Program Comprehension." (2017)](https://www.hindawi.com/journals/sp/2017/4382348/abs/)

 An approach to generate a **feature tree based on hierarchical Latent Dirichlet Allocation** (hLDA), which includes two hierarchies, the feature hierarchy and file structure hierarchy. The feature hierarchy shows the features from abstract level to detailed level, while the file structure hierarchy shows the classes from whole to part. Empirical results show that the feature tree can produce a view for the features and files, and the clustering of classes in the package in our approach is better (in terms of recall) than the other clustering approach, that is, hierarchical clustering.


## Meta & background

### [Tufano, Michele, et al. "When and why your code starts to smell bad." (2015)](http://dl.acm.org/citation.cfm?id=2818805)

While the repercussions of smells on code quality have been empirically assessed, there is still only anecdotal evidence on when and why bad smells are introduced. To fill this gap, we conducted a large empirical study over the change history of 200 open source projects and **investigated when bad smells are introduced by developers, and the circumstances and reasons behind their introduction**. Our findings mostly **contradict common wisdom stating that smells are being introduced during evolutionary tasks**. In the light of our results, we also call for the need to develop a new generation of recommendation systems aimed at properly planning smell refactoring activities.
- most of times code artifacts are affected by  bad smells since their creation: highlights that the  introduction  of  most smells can simply be avoided by performing quality checks at commit  time
- code  artifacts  becoming  smelly  as consequence of  maintenance  and  evolution activities are characterized by peculiar metrics’ trends, different from those of clean artifacts: encourages the development of recommenders able of alerting software developers when changes  applied to code artifacts result in worrisome metric trends

### [Candela, Ivan, et al. "Using cohesion and coupling for software remodularization: Is it enough?." (2016)](http://dl.acm.org/citation.cfm?id=2928268)

Refactoring and, in particular, remodularization operations can be performed to repair the design of a software system and remove the erosion caused by software evolution. Various approaches have been proposed to support developers during the remodularization of a software system. Most of these approaches are based on the **underlying assumption that developers pursue an optimal balance between cohesion and coupling when modularizing the classes of their systems**. Thus, a remodularization recommender proposes a solution that implicitly provides a (near) optimal balance between such quality attributes. However, there is still **no empirical evidence that such a balance is the desideratum** by developers. This article aims at analyzing both objectively and subjectively the aforementioned phenomenon. Specifically, we present the results of (1) a large study analyzing the modularization quality, in terms of package cohesion and coupling, of 100 open-source systems, and (2) a survey conducted with 29 developers aimed at understanding the driving factors they consider when performing modularization tasks. The results achieved have been used to distill a set of lessons learned that might be considered to design more effective remodularization recommenders.
- developers are often at a crossroad [Cunningham 1993] regarding (1) implementing it without compromising the original design integrity or (2) implementing it in the most straightforward way by stretching a bit the rules of the existing design if needed (i.e., by introducing technical debt)
- the continuous changes made during software evolution generally tend to “erode” the original design of the system [Parnas 1994]
- cohesion and coupling are **probably not enough** to recommend meaningful remodularization solutions from the developers’ point of view, reinforcing the need for multiobjective software remodularization techniques seeking for the optimization of several different factors and allowing the developer to (1) prioritize specific objectives and (2) provide constraints
that the optimization technique should respect while generating the recommended solution
- tools supporting a “Big Bang” remodularization have a limited applicability, while interactive recommenders proposing fine-grained refactoring operations seem to be more adequate during software evolution
- The software engineering research community should increase its effort in producing and advertising high-quality refactoring/remodularization tools: more often than not very good techniques that underwent an exhaustive and successful empirical validation are never implemented and publicly released as part of a concrete, working tool

### [Parnas, David Lorge. "On the criteria to be used in decomposing systems into modules." (1972)](https://blog.acolyer.org/2016/09/05/on-the-criteria-to-be-used-in-decomposing-systems-into-modules/)
- the effectiveness of a “modularization” is dependent upon the criteria used in dividing the system into modules.
- it is almost always incorrect to begin the decomposition of a system into modules on the basis of a flowchart. We propose instead that one begins with a list of difficult design decisions or design decisions which are likely to change. Each module is then designed to hide such a decision from the others.

### [Parnas, David Lorge. "Designing software for ease of extension and contraction." (1979)](https://blog.acolyer.org/2016/10/31/designing-software-for-ease-of-extension-and-contraction/)
Designing software to be extensible and easily contracted is discussed as a special case of **design for change**. The most critical step is the design of a software structure called the **"uses" relation**.
- we say of two programs A and B that A uses B if correct execution of B may be necessary for A to complete the task described in its specification
- if you allow unconstrained uses relations, then parts of the system become highly interdependent: the uses relation should therefore be restricted so that it is loop (cycle) free
- based on the uses relation, we can identify a hierarchy of levels within the system: if such a hierarchical ordering exists, then each level offers a testable and usable subset of the system… The design of the “uses” hierarchy should be one of the major milestones in a design effort
