## Conclusions
{:#conclusions}

In this work, we discuss and compare different approaches
for declaratively describing the responses of hypermedia-driven Web APIs.

As discussed in [](#model-application), we propose the SHACL-based approach as a general solution.
In certain specific use cases, other criteria importance orders may be in place,
which could lead to different answers.

As mentioned in [](##approach-shacl), there is however some overlap between the Hydra variables and SHACL parameters.
As the latter is more expressive, Hydra variables could be deprecated in favor of SHACL parameters.
For ensuring backwards compatibility with clients that only support regular Hydra controls,
these Hydra variables should still be kept in place.

The SHACL-based approach that we propose requires no changes to the existing Hydra controls,
it only requires additional metadata.
This allows clients to make use of this additional metadata if they require knowledge of the response structure of Web APIs.
Clients that _are not_ able to interpret this information will still be able to use the regular Hydra controls.
Furthermore, even if clients _are_ able to interpret this information,
but the server does not declare the response structure,
the client could still use the regular Hydra controls,
by falling back to the assumption-based response structure,
as it is currently being done.

With this hypermedia control extension, clients are able to known what kind of data is returned based on certain input.
This will enable autonomous clients to become smarter,
by making better choices when consuming data from interfaces.
