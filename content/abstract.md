## Abstract
<!-- Context      -->
While humans browse the Web by following links,
<span class="rephrase">
hypermedia is the equivalent that machines use for browsing.
</span>
<span class="comment" data-author="RV">
Not entirely correct: the links on the human Web are also hypermedia.
</span>
While efforts such as Hydra semantically describe
the hypermedia controls on Web interfaces
to enable smarter interface-agnostic clients,
they are largely limited to the input parameters to interfaces,
and clients therefore do not know what response to expect from these interfaces.
<!-- Need         -->
In order to convey such expectations,
interfaces need to declaratively describe the response structure
of their parameterized hypermedia controls.
<!-- Task         -->
We therefore explored techniques to represent this parameterized response structure
in a generic but expressive way.
<!-- Object       -->
In this work, we discuss four different approaches for declaring a response structure,
and we compare them based on a simple model that we introduce.
<!-- Findings     -->
<!-- Conclusion   -->
Based on this model, we conclude that a SHACL shape-based approach
is the most <span class="comment" data-author="RV">word missing</span>
for declaring such a parameterized response structure,
as it conforms to the REST architectural style that has helped shape the Web into its current form.
<!-- Perspectives -->

<span id="keywords"><span class="title">Keywords</span> Linked Data, Hypermedia, REST, RDF, SHACL, Hydra</span>
