---
title: 'Formal Monotony Analysis of~Neural Networks with~Mixed Inputs: An Asset for~Certification'
shorttitle: Formal {{Monotony Analysis}} of~{{Neural Networks}} with~{{Mixed Inputs}}
booktitle: Formal {{Methods}} for {{Industrial Critical Systems}}
editor: Groote, Jan Friso and Huisman, Marieke
year: 2022
series: Lecture {{Notes}} in {{Computer Science}}
pages: 15-31
publisher: "{Springer International Publishing}"
address: "{Cham}"
doi: 10.1007/978-3-031-15008-1_3
abstract: 'The use of ML technology to design safety-critical systems requires a complete
  understanding of the neural network''s properties. Among the relevant properties
  in an industrial context, the verification of partial monotony may become mandatory.
  This paper proposes a method to evaluate the monotony property using a Mixed Integer
  Linear Programming (MILP) solver. Contrary to the existing literature, this monotony
  analysis provides a lower and upper bound of the space volume where the property
  does not hold, that we denote ``Non-Monotonic Space Coverage''''. This work has
  several advantages: (i) our formulation of the monotony property works on discrete
  inputs, (ii) the iterative nature of our algorithm allows for refining the analysis
  as needed, and (iii) from an industrial point of view, the results of this evaluation
  are valuable to the aeronautical domain where it can support the certification demonstration.
  We applied this method to an avionic case study (braking distance estimation using
  a neural network) where the verification of the monotony property is of paramount
  interest from a safety perspective.'
isbn: 978-3-031-15008-1
langid: english
keywords: Certification,Formal Methods,Monotony,Neural network verification
file: "/home/remi/Zotero/storage/D9CIKDLQ/Vidot et al. - 2022 - Formal Monotony Analysis
  of Neural Networks with M.pdf"
authors:
- Guillaume Vidot
- Mélanie Ducoffe
- Christophe Gabreau
- Ileana Ober
- Iulian Ober
layout: paper
read: false
readings: []
added: 2023-04-28
---

This paper proves monotony property of Neural networks that model a physical system (breaks in an airplane), where monotony is a physical property of the approximated model that we want the NN to have.

> Today, state-of-the-art methods for enforcing partial monotony
No citation here, what are they refering to? De Maria et al?

They propose a refinement of the monotony property: it has to be monotonous only in the desired area -> moving the burden of verification from the verifier to the specification

Related works discussion: Some methods merely encourage monotony without enforcing it.
Some methods enforce it for continuous variables
Others use hand-designed structures that enforce monotony but make training harder
Urban, C., Christakis, M., W ̈ ustholz, V., Zhang, F.: Perfectly parallel fairness certification of neural networks, considers monotony for discrete input spaces

The goal is not to prove monotonicity glabally but identify regions for which monotonicity holds and those which don't.
Could this be translated to a structural property, i.e. quantified on networks?