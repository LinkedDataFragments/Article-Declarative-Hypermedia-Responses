## Related Work
{:#related-work}

Next to the REST architectural style, the SOAP protocol is often used for letting _Web Services_ interoperate.
Just, like RPC, SOAP requires custom client-side implementation for each Web Service,
as opposed to the more generic REST APIs.
[OWL-S](cite:citesAsAuthority owls) is a vocabulary for describing such Web Services.
It allows services to declare their actions, how they can be used, and how they work.
As opposed to the Hydra Core vocabulary, this leads to tight coupling between servers and clients.

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
