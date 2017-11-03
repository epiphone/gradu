# Thesis topic: Migrating a web application to FaaS

## Motivation

Function as a Service (FaaS or serverless) is defined as a cloud-native platform for short-running, stateless computation and event-driven applications which scales up and down instantly and automatically and charges for actual usage at a millisecond granularity. Unlike SaaS or PaaS that are always running, but scale on-demand, serverless workloads run on-demand, and consequently, scale on-demand

![https://specify.io/concepts/serverless-baas-faas](https://specify.io/assets/serverless-automation-7265d1b1cc7ae92e9559995db6dd680fce120ab97f65a5c70edbd7fa71e41acd.png)
[lähde](https://specify.io/concepts/serverless-baas-faas)

The two main benefits of FaaS (as I see them) are gains in developer productivity (less time spent on operations/infrastructure vs. features) and decreased hosting costs. 

> I don't have to manage a virtual machine, operating system, patch management, scaling service, load balancing, availability, fault tolerance, provisioning, anti-virus, anti-malware, vulnerability scanning, continuous monitoring, access control, rightsizing, server tuning, intrusion detection, hardware affinity, OS dependencies [...] and I only pay for what I use ([Groat & Lu, 2017](https://www.slideshare.net/AmazonWebServices/serverless-design-patterns-for-rethinking-traditional-enterprise-application-approaches-aws-public-sector-summit-2017))

These benefits in mind I thought it'd be worthwhile to focus on the topic of migrating an existing web app into FaaS. Potential **research questions** or items to address in the thesis include
- why should a web app be migrated to FaaS?
- how do you migrate a web app to FaaS?
  - in which ways does the app need to be changed?
  - how laborious is the migration?
- evaluating the end result, ie. how does migrating a web app into FaaS effect its quality?
  - performance, maintainability and other quality attributes
  - developer experience, as in ease of local development, testing, deployment...
  - hosting costs

## Various incoherent thoughts

- how should the app be changed?
  - changes both in architecture and code-level
  - from synchronous to event-driven?
  - remodularization from a monolith to microservices?
  - replacing internal modules with external services? db, notifications, logging, monitoring, ...
- developer experience
  - devops -> no-ops?
  - > "We use Lambda primarily to improve developer efficiency and to allow dev teams to own their own operations end-to-end, with cost efficiency only a secondary goal. It's been great for that as it's a small enough thing to integrate with that any given developer can learn the entire operations stack (for their team's services) well enough to work on it themselves."
- addressing the general problems of distributed systems: overhead, distributed transactions, ...
- cold starts, vendor lock-in and other unsolved issues in FaaS
- does FaaS support good architecture design principles?
  - > Different constraints drive different design choices; historically good architecture optimized for what you've got, forgetting principles like isolation and decoupling. With Lambda there's no more financial incentive to bundle services
- fat vs thin lambdas: the whole app as one huge lambda, each API endpoint as its own lambda, something in the middle?
- migrating piece by piece or all at once? Is there a logical place to start?
- do we end up with more or less code?
  - >  A lot of the infra code is gone
- security https://snyk.io/blog/serverless-security-implications-from-infra-to-owasp/
- considering the starting point: the amount of work and benefits gained vary when migrating from e.g. a self-hosted PHP app versus a modern PaaS-hosted app. The latter should be easier but the former has more to gain. Skipping an entire generation?

## The app to migrate

https://tacit.space/ is a modern(ish) web application for taking, organizing and sharing notes. It consists of about 30k lines of Javascript and Typescript and it includes many of your typical web app features: REST API, single page app UI, complicated role-based authorization, some (soft) real-time features, email and SMS notifications, credit card billing, separate admin tools, dependencies to external services etc. The app is divided into a frontend and a backend, where the latter is further divided into a handful of distinct services.

Migrating the whole app might not be feasible during the thesis project, so I was thinking of picking and choosing the features most essential to the research questions.

Also, the app currently has only some dozens of active users. Measuring scalability and hosting costs without any actual load can be a bit tricky. Simulated tests to the rescue?

## Problems and open questions

- Research questions are still too vague
- The number of relevant research articles is a bit limited ([examples summaried here](./refs.md)). Less formal articles, blog posts and conference presentations etc. are easily found - not sure if these are ok as thesis references?
- In a thesis like this are you supposed to just report your experiences/findings, or also make suggestions? The research questions listed above are still very subjective. Even the more absolute measures (hosting costs, amount of code) are application-specific.
- Is the topic academic enough for a Master's thesis? 

## Materials
- Relevant research articles summaried [here](./refs.md)
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
