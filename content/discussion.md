## Discussion
{:#discussion}

Based on our model from [](#comparison-model), there are different ways for choosing between the discussed approaches from [](#approaches).
There is no one approach that is the _winner_ across all criteria,
an appropriate approach depends on the situation.
In this section, we discuss the arguments for preferring certain criteria over others,
and which approaches may be best suited in certain situations.

In many cases, the _adoption_ rate would be of great importance,
unless the approach would be used in a closed-off environment,
which makes declarative response types less useful in the first place.
According to the [best practises for publishing Linked Data](cite:cites ldbestpractises),
standard vocabularies should be reused as much as possible,
because this helps with the inclusion in the Web of data.
Furthermore, multiple tools typically exist to work with these standard vocabularies.

Responses should be declaratively definable at a sufficient level of _expressivity_,
as long as clients are able to interpret them.
Chances of this are higher when standard vocabularies are used,
because these tend to have support in multiple tools.
That is why the adoption criterion will typically have a higher preference over the level of expressivity.

A response declaration can be defined in an expressive way,
but as long as clients are not able to _discover_ it,
the declaration is of not much use.
More expressive response structures may be more complex and difficult for clients to discover,
which is why a trade-off between those two criteria must be defined.

The _composability_ criterion is related to expressivity and discoverability.
If an approach allows very few and simple building blocks to be combined to reach a high level of expressivity,
clients require less hard-coded support for these building blocks, which benefits the discoverability.
Approaches that do not allow composability will require more of these building blocks to
achieve a high level of expressivity, which can negatively impact discoverability.

In situations where RDF-based tools are required for
handling the response declarations, then the _RDF complexity_ criterion is of importance.
Nevertheless, even in cases where non-RDF representations are used,
RDF-based tool processing could still be done by reifying to RDF in a client-side postprocessing step.
The RDF complexity is related to the composability of an approach,
as small building blocks that are defined in granular RDF statements,
can potentially be reused as part of other more complex and therefore expressive declarations.
A high level of RDF complexity can however again negatively impact discoverability due to the higher required client effort.

As mentioned before, choosing an appropriate approach depends on the situation.
For instance, if we require an approach that is based on standards,
is expressive, discoverable and is made up of easily composable building blocks,
then the SHACL shapes approach is be best suited.
But if we require an approach that has a high level of RDF complexity and is sufficiently expressive,
then the SPIN-based approach could be sufficient.
Otherwise, if we value discoverability over adoptability, then custom types might be preferred.

