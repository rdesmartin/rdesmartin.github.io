---
tags:
  - research
  - verification
  - itp
  - imandra
---

Working notes for implementing and verifying a piece of software in Imandra (e.g. [[Marabou-Imandra interfacing]]).

# Syntax
Constructor with multiple parameters: the parameters are a tuple, so to call the constructor we need to put the parameters in a tuple with parenthesis. 

```ocaml
type t = | Foo of int * int | Bar

let x : t = Foo (1, 2) (* Correct *)

let y : t = Foo 1 2 (* Wrong *)
```

If the wrong syntax is used within parenthesis, the parser will throw an error about a missing parenthis.

# Interactive Proof Interface

Use `[@@disable]` to tell Imandra to not try recursion on the functions that don't make sense.

Instead of  immediatly applying admitted lemmas as rewrite rules (using `[@@rewrite]`), first try to apply them explicitly: for a lemma `lemma foo x y = ...`, use `[@@apply foo a b]` where a and b are variables used in the current verification goal.

# Proving program termination
To specify which set of variable to use as a decreasing measure to prove program termination, use the `[@@adm]` annotation:
```ocaml
let rec ack m n =
  if m <= 0 then n + 1
  else if n <= 0 then ack (m-1) 1
  else ack (m-1) (ack m (n-1))
  [@@adm m,n]
```
