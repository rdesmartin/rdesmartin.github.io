---
---

Working notes when verifying the correctness of the Marabou verification proofs as explained in [[Marabou-Imandra interfacing]].

Use `[@@disable]` to tell Imandra to not try recursion on the functions that don't make sense.

Instead of  immediatly applying admitted lemmas as rewrite rules (using `[@@rewrite]`), first try to apply them explicitly: for a lemma `lemma foo x y = ...`, use `[@@apply foo a b]` where a and b are variables used in the current verification goal.
