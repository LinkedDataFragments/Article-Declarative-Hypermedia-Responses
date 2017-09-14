## Conclusions
{:#conclusions}

Much of the Web's current hypermedia control response types are left to the client's interpretation,
which could be done using custom types.
This approach is however hard to sustain, as it leads requires new types for each new response type,
and leads to tight client-server coupling.
If we want to have sustainable and declarative hypermedia response definitions on the Web,
a technique is required that revolves around standards with an adequate level of expressivity and composability,
but is not too difficult for clients to work with.

The SHACL-based approach that we introduce in this work adheres to these requirements.
It is in line with the REST architectural style,
as at its core, it is based on simple building blocks that make it easy for clients to discover and interpret them,
and these building blocks can be combined for reaching a higher level of expressivity.
Furthermore, as SHACL is a W3C recommendation, it can lead to a higher adoption rate.
Practical usage of this approach is already possible without any new vocabularies or extensions.
If servers expose the _shape_ of their control responses,
clients that _understand_ SHACL and Hydra can interpret this to determine if this control is useful for them.

A response declaration can be seen as the server's _suggested_ way
of consuming the data behind a control, but not necessarily the only way.
Profile-based negatiation on controls can provide _multiple dimensions_ on how this data can be consumed,
by allowing clients to ask the server for returning the data in a different _application profile_,
which may be more convenient for the client to work with.

With such a hypermedia control extension, clients are able
to known not only what the _input_ of a control is,
but also what kind of data is returned as _output_ based on certain input.
This information is vital for any kind of operation,
just like typed programming languages require declaration
of both the input and output types of operations.
This extension will enable autonomous clients to work with such controls in a better way,
as they will be able to know what output to expect from a certain control.
This will for instance allow clients to select only the controls that will
produce the response structure that the client can work with,
or start preparing a response data structure _before_ the actual control response is even received.
Nevertheless, future work is still required in this direction,
to empirically validate the practisal feasibility of this approach.
Furthermore, algorithms will need to be developed to efficiently generate such declarations server-side,
and to work with them client-side.
