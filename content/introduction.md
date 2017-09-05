## Introduction
{:#introduction}

The Web has become the most important global knowledge base for humanity.
This is partly because of the simple concepts our Web is build upon,
which makes it simple for humans to understand and browse.

This _human_ interface is only one of the possible Web interfaces that exist.
Next to humans, machines are also heavily making use of the Web,
through the use of Web Application Programming Interfaces (APIs).
Two architectural styles for Web APIs can be distinguished.
First, some APIs are based on the concept of remote-procedure-calling (RPC),
in which HTTP calls correspond to procedure or method calls of internal programs.
Second, other APIs are based are based on [Representational State Transfer (REST)](cite:citesAsAuthority rest),
in which HTTP resources are linked and described to each other,
simular to how the human web works.
_Hypermedia controls_ are used to declaratively instruct clients
on how they can use an interface.
An advantage of REST over RPC is that these hypermedia controls
are self-descriptive, and can be reused across different interfaces.
Once they are implemented, clients can automatically interact interfaces
using these self-descriptive hypermedia controls
without having to refer to external documentation.

Based on the [Linked Data principles](cite:citesAsAuthority linkeddata) and the REST architectural style,
the [Hydra Core Vocabulary](cite:citesAsAuthority hydra) was introduced with the aim of describing Web APIs
using self-descriptive hypermedia controls so that autonomous clients can consume them in the same way as humans consume the Web.
This vocabulary is for example used in the [Triple Pattern Fragments (TPF)](cite:citesAsAuthority ldf) framework
for describing triple pattern interfaces.
TPF interfaces expose hypermedia controls that enable triple pattern queries on top of certain datasets.
This allows clients to consume data from datasets that are exposed behind TPF interfaces using these self-descriptive controls,
as shown in [](#tpf-controls).
In this example, the `hydra:search` predicate is used to link a search form to a dataset.
This search form has a IRI template string which allows certain variables to be filled in.
These variables are declared in the range of `hydra:mapping`,
which are in this case `'s'`, `'p'` and `'o'`, which respectively are an
[RDF](cite:citesAsAuthority spec:rdf) subject, predicate and object.
The `hydra:ExplicitRepresentation` variable representation indicates that the variable values
can include type and language information when filled in.

<figure id="tpf-controls" class="listing">
````/code/tpf.txt````
<figcaption markdown="block">
Declarative triple pattern query control on the DBpedia TPF interface using the Hydra Core Vocabulary in TriG.
</figcaption>
</figure>

While the Hydra Core Vocabulary achieves the goal of describing the _input_ of hypermedia controls,
it is not capable of describing what kind of _output_ it will return based on these the given parameters.
In the case of TPF, the subject, predicate and object IRI parameters are described,
but it is nowhere described that the interface necessarily performs a triple pattern query on the dataset using these parameters.
The server could for example return the _negation_ of the give triple pattern query on that dataset instead,
as there is no provided method for distinguishing between these different behaviours with the same input parameters.

In this article, we introduce and compare different approaches
for describing the responses of such hypermedia-driven API responses.
We discuss approaches based on custom vocabularies,
the recent W3C recommendation [SHACL](cite:citesAsAuthority spec:shacl),
and the [SPIN modeling vocabulary](cite:citesAsAuthority spec:spin).