## Approaches for Declarative Response Description
{:#approaches}

In this section, we discuss and compare different approaches
for declaratively describing the responses of Web APIs based on given parameters.
We will use the TPF use case as a running example.
For this, we will extend from the hypermedia control from [](#tpf-controls),
which currently describes the interface input parameters,
to describe the responses to triple pattern queries.

The four approaches that will be explained hereafter are
Custom types, SHACL shapes, SPIN SPARQL queries and OWL restrictions.
For each approach, we will provide a score for the model criteria from [](#comparison-model),
which are summarized in [](#model-scores).

<figure id="model-scores" class="table" markdown="1">

| Criterion       | Custom Types | SHACL | SPIN | OWL |
| --------------- |:------------:|:-----:|:----:|:---:|
| RDF Complexity  | ◌            | ◑     | ◉    | ◉   |
| Expressivity    | ◯            | ◉     | ◑    | ◯   |
| Composability   | ◯            | ◉     | ◉    | ◉   |
| Discoverability | ◉            | ◑     | ◑    | ◑   |
| Adoptability    | ◌            | ◉     | ◑    | ◉   |

<figcaption markdown="block">
Qualitative scores (very low ◌, low ◯, medium ◑, high ◉) for three different approaches for
declaring interface responses based on the model from [](#comparison-model).
</figcaption>
</figure>

### Custom Types

A simple solution is to define a new response type at vocabulary-level
for each hypermedia control type that exists.
For our use case, we could introduce a (hypothetical) `tpf:TriplePatternQueryResponse` type in a new `tpf` vocabulary,
which refers to a triple pattern query, as shown in [](#approach-customtypes).

<figure id="approach-customtypes" class="listing">
````/code/approach-customtypes.txt````
<figcaption markdown="block">
Triple pattern query response declaration using a custom type,
with `ex:responseType` referring to this type.
</figcaption>
</figure>

The advantages of this approach are that it is very simple to set up,
and is easily _discoverable_.
However, it has some significant disadvantages.
For one, as each response type requires a separate RDF type,
and clients need explicit support for a potentially huge number of types.
Instead of having small reusable functional building blocks,
new types have to be defined for each interface that offers different functionality.
As opposed to indirect hierarchical types as is the case with [MIME types](cite:citesAsAuthority mimetypes),
RDF enables more explicit basic composition of types by attaching multiple types and subclassing.

### SHACL Shapes
{:#approach-shacl}

The SHACL vocabulary is designed for defining shape constraints to validate RDF graphs against,
which allows us to describe the shape of our responses.
In our TPF use case, we could make our search form a parameterizable shape,
and declare the triple pattern query as a [SPARQL](cite:citesAsAuthority spec:sparqllang) `SELECT` query,
as shown in [](#approach-shacl).

The interface input parameters and the response shape parameters are declared separately.
The former is defined using Hydra, while the latter is defined using SHACL.
As these parameters are—and should always be—equal for allowing output to be fully defined using input,
one of the two methods could be deprecated in favor of the other.
The Hydra variables are simpler, but also less expressive.
SHACL parameters are much more expressive because they are also SHACL property shapes,
which means that the full expressivity of SHACL constraints can be used on these parameter values.
SHACL parameter names are, however, not defined in the same way as Hydra variable names.
Hydra allows variable names to be set using the `hydra:variable` predicate.
Instead, SHACL parameter names are derived from the IRI in `sh:path`.

<figure id="approach-shacl" class="listing">
````/code/approach-shacl.txt````
<figcaption markdown="block">
Triple pattern query response declaration using a SHACL shape
that is a subclass of `sh:Parameterizable` and `sh:SPARQLSelectExecutable`.
</figcaption>
</figure>

In summary, SHACL shapes are very expressive for declaring responses of Web APIs.
Furthermore, the expressivity from the SPARQL query language and JavaScript are inherited thanks to
the SHACL extensions [SHACL-SPARQL](https://www.w3.org/TR/2017/REC-shacl-20170720/#sparql-constraints)
and [SHACL-JS](https://www.w3.org/TR/2017/NOTE-shacl-js-20170608/).

### SPIN SPARQL Queries

The [SPIN vocabulary](cite:citesAsAuthority spec:spin) allows SPARQL queries to be defined in a triple representation,
which SHACL does not support.
The advantage of triple-based representations over text-based is that RDF-based tools
can directly use and work with these structures, such as reasoners and query engines.
The disadvantage of triple-based representations is their verbosity compared to a text-based variant.

As our TPF use case requires the representation of a triple pattern query,
we can again trivially represent this as a SPARQL SELECT query using SPIN,
as shown in [](#approach-spin).

<figure id="approach-spin" class="listing">
````/code/approach-spin.txt````
<figcaption markdown="block">
Triple pattern query response declaration using a SPARQL SELECT query using the SPIN vocabulary.
</figcaption>
</figure>

As mentioned before, the SPIN-based query in [](#approach-spin) is indeed
more verbose than the SHACL-SPARQL SELECT query from [](#approach-shacl).
That is because SPIN reifies triple patterns,
which leads to a large amount of triples, even for simple queries.

As our subject, predicate and object variables are now represented as actual resources,
they are explicitly linked with the Hydra variables, which is a semantic advantage.

### OWL Restrictions

While [OWL](cite:citesAsAuthority spec:owl) allows restrictions to be placed on RDF graphs,
it can not do this at the same level of expressivity as SHACL.
Furthermore, the open world assumption on which OWL is based makes it more difficult to describe the closed world of Web API responses.

Our TPF use case can for instance not be represented using OWL restrictions,
because OWL restrictions work on class structures, but not on triple structures.
That is because OWL has been designed for _inferencing_, and not for defining arbitrary constraints on RDF graphs.
Other operations such as type restrictions on instances,
or defining the cardinality of certain aspects are however possible.
