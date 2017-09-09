## Abstract
<!-- Context      -->
<del class="comment">The Web is the main driver of the exchange of information.</del>
While humans browse the Web by following links,
hypermedia is <span class="grammar">the equivalent that machines for browsing.</span>
While efforts such as Hydra exist for semantically describing hypermedia controls,
they are limited to describing the input parameters to interfaces.
<!-- Need         -->
<span class="grammar">
In order to make it possible for clients to autonomously detect what responses certain interfaces
can return based on certain parameters.
</span>
These interfaces need to declaratively define what the response structure
for certain controls is in terms of certain parameters.
<span class="comment" data-author="RV">I think we need to nail the need more precisely and clearly. It's too obfuscated now. Consider direct language like: machines know what parameters to send, but not what response to expect.</span>
<!-- Task         -->
For this, a vocabulary is needed to represent this parameterized response structure
in a generic, but expressive way.
<!-- Object       -->
In this work, we discuss three different approaches for declaring such response structure,
and we compare them based on a simple model that we introduce.
<!-- Findings     -->
<!-- Conclusion   -->
Based on this model, we conclude that a SHACL shape-based approach
is sufficient for declaring such a parameterized response structure.
<!-- Perspectives -->

<span id="keywords"><span class="title">Keywords:</span> Linked Data, Hypermedia, RDF, SHACL, Hydra</span>
