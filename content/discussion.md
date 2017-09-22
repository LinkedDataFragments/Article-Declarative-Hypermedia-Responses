## Discussion
{:#discussion}

Based on our model from [](#comparison-model), there are different ways for choosing between the discussed approaches from [](#approaches).
There is no one approach that is the _winner_ across all criteria:
an appropriate approach depends on the situation.
In this section, we discuss the arguments for preferring certain criteria over others,
and which approaches may be best suited in certain situations.

In many cases, the _adoption_ rate would be of great importance,
unless the approach would be used in a closed environment,
which makes declarative response types less useful in the first place.
According to the [best practises for publishing Linked Data](cite:cites ldbestpractises),
standard vocabularies --such as SHACL-- should be reused as much as possible,
because this helps with the inclusion in the Web of data and these typically have better tool support.

Responses should be declared at a sufficient level of _expressivity_,
as long as clients are able to interpret them.
Chances of this are higher when standard vocabularies are used,
because of the better tool support.
Therefore, adoption rate is typically prioritized over expressivity.
SHACL for instance provides a higher level of expressivity than OWL,
while they are both standard vocabularies.

A response declaration can be defined in an expressive way,
but as long as clients are not able to _discover_ it,
it is of not much use.
Custom types are for example very easily discoverable.
More expressive response structures may be more complex and difficult to discover,
which is why a trade-off between those two criteria exists.

The _composability_ criterion is related to expressivity and discoverability.
If an approach allows very few and simple building blocks to be combined to reach a high level of expressivity,
clients require less hard-coded support for these building blocks, which benefits the discoverability.
Approaches that do not allow composability will require more of these building blocks to
achieve a high level of expressivity, which can negatively impact discoverability.
The composability of the approaches based on SHACL, SPIN and OWL
is for instance much higher than that of custom types,
because the latter have no standard building blocks.

When RDF-based tools are required for
handling the response declarations, _RDF complexity_ is important.
Nevertheless, even where non-RDF representations are used,
RDF-based tool processing could still be done by reifying to RDF in a postprocessing step.
SPIN and OWL are examples where responses can be expressed purely in RDF,
while SHACL-SPARQL encodes SPARQL queries as RDF literals.
The RDF complexity is related to the composability of an approach,
as small building blocks that are defined in granular RDF statements,
can potentially be reused as part of other more complex and possibly more expressive declarations.
A high level of RDF complexity can however negatively impact discoverability due to the higher required interpretation effort.

As mentioned before, choosing an appropriate approach depends on the situation.
For instance, if we require an approach that is based on standards,
is expressive, discoverable and is made up of easily composable building blocks,
then the SHACL shapes approach is best suited.
But if we require an approach that has a high level of RDF complexity and is sufficiently expressive,
then the SPIN-based approach could be sufficient.
Otherwise, if we value discoverability over adoptability, then custom types might be preferred.
