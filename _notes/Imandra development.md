---
---

Notes for problems encountered and general tips for development using Imandra.

# Syntax
Constructor with multiple parameters: the parameters are a tuple, so to call the constructor we need to put the parameters in a tuple with parenthesis. 

```ocaml
type t = | Foo of int * int | Bar

let x : t = Foo (1, 2) (* Correct *)

let y : t = Foo 1 2 (* Wrong *)
```

If the wrong syntax is used within parenthesis, the parser will throw an error about a missing parenthis:

