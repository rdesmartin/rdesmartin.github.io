---
tags:
  - research
  - verification
---
Equivalence Checking is used successfully in Hardware verification. 

There seem to be 2 tricks used in HW verification that could be of interest for NNV. 

# Equivalence between complex and simple model

Instead of proving functional correctness on a complex model, we prove that the real-world circuit's complex model is functionally equivalent to a smaller, simpler model.
For NN, the complex model would be the real-valued, original model, and the simpler model a compressed version, using pruning, or binarisation, or quantisation.

The NN equivalence (NNE) problem has been formalised by Teuber et al. (2021) and Eleftheriatis et al. (2022). 
Teuber use Geometric Path Enumeration and prove that the NNE problem is coNP-hard (by reducing the NNE problem to a reachability problem and re-using Katz's proof). Their tool NNEquiv compares favorably to 2 pre-existing techniques (Reludiff, MILPEquiv). They use Zonotopes : related to ERAN?
Question about experimental setup: they claim to have re-trained some ACAS-Xu models, but ACAS-Xu training data is not publically available, apparently taken from RELUDiff -> investigate. 

Eleftheriatis' contribution is to encode the NNE problem as an SMT formula, and use Z3 as a proof of concept. Their implementation works with toy networks, but does not scale to MNIST-sized networks. (Networks with 10 inputs, 1-2 10-note hidden layers, 2 outputs).

Problem with these approaches: same as proving reachability properties on NNs. Too complex to work with general-purpose SMT-solver, would need specific optimsations. Could the problem be expressed in a way that Marabou could have a go at it?

# Iterative equivalence checking / divide and conquer
## Iterativity

In hardware verification, usually the original model and the new model are only marginally different because we are trying to prove that a minor change did not break the circuit. We can exploit their structural similarity: by running random simulations, we can identify the corresponding parts of the 2 models that seem to behave similarly and focus on proving equivalence between those.

Transfering that idea to NNV asks the question: does it make sense to verify equivalence of parts of 2 networks (eg specific layers, a subnetwork)? Would it help to verify the global equivalence of two networks?
It could look like this: between an original network and a quantised network, try to prove layer by layer that the quantised version is equivalent to the original version. If it is not, increse the bit width until it is.

FANC: by the ERAN people, transfer of proofs, iterative verification : is the idea similar?
I remember reading about proof transfer in Marabou, same question. -> residula reasoning


## Residual reasoning

Abstraction-refinement uses an abstraction of the model we want to check (easier to verify if the properties hold on it or not). If the verification fails, we use the information to refine the abstraction, i.e. we use the result to reduce the search space.
Initial paper: Clarke et al. Counterexample-guided abstraction refinement for symbolic model checking (2002)

Used in NNV

Integrated in Marabou (Elboher et al. Neural Network Verification using Residual Reasoning)