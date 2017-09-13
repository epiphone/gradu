# Gradu

- kompleksisuus ja riippuvuudet
- dynaamisille kielille on vain pinnallisia lint-tyokaluja ym., ei ota huomioon moduulien valisia relaatioita
- strukturaalinen vs semanttinen?
- tyokalu hallitsemaan kompleksisuutta
- perustele Parnas tai Big Ball of Mud?

A tool that helps programmers to figure out the optimal location for any given piece of code
Optimal as in
- low coupling and high cohesion between modules
- minimize unnecessary dependencies
- make easier to change
- aids programmers via suggestions, no automatic modularization

two goals for the tool
- help programmers manage high complexity of software by suggesting module structure
- visualize system's existing structure for comprehension (less important?) i.e. software architecture recovery

Why modularize?
- Software is modularized to make its high complexity manageable


- existing research focuses on OO-software; what about dynamic and multi-paradigm languages i.e. Javascript?
-

three sources of data
- structural (AST, imports, exports)
- semantic (variable naming, comments)
- historical (repository mining)

methods:
- clustering
  - unsupervised vs. semi-supervised (constrained)
- NLP (topic modeling)
- optimization (multi-objective, coupling & cohesion)
- repository change history mining
- graph teory/network analysis?
- other ML?
