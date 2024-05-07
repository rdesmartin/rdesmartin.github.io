Spinoza's *Ethics* is an important work from 17th c. philosopher Baruch Spinoza. In it, Spinoza presents his philosophical system in an axiomatic way, in the manner of Euclid's geometry. It resembles a logical theory. As in all logical theories, we expect that, all the system composed of  these axioms and the rules of inference should be *sound*, meaning that all provable propositions are true, or alternatively, it is not possible to prove propositions that are false. 

If it is relatively straightforward to try to prove soundness of a formally defined theory, Spinoza's ethics is *not* such a formally defined work. In fact, Spinoza explicitly writes it: the only mention he makes of it in *Ethics* is to say that it is not relevant to his work[^1]. Since he does not give formal definitions of the connectives he considers, there are debates on the exact meaning of some the notions Spinoza uses (e.g. "attribute", "necessity").

Nonetheless, Charles Jarrett has formalised Spinoza's *Ethics* as a quantified, modal logic (i.e. a logic that includes two modalities: necessity, and contingency). He discovered that there are some axioms that are necessary for Spinoza's theory to be sound, that Spinoza doesn't make explicit. In other cases, Spinoza's lack of formal definitions causes logical unsoundness, for instance with the Ontological argument, a classical way of proving God's existence.

Theorem provers are software that are able to formalise mathematical statements and prove that they are theorems. Using them to formalise philosophical reasonments is not a new thing: Proof of Godel's ontological argument in 197... and in Coq in 20..

From this lengthy introduction, I can finally state the goal of this project: to formalise Spinoza's *Ethics* -- or precisely, Jarrett's formalisation -- in the Coq theorem prover. After all I said about the (expected) unsoundness of Spinoza's system, you can yourself why even do it? One pragmatic reason is intellectual curiosity, and a way to become more familiar with Coq. But in addition, the expectation when starting a formalisation entreprise is to discover a flaw in the unverified system; this is my hope here too. Finally, I also hope that once I have the unsound, formally stated system, I might be able to experiment with adding axioms and see if it changes the soundness, or if it allows to prove more propositions.

This is a very ambitious side project, because I know little about the *Ethics* or modal logic to begin with, but even if it doesn't yield any tangible result, I enjoy reading about Spinoza's philosophy and the debates on the Ontological proof so it is worth spending time to me. 

My plan to tackle it is, in order:
* Get a better understanding of Spinoza's work:
	* Read the overview of Spinoza's ethics by Jarrett
	* Maybe a Very Short Introduction or something similar
* Familiarise myself with the modal logic in Coq:
	* Refresher on modal logic
	* Read paper
	* Read up on Godel's ontological proof
	* Re-run the paper's proof of Godel's ontological proof
* Read Jarrett's formalisation of *Ethics* (focusing on the Ontological proof)
* Implement Jarrett's logic in Coq
* Formalise Spinoza's ontological proof in Coq
	* Try to arrive to Jarrett's 2 formulations of the ontological proof
* Formalise the rest of *Ethics*.

I hope to update this article with more details soon. If you know of any similar attempts, or any resources that might prove helpful for this project, please contact me!

[^1] [[mason-spinoza-on-modality]]
> Spinoza had almost no direct in logic, and still less in anything resembling modal logic. His only reference to logic in the Ethics (V Pref) was to say in passing that it was not relevant to his concerns.

