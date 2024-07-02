---
season: winter
toc: true
tags:
  - imandra
  - marabou
  - research
---

Marabou called externally by Imadra as a module.

## Serialisation format
Marabou supports ONNX and Tensorflow protobufs.
ONNX: recommended by Andrew. Look at Python interface for example of external API calling Marabou's core.
IIRC Simon mentioned protobuf implementation in Imandra

## Proof production
Our main accomplishments are:
* Serialization of Marabou proofs and deserialization of them into Imandra; we chose the JSON format for readability, with the drawback of large proof files, up to several GB. Most of the proofs constitiutes of lemmas, which in our context mean proofs for intermediate bound-tightenings which cannot be proved with Farkas vectors. It is noteworthy that serialization is done with 8 decimal digits (as the Marabou standard percision), thought checking is done with infitie percision w.r.t to serialized proof. 
* implement a proof checker in Imandra which traverses the proof-tree.The proof tree constructed from two-typed nodes (nodes with head split, lemmas, children and leaves with head split, lemmas and a contradiction) - this allows implicit verification of a correct tree stucture. The proof checker is admitted in the Imandra's logic mode, which allows to formally verify its correctness.
* The proof checker may check two possible forms of lemmas (suppoerted by the de/serializer) - short lemmas which corresponds to mere data-updates, and full lemmas which contain all info. necessary for proving their correctness. These two forms enalbe two mode of proof checking, each prioritising perfromance over percision and vice versa.
* The implementation includes two seprate data structes for representing linear-algebraic structures (vectors and tableaus) - either efficient sparse iterative maps, or native lists. The former is more effiecient and is more likely to be used in practice; the latter is implemennted for verification purposes.
* We created a small benchmark of serialized JSON proofs with varied sizes. So far it seems the proof-checker does not scale enough to check ACAS-Xu queries (with full lemmas) and scale only to the smallest ACAS-Xu proofs in the short version. We believe this is caused by the infinte percision computation that Imandara uses, combined with the use of native-lists that don't supoort random access to its elemetns.

Looking forward, we would like to:
* Complete verification of the proof-checker's correctness, starting with the correctness of the leaves' contradictions.

