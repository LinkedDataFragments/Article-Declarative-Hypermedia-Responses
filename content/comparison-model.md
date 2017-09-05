## Model for Comparison
{:#comparison-model}

In this section, we introduce a simple model for comparing approaches for declaratively representing Web API responses.
Our model consists of different criteria: reification, expressivity and adoption.
These will be explained hereafter.
Each reponse representation approach can receive a qualitative score for each of these criteria.
A suitable approach can then be chosen based on the composite score across these criteria,
which can possibly be weighted depending on the relative importance of these criteria in the use case.

### Reification

The level of reification, i.e., how 'deep' the response structure is represented in RDF,
has an influence on how easy such a representation can be used by RDF-based tools.

A SPARQL query could for example be represented as an RDF string literal,
or fully reified using the SPIN vocabulary.
Both approaches have the same meaning, but the former representation is simpler,
while the latter provides better compatibility with RDF-based tools, such as reasoners and query engines.
If a subset of such a SPARQL query needs to be taken, an RDF reasoner or query engine
can more easily do this using the reified RDF representation than the string literal.

### Expressivity

Vocabularies for declaring response types can exist at different levels of expressivity.
One vocabulary may only enable simple triple pattern queries to be represented,
which may be simple for a client to parse and handle, but is not very expressive.
Another vocabulary may enable full SPARQL queries to be represented,
which may be more complex for a client to use, but is much more expressive.

According to the REST principles, clients should require no prior knowledge about interface functionality.
If a server exposes certain functionality,
clients should be able to interpret and make use of this functionality without requiring explicit implementation of it.
Therefore, the approach should be as expressive as possible.

Higher expressivity does however typically lead to higher complexity for client-side parsing and usage,
but also for server-side declaration generation if this would happen dynamically at runtime.
Expressivity and simplicity of usage are contradicting criteria, so a trade-off between these two must be sought out.
The Assembly language is for example very expressive, but its low level of abstraction would make it complex to use.

### Adoption

While different approaches for Web API response types exist,
the used technologies behind these approaches will have an impact on the adoption rate.
The usage of a new, unknown and non-standard vocabulary will most likely lead to a lower adoption rate
than the usage of vocabulary that is recommended by W3C.
