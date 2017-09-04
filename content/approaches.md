## Approaches
{:#approaches}

In this section, we discuss and compare different approaches
for declaratively describing the responses of Web APIs based on given parameters.
We will use the TPF use case as a running example.
For this, we will extend from the hypermedia control from [](#tpf-controls),
which currently describes the interface input parameters,
to describe the responses to triple pattern queries.

We categorize our four categories,
which will be explained hereafter:
Custom types, SHACL shapes, OWL restrictions, and SPARQL query mapping.

### Custom Types

A simple solution would be to define a new response type at vocabulary-level
for each hypermedia control type that exists.
For our use case, we could introduce a `tpf:TriplePatternQueryResponse` type in a new `tpf` vocabulary,
which refers to a triple pattern query, as shown in [](#approach-customtypes).

<figure id="approach-customtypes" class="listing">
````/code/approach-customtypes.txt````
<figcaption markdown="block">
Triple pattern query response declaration using a custom `tpf:TriplePatternQueryResponse` type.
</figcaption>
</figure>

While this approach may seem very simple to setup at first sight,
it has some significant disadvantages.
For one, as each response type requires a separate RDF type,
clients implement have explicit support for each of these potentially huge number of types.
Instead of small functional building blocks that can be reused,
service providers would have to define new types for each interface that offers different functionality.

### SHACL Shapes

### OWL Restrictions

### SPARQL Query Mapping
