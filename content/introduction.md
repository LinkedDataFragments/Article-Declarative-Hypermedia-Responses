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
<span class="comment" data-author="RV">This gives the feeling that there are only two styles, whereas it is more nuanced in practice.</span>
in which HTTP resources are linked and described to each other,
similar to how the human web works.
In the case of <ins class="comment">pure</ins> REST APIs, _hypermedia controls_ declaratively instruct clients
on how they can use an interface.
An advantage of REST over RPC is that these hypermedia controls
are self-descriptive, and can be reused across different interfaces.
Once they are implemented, clients can automatically interact with interfaces
through these self-descriptive hypermedia controls
without having to refer to external documentation.
However, self-descriptiveness is a _relative_ notion:
depending on the set of primitives supported by a client,
an interface exposed by a server might or might not describe itself.

According to the [Linked Data principles](cite:citesAsAuthority linkeddata),
HTTP URIs should be used to identify concepts on the Semantic Web, which can be seen as _the Web for machines_.
As the [RDF](cite:citesAsAuthority spec:rdf) data model uses URIs as primary data element,
hypermedia controls can be encoded using this model, so that machines can use and understand them.
Amundsen identifies nine [_"Hypermedia Factors"_](cite:citesAsAuthority hypermediatypes)
to identify hypermedia behaviors.
While RDF natively supports the _outbound links_ hypermedia factor,
it provides no support for more advanced _templated links_.
The latter corresponds to HTML forms on Web pages, such as a form for searching books through a library's website.
One part of the [Hydra Core vocabulary](cite:citesAsAuthority hydra) attempts to fill this gap
by representing HTML controls as Linked Data for machines.

The Hydra Core vocabulary is for example used in the [Triple Pattern Fragments (TPF)](cite:citesAsAuthority ldf) interface
for describing a query form.
TPF interfaces expose hypermedia controls that afford triple pattern queries on top of certain datasets.
This allows clients to consume data from datasets that are exposed behind TPF interfaces using these self-descriptive controls,
as shown in [](#tpf-controls).
In this example, the `hydra:search` predicate is used to link a search form to a dataset.
This search form has an IRI template string which allows certain variables to be filled in.
These variables are declared in the range of `hydra:mapping`,
which are in this case `'s'`, `'p'` and `'o'`, which respectively are an
[RDF](cite:citesAsAuthority spec:rdf) subject, predicate and object.

<figure id="tpf-controls" class="listing">
````/code/tpf.txt````
<figcaption markdown="block">
Declarative triple pattern query control on the DBpedia TPF interface using the Hydra Core Vocabulary in the TriG syntax.
</figcaption>
</figure>

Without the Hydra Core Vocabulary, clients would need a hard-coded API contract.
With this markup, clients can automatically understand that by providing a certain set of parameters,
a certain request to the API can be made.
However, the Hydra Core Vocabulary is not capable of describing the link's [_control data_](cite:cites hypermediatypes)
on _how_ these parameters will be used,
i.e., what kind of response will be returned based on the given request.
In order to reach smarter clients, they also need to know in what way the parameters
will contribute to the response.
This would not only allow clients to derive _what_ parameters are used for a certain request,
but also _how_ these parameters form the response.

In the case of TPF for example, the subject, predicate and object IRI parameters are described,
but it is nowhere described that the interface necessarily performs a triple pattern query on the dataset using these parameters.
The server could for example return the _negation_ of the given triple pattern query on that dataset instead,
<span class="comment" data-author="RV">Very difficult example (I don't understand it). How about instead you give three possible simple things the server could do with the same data? I also think we should more explicitly say what exactly “performing a triple pattern query” means, i.e., simply returning all triples in the dataset that match a certain pattern.</span>
<span class="comment" data-author="RV">I also wonder whether TPF is maybe too difficult of an example. The difficulty here is that TPF works on the metalevel, i.e., we use triples to describe hypermedia controls, and TPF then also queries triples. Another example would be, let's say, a firstname/lastname/employee_number interface, where there is a certain expectation of that this interface does, but that is not made explicit and hence could have different effects in practice.</span>
as there is no provided method for distinguishing between these different behaviours with the same input parameters.

In this article, we introduce and compare different approaches
for describing the responses of such hypermedia-driven API responses.
We discuss approaches based on custom vocabularies,
the recent W3C recommendation [SHACL](cite:citesAsAuthority spec:shacl),
the [SPIN modeling vocabulary](cite:citesAsAuthority spec:spin),
and the [Web Ontology Language (OWL)](cite:citesAsAuthority spec:owl).
