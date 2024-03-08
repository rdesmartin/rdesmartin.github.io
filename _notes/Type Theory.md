---
---



# Day 2
Operations on Types/Sets
```Agda
A, B: Set

A -> B : Set
A x B: Set  -- product
A + B: Set  -- labelled sum
			-- symbol is disjoint union or coproduct
```

# Day 3
### Natural numbers

Nat:
```Agda
data nat: Set where
	zero: nat
	suc: nat -> nat
```

Annductive type is defined by its constructors

```Agda
pred: nat -> Maybe nat
pred zero = nothing
pred (suc n) = just n

zerosuc: Maybe nat -> nat
zerosuc nothing = zero
zerosuc (just n) = n
```


### Conatural numbers
A coinductive type is defined by the destructors
Structural greater is a criteria for inductive type
For coinductive type a criteria is productivity: e.g. (`predinf inf` will always be productive, the result will never be `nothing`)

```Agda
record natinf : Set where
	coinducuctive
	field
		predinf : Maybe ninf

zeroinf : natinf
predinf zeroinf = nothing

sucinf : natinf -> natinf
predinf (sucinf x) = just x

-- we can define conatural numbers that are not natural numbers
inf : natinf
predinf inf = just inf


_+inf_ : natinf -> natinf -> natinf
predinf (m +inf n) with predinf m
... | nothing = predinf n
... | just m' = just (m' +inf n)
```
