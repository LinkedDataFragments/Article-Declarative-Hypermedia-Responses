## Introduction
{:#introduction}
Humans can browse the Web by following _links_ from one page to another.
This _human_ interface is only one of the possible Web interfaces that exist.
Next to humans, machines also heavily make use of the Web
through Web Application Programming Interfaces (Web APIs).
Two architectural styles for Web APIs can be distinguished.
First, some APIs are based on the concept of Remote Procedure Calling (RPC),
in which HTTP requests correspond to procedure or method calls of internal programs.
Second, other APIs are based on [Representational State Transfer (REST)](cite:citesAsAuthority rest),
in which HTTP resources are linked and described to each other,
simular to how the human web works.
In the case of REST, _hypermedia controls_ are used to declaratively instruct clients
on how they can use an interface.
An advantage of REST over RPC is that these hypermedia controls
are self-descriptive, and can be reused across different interfaces.
Once they are implemented, clients can automatically interact interfaces
using these self-descriptive hypermedia controls
without having to refer to external documentation.
Self-descriptiveness is however a relative notion,
because it requires a set of primitives that need to be agreed upon,
which typically are [HTTP](cite:citesAsAuthority http) methods such as GET and POST in the case of RESTful applications.

According to the [Linked Data principles](cite:citesAsAuthority linkeddata),
HTTP URIs should be used browse the Semantic Web, which can be seen as _the Web for machines_.
As the [RDF](cite:citesAsAuthority spec:rdf) data model uses URIs as primary data element,
hypermedia controls can be encoded using this model, so that machines can use and understand them.
Amundsen identifies nine [_"Hypermedia Factors"_](cite:citesAsAuthority hypermediatypes)
that can be used to describe hypermedia behaviors.
While RDF natively supports the first hypermedia factor, i.e., _outbound links_,
it provides no support for more advanced _templated links_.
The latter corresponds to HTML forms on Web pages, such as a form for searching books through a library's website.
One part of the [Hydra Core Vocabulary](cite:citesAsAuthority hydra) attempts to fill this gap
by representing HTML controls as Linked Data for machines.

This vocabulary is for example used in the [Triple Pattern Fragments (TPF)](cite:citesAsAuthority ldf) framework
for describing triple pattern query interfaces.
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

Without the Hydra Core Vocabulary, clients would need a hard-coded API contract.
But _with_ it, clients can automatically understand that by providing a certain set of parameters,
a certain request to the API can be made.
However, the Hydra Core Vocabulary is not capable of describing the link's [_control data_](cite:cites hypermediatypes)
on _how_ these parameters will be used,
i.e., what kind of response will be returned based on the given request.
In order to reach smarter clients, they also need to know in what way the parameters
will contribute to the response.
This would not only allow clients to derive the parameters that have to be used to perform a certain request,
but also how the parameters are used to form the response.

In the case of TPF for example, the subject, predicate and object IRI parameters are described,
but it is nowhere described that the interface necessarily performs a triple pattern query on the dataset using these parameters.
The server could for example return the _negation_ of the given triple pattern query on that dataset instead,
as there is no provided method for distinguishing between these different behaviours with the same input parameters.

In this article, we introduce and compare different approaches
for describing the responses of such hypermedia-driven API responses.
We discuss approaches based on custom vocabularies,
the recent W3C recommendation [SHACL](cite:citesAsAuthority spec:shacl),
the [SPIN modeling vocabulary](cite:citesAsAuthority spec:spin)
and the [Web Ontology Language (OWL)](cite:citesAsAuthority spec:owl).
