## Model for Comparison
{:#comparison-model}

In this section, we introduce a simple model for comparing approaches for declaratively representing Web API responses.
Our model consists of different criteria: _reification_, _expressivity_ and _adoption_.
<span class="comment" data-author="RV">How are these criteria? This is not obvious for the first one.</span>
These will be explained hereafter.
Each response representation approach can receive a qualitative score for each of these criteria.
A suitable approach can then be chosen based on the composite score across these criteria,
which can possibly be weighted depending on the relative importance of these criteria in the use case.

<span class="comment" data-author="RV">I've got more criteria: <em>composability</em> and <em>extensibility</em>. Do you think these are already covered? If we consider APIs as consisting of <a href="https://arxiv.org/pdf/1609.07108v2.pdf">features</a>, then we need to ensure that hypermedia controls are composable. Maybe this is the case for hypermedia controls in general, although I wonder whether types would have any limitation regarding composability. For sure, types have a major problem with composability, as they are only one-directional.</span>

<span class="comment" data-author="RV">Also, easy of <em>discovery</em> should be tackled! This can be a part of expressivity, but on second thoughts, maybe not, since both are not necessarily opposites. Custom types are really easy to discover, so this should definitely be visible in a comparison table. See also my comment in the conclusion.</span>

### Reification

The level of reification, i.e., how 'deep' the response structure is represented in RDF,
<span class="comment" data-author="RV">Mmm, I think we need a new term. Maybe something like <q>nesting</q> or <q>abstraction level</q>. <q>Reification (level)</q> is weird to have as a criterion, the term will be understood differently.</span>
has an influence on how easy such a representation can be used by RDF-based tools.

A SPARQL query could for example be represented as an RDF string literal,
or fully reified using the SPIN vocabulary.
<span class="comment" data-author="RV">This thinking is good!</span>
Both approaches have the same meaning, but the former representation is simpler,
<span class="comment" data-author="RV">try arguing <q>simpler</q> better, perhaps using a more precise term</span>
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
<span class="comment" data-author="RV">This is tricky. Self-descriptiveness is a relative notion; it all depends on the primitives you agree on. These can be narrow or broad.</span>
<span class="comment" data-author="RV">Let's actually have <q>Self-descriptiveness is a relative notion</q> in this article, together with the corresponding argument, I don't have that quote citable yet anywhere.</span>
If a server exposes certain functionality,
clients should be able to interpret and make use of this functionality without requiring explicit implementation of it.
Therefore, the approach should be as expressive as possible.

Higher expressivity does however typically lead to higher complexity for client-side parsing and usage,
but also for server-side declaration generation if this would happen dynamically at runtime.
Expressivity and simplicity of usage are contradicting criteria, so a trade-off between these two must be sought out.
The Assembly language is for example very expressive, but its low level of abstraction would make it complex to use.
<span class="comment" data-author="RV">I follow the line of that last argument, but it should be played out more precisely.</span>

### Adoption

While different approaches for Web API response types exist,
the used technologies behind these approaches will have an impact on the adoption rate.
The usage of a new, unknown and non-standard vocabulary will most likely lead to a lower adoption rate
than the usage of vocabulary that is recommended by W3C.
