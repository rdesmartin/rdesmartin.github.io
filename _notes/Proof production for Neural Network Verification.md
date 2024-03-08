---
season: winter
tags: nnv proof-checking
---

## Motivation

NNV tools are designed to formally verify properties on NNs. As software, they may present defaults (implementation errors, floating-point errors). We would like assurance that their verification is correct, which proof production can do.

The following scenarios show when proof production can be desirable:
* NN competition: if all participants do not agree on the outcome of a verification task, how can we determine who is right? For SMT solving competitions, we usually knew the expected result. For NNV, we don't (that's sort of the main characteristic of NNV: difficult to reason about.)
* Integrate NNV in a larger verification framework. NN are usually part of larger systems that need to be verified too (ex: NN controller in an autonomous plane control system). These larger verification shouldn't accept the NNV tool's result blindly (is there an example of this being used in a different case?).

Normal case: for a network $N: I \rightarrow O$ and a property $\phi$, we want to prove that $\forall x \in I', \phi(N,x)$ holds. A NNV program $P$ is given $N$, $x$ and $I'$ as input and is expected to return $True$ if the property is holds or $False$ if it doesn't. In the case of an incomplete verifier, it can also output $Unknown$. Some provers, like SMT-based ones give a counter-example $\hat{x}$ when  the output is $False$.

If the output is $False$ and a counterexample is provided, it is easy to verify the result's correctness by computing $\phi(N,\hat{x})$.

Proof production consists of generating some artifact during the verification process. This proof artifact can be replayed by a verified external program (proof checker). If the proof artifact has an error, the proof checker detects it and invalidates the proof. Otherwise, the proof is validated.  

## Interactive theorem provers and constructive proofs

Constructive proofs are proofs that hold under [[Constructive mathematics]], which is more restrictive than classical logic.
Some theorem provers such as Coq and Agda use constructive logic. If we want to interface one of them with an external tool, the latter must provide a constructive proof for its result to be accepted by the constructive prover.
Other theorem provers like Isabelle/HOL use classical logic and have valid results.

## Proof production in SMT solvers

SMT solvers, or SMT-solving inspired custom algorithms like Reluplex, are used for NNV. They have the benefit of providing a counter-example for negative results. Providing a checkable proof for a positive result is more challenging.

### SMT-ITP integrations

Several interactive theorem provers have integrated SMT solvers; studying how these SMT/ITP interfaces have been developed can be interesting for interfacing SMT-based NNV tools and 

CoqSMT:
* how does CoqSMT connect SMT solver and 
Sledgehammer Isabelle/HOL

### Proof production

CVC4