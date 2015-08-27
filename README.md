# My MSc by Research thesis at University of Hertfordshire

This repositiry contains the Master of Science by Research thesis I wrote at [University of Hertfordshire](http://www.herts.ac.uk).

General information about the programme: [Wikipedia](https://en.wikipedia.org/wiki/Master_of_Research)

The programme lasts for 12 months. In the first 2 months students must defend the progress report. It contains a short introduction to the research area, the motivation/problem statement and the project planning for next 10 months.

Group page: [Compiler Technology and Computer Architecture](http://ctca.eu)


## Introduction
The concepts of the new coordination language __AstraKahn__ are described in [[1]](http://arxiv.org/abs/1306.6029). The language defines the coordination behaviour of asynchronous stateless components (_boxes_) and their orderly interconnection via stream-carrying channels with finite capacity. __AstraKahn__ structures the interconnect using a fixed set of wiring primitives, viz. serial and parallel composition, wrap-around connection and serial replication. Boxes are connected to the network with one or two input channels and one or more output channels. A stateless box does not synchronise data on its input channels; to this end, __AstraKahn__ provides a synchronisation facility called _synchroniser_. Synchronisers are finite state machines for joining messages and sending them on to the output channels. A synchroniser is connected to the network with one or more input and output channels. __AstraKahn__ provides a dedicated language to define synchronisers, while boxes are specified in any conventional programming language. In order to deal with the issue of application progress, __AstraKahn__ attempts to provide an automatic resource and concurrency management based on communication demand.


## Contribution
This thesis focuses on the implementation of synchronisers and their role in the serial replication wiring pattern. We provide some minor syntax improvements and detailed explanation how each language construct should be used. An AstraKahn synchroniser has a non-deterministic behaviour. We give an execution algorithm that defines the ordering of non-deterministic choices made by the synchroniser, and which is a basis for the synchroniser runtime. We implement the language compiler that generates the data structure to be interpreted by the runtime and the communication passport of the synchroniser. The compiler performs semantic and type checking and reports source code errors.

The language report [[1]](http://arxiv.org/abs/1306.6029) explains the machinery behind the serial replication briefly. The serial replication is an important part of __AstraKahn__ and it has to be well-established for the execution environment to be implemented. We analyse the original synchroniser-based approach to fixed points and show how it can be implemented. As a part of the analysis, we give the topological properties of the operand network that are required for the existence of forward and reverse fixed points. The analysis shows that the construction and the debugging of an operand network with a complex fixed point condition can be quite complicated. In order to avoid having to construct complicated operand networks, we provide a simple alternative solution for forward fixed point. Finally, we provide algorithms for the AstraKahn compiler to detect both kinds of fixed point in the operand network.


## What is in

I wrote the thesis and the report in _TeX_. I used [MacTex-2015](https://tug.org/mactex/), _make_ and _vim_. The presentation was made in PowerPoint.

* progress_report/: my progress report
* thesis_(legacy|template)/, figs/, chapters/, appendices/: thesis files
* Bibliography.bib: thesis bibliography
* presentation/: the presentation I prepared for my oral examination
* __Thesis.pdf__: thesis release

To build the thesis from sources:
```
cd thesis_template && make
```
