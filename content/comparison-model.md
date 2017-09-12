## Model for Comparison
{:#comparison-model}

In this section, we introduce a simple model for comparing approaches for declaratively representing Web API responses.
Our model consists of different criteria that can influence the choice of a certain approach:
_RDF complexity_, _expressivity_, _composability_, _discoverability_ and _adoptability_.
These will be explained hereafter.
Each response representation approach can receive a qualitative score for each of these criteria.
A suitable approach can then be chosen based on the composite score across these criteria,
which can possibly be weighted depending on the relative importance of these criteria in the use case.

### RDF Complexity

The level of RDF complexity, i.e., how 'deep' the response structure is represented in RDF,
has an influence on how easily such a representation can be used by RDF-based tools.

A SPARQL query could for example be represented as an RDF string literal,
or fully reified using the SPIN vocabulary.
Both approaches have the same meaning, but the former representation requires less effort to represent in RDF,
while the latter provides better compatibility with RDF-based tools, such as reasoners and query engines.
If a subset of such a SPARQL query needs to be taken, an RDF reasoner or query engine
can more easily do this using the reified RDF representation than the string literal.

### Expressivity

The expressivity of an approach for response declaration of an interface
corresponds to the range of responses that can be declared using this approach.

According to the REST principles and the layered architectural style,
clients should require no prior knowledge
about interface functionality except for the agreed-upon primitives.
Simple and few primitives on the one hand lower the barrier for client support,
such as the eight well known [HTTP](cite:citesAsAuthority http) methods.
These primitives should however be sufficiently expressive,
as to allow more advanced operations to be defined on top of them.
Many complex and expressive primitives on the other hand
make it more complex for clients to support them,
but when they are supported, complex operations can more easily be interpreted by clients.

In the case of declaring interface responses,
vocabularies can exist at different levels of expressivity.
One vocabulary may for example only enable simple triple pattern queries to be represented,
which may be simple for a client to parse and handle, but is not very expressive.
Another vocabulary may enable full SPARQL queries to be represented,
which may be more complex for a client to use, but is much more expressive.
By following the REST principles, a well defined restricted vocabulary should be agreed upon
using which, potentially complex, response types can be declared.

### Composability

Just like a [feature-based interface](cite:citesAsAuthority webapifeatures),
response structures could be made up of multiple smaller reusable components that can be _composed_ and _extended_.
This allows clients to only be required to understand these smaller components,
and this could allow more complex composed response types to be interpreted automatically.
Different techniques can lead to different levels of composability.

A certain Web API could for example return a list of people based on a certain query.
Another similar Web API could annotate all these people with their place of birth,
which can be seen as an _extension_ to the first API,
or a _composition_ of the 'query' feature and the 'annotation' feature.
Another composition could for example apply some kind of _sorting_ or _filtering_ feature,
possibly based on certain parameters.

### Discoverability

Certain techniques for declaring response structure are more easily _discoverable_ than others,
meaning that based on the technique,
clients may require more or less effort for _finding_ and _interpreting_ the response structure.
A single text-based identifier for a reponse structure could for example be very simple for clients to detect,
while a reference to the source code that is used to control the Web API requires much more effort from the client.

### Adoptability

While different approaches for Web API response types exist,
the used technologies behind these approaches will have an impact on the adoption rate.
The usage of a new, unknown and non-standard vocabulary will most likely lead to a lower adoption rate
than the usage of vocabulary that is recommended by W3C.
