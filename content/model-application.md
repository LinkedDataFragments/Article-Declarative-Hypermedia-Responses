## Model Application
{:#model-application}

In this section, we propose a general suggestion for which approach to use for declaratively representing Web API responses.
Based on our model from [](#comparison-model), there are different ways for choosing between the discussed approaches from [](#approaches).
We order the model criteria by the following level of importance:

1. Adoption
2. Expressivity
3. Reification

We give the most importance to the possible adoption rate.
According to the [best practises for publishing Linked Data](cite:cites ldbestpractises),
standard vocabularies should be reused as much as possible,
because this helps with the inclusion in the Web of data.
Furthermore, multiple tools typically exist to work with these standard vocabularies.

Expressivity is the second most important in our list, right after adoption rate.
Responses should be declaratively definable,
as long as clients are able to interpret them.
Chances of this are higher when standard vocabularies are used,
because these tend to have support in multiple tools.

Finally, we consider level of reification as the least important criteria of the three.
That is because level of reification can be seen as a possible benefit, but not a requirement.
It is more important that tooling exists for interpreting the vocabulary,
and that this vocabulary is expressive enough,
than the importance of how easy it is to use this representation in RDF-based tools.
If RDF-based tool processing would be required, non-RDF representation could still
be reified to RDF in a client-side postprocessing step.

Based on this order of criteria, the SHACL shapes approach is most suited.
