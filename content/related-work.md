## Related Work
{:#related-work}

In this section, we introduce the related work on Web APIs and Web Services,
followed by an overview of technologies for defining constraints in RDF.

### Web APIs and Services

Next to the REST architectural style, the SOAP protocol is often used for letting _Web Services_ interoperate.
Just, like RPC, SOAP requires custom client-side implementation for each Web Service,
as opposed to the more generic REST APIs.
[OWL-S](cite:citesAsAuthority owls) is a vocabulary for describing such Web Services.
It allows services to declare their actions, how they can be used, and how they work.
As opposed to the Hydra Core vocabulary for Web APIs, this leads to tight coupling between servers and clients.

[Verborgh et al. distinguish two types of Web APIs](cite:citesAsAuthority webapifeatures)
in terms of how they expose their functionality.
The first type, which are mostly used today, is the _top-down_ Web API.
This kind of API exposes certain functionality through a _single_ interface,
and requires clients to understand this specific interface.
The second type is the _bottom-up_ Web API,
where an API exposes different functionalities as different _features_.
The second kind of API leads to clients that are not bound to specific providers,
but to specific reusable features.
The authors introduce five principles for the design of such feature-based interfaces:

1. Web APIs should consist of _features_ that implement a common interface.
2. Web APIs should partition their interface to maximize feature _reuse_.
3. Web API responses should advertise the _presence_ of each relevant feature.
4. Each feature should describe its own _invocation mechanics_ and functionality.
5. The impact a feature on a Web API should be _measured_ across implementations.

The concept of declaring the response structure is in line with these principles.
More specifically, it tackles the problem of describing the _functionality_ of a feature.

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
