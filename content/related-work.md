## Related Work
{:#related-work}

In this section, we introduce the related work on Web APIs and Web Services,
followed by an overview of technologies for defining constraints in RDF.

### Web APIs and Services

Next to the REST architectural style, the SOAP protocol is often used for letting _Web Services_ interoperate.
Just, like RPC, SOAP requires custom client-side implementation for each Web Service,
which leads to tighter coupling between servers and clients,
as opposed to the more generic REST APIs.
[OWL-S](cite:citesAsAuthority owls) is a vocabulary for describing such Web Services.
It allows services to declare their actions, how they can be used, and how they work.

[Verborgh et al. distinguish two types of Web APIs](cite:citesAsAuthority webapifeatures)
in terms of how they expose their functionality.
The first type, which are mostly used today, is the _top-down_ Web API.
This kind of API exposes certain functionality through a _single_ interface,
and requires clients to understand this specific interface.
The second type is the _bottom-up_ Web API,
where an API exposes different functionalities as different _features_,
where each feature should describe its own _functionality_.
The second kind of API leads to clients that are not bound to specific providers,
but to specific reusable features.
The concept of declaring the response structure is
in line with these principles of feature-based interfaces.

### RDF Constraints

SHACL is a recent W3C recommended vocabulary that allows
RDF shapes to be defined and composed for constraint checking and validation.
The [SPIN vocabulary](cite:citesAsAuthority spec:spin) can be seen as the predecessor
to SHACL for specifying rules and constraints.
It is more lightweight than SHACL, but thereby also less expressive.
The SPIN vocabulary is based on the SPARQL query language for defining these constraints,
where triple patterns can be composed as graph patterns, which in turn can be composed as more complex graph patterns.
Alternatively, [OWL](cite:citesAsAuthority spec:owl) and [RDF Schema (RDFS)](cite:citesAsAuthority spec:rdfs)
could be used to define constraints on certain targets.
The main difference between SHACL and OWL is that SHACL works under the _closed world assumption_,
while OWL works under the _open world assumption_.
In practise, the latter makes data validation more complex, which is part of the motivation for SHACL's creation.
