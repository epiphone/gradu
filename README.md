# Migrating a web application to FaaS

> **Abstract:** Serverless computing is a novel cloud computing model based on auto-scaling,ephemeral resources billed at a millisecond granularity.   Serverless has gained interest in the industry but literature on how the model’s characteristics drive application design is still scarce.  This thesis aims to fill the gap by first defining the paradigm along with its origins and surveying for applicable design patterns. The patterns are then applied in an experimental migration process through which 5 new patterns are introduced.  Finally the migration outcome is evaluated in terms of development ease, performance and costs.  The serverless model is found to deliver on its promises of elasticity and reduced operational overhead; cost benefit however depends largely on expected traffic shape

## Motivation

Function as a Service (FaaS or serverless) is defined as a cloud-native platform for short-running, stateless computation and event-driven applications which scales up and down instantly and automatically and charges for actual usage at a millisecond granularity. Unlike SaaS or PaaS that are always running, but scale on-demand, serverless workloads run on-demand, and consequently, scale on-demand.

![https://specify.io/concepts/serverless-baas-faas](https://specify.io/assets/serverless-automation-7265d1b1cc7ae92e9559995db6dd680fce120ab97f65a5c70edbd7fa71e41acd.png)
[source](https://specify.io/concepts/serverless-baas-faas)

The two main benefits of FaaS (as I see them) are gains in developer productivity (less time spent on operations/infrastructure vs. features) and decreased hosting costs. Also "green computing", reduced operational costs, time-to-market and experimentation.

> I don't have to manage a virtual machine, operating system, patch management, scaling service, load balancing, availability, fault tolerance, provisioning, anti-virus, anti-malware, vulnerability scanning, continuous monitoring, access control, rightsizing, server tuning, intrusion detection, hardware affinity, OS dependencies [...] and I only pay for what I use ([Groat & Lu, 2017](https://www.slideshare.net/AmazonWebServices/serverless-design-patterns-for-rethinking-traditional-enterprise-application-approaches-aws-public-sector-summit-2017))

A serverless platform has a number of unique characteristics and restrictions, including statelessness, lifespan and resource limits on individual functions and an event-driven execution model. Considering these features it's relevant to ask how do we compose the building blocks of serverless (individual functions or lambdas) into larger systems? Do the same rules and patterns apply as in more traditional platforms?

> Will there be patterns for building serverless solutions? How do we combine low granularity basic building blocks of serverless into bigger solutions? How are we going to decompose apps into functions so that they optimize resource usage? For example how do we identify CPU-bound parts of applications built to run in serverless services? Can we use well-defined patterns for composing functions and external APIs? What should be done on the server vs. client (e.g., are thicker clients more appropriate here)? Are there lessons learned that can be applied from OOP design patterns, Enterprise Integration Patterns, etc.? [Baldini et al., 2017](https://arxiv.org/abs/1706.03178)

> Some of these patterns will be in application architecture. For instance how big can FaaS functions get before they get unwieldy? Assuming we can atomically deploy a group of FaaS functions what are good ways of creating such groupings - do they map closely to how we’d currently clump logic into microservices or does the difference in architecture push us in a different direction? ([Fowler, 2016](https://martinfowler.com/articles/serverless.html#TheEmergenceOfPatterns))

## Research questions

The above-mentioned benefits and characteristics in mind I thought it'd be worthwhile to focus on the topic of migrating an existing web app into FaaS. My **research questions** include
1. Why should a web app be migrated to FaaS?
2. What kind of patterns are there for building serverless web application backends?
3. Do the existing patterns have gaps or missing parts, and if so, can we come up with improvements or alternative solutions?
4. How does migrating a web app to FaaS effect its quality?

The first two questions are addressed in the theoretical part of the thesis. Question 1 concerns the motivation behind the thesis and introduces FaaS migration as an important and relevant business problem. Question 2 is addressed by surveying existing literature for patterns thought suitable specifically for the target class of applications.

The third question forms the constructive part of the thesis. I'm planning to implement a subset of the target app in a serverless style, utilizing the surveyed patterns and keeping a log of all the tricky parts. In case the patterns prove unsuitable for the given problem, I'll try to come up with an alternative solution. My guess at this point is that the general patterns described in literature provide an approximate fit but don't necessarily account for all the edge cases and distinct requirements of a real-world application; proposing solutions for these unaccounted-for cases would be the main product of my thesis. This might take the form of either proposing a new pattern or extending existing ones.

The last question consists of comparing the migrated portions of the app to the original version. Since the app currently has only a handful of active users I'm planning to simulate and estimate performance and hosting costs. In addition to this hard data, I'll evaluate differences between quality attributes like maintainability, extendability and testability. I'll also try to address ease of development (or developer experience), since this seems to be one of the most commonly mentioned pain points when it comes to serverless.

## What is **not** included in the topic

- Other kinds of common serverless use cases e.g. batch/stream processing, data pipelines, scientific computing workflows
- Theory of system migration or refactoring in general (although I'll probably have to make some references to the topic)
- Inner workings of serverless runtimes (again, might have to mention briefly)

## Rendering diagrams

Rendering `.dot` diagrams:
`dot -Tpng src/image-manager-serverless.dot -o src/img/image-manager-serverless.png`
