---
season: winter
tags: imandra, ocaml
---

Once we verified our code with Imandra, we want to extract it to OCaml so that it is compiled with optimisation and runs faster. Note that the extracted OCaml code uses arbitrary precision integers, it retains exactly the same semantics as Imandra's language.

For extracting OCaml code, we can use `imandra-extract file_name.iml > file_name.ml` on each file, but for multi-file development it is easier to set up a dune project.

# Dune project setup
Directory structure:
```
project-root
|-- dune-project
|-- src/
	|-- lib1/
		|-- dune
		|-- lib1.iml
	|-- lib2/
		|-- dune
		|-- lib2.iml
	|-- executable/
		|-- dune
		|-- main.iml
```

cf. [FIX engine repo](https://github.com/imandra-ai/fix-engine/)

Content of `dune-project`:

```lisp
(lang dune 2.2)
(name imandra-marabou-proof-checker)

  
(dialect
	(name imandra)
	(implementation
		(extension iml)
		(preprocess (system "imandra-extract %{input-file}"))
	(format (system "ocamlformat %{input-file}")))
	(interface (extension "imli")))
```

We use a [`dialect` stanza](https://dune.readthedocs.io/en/stable/dune-files.html#dialect) to apply `imandra-extract` to all iml files.

Example content of a `dune` file for an executable:

```lisp
(executable
	(name main)
	(flags :standard -open Imandra_prelude -warn-error -A+8+39 -w -33-58)
	(libraries decoders-yojson decoders yojson imandra-prelude))
```


# Relative Imports
