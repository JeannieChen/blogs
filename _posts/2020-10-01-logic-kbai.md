---
layout: post
title:  Logic in Knowledge-based Artifical Intelligence 
subtitle: Formal logic and the cognitive connection
tags: [kbai]
---

Logic is a language that allows us to make association of the world in a precise way. It also forms the basis of planning.

## Why do we need formal logic?
We need it for two reasons:
- Soundness: only valid conclusions can be proven
- Completeness: all valid conclusions can be proven

## Formal Notation
For example, if we want to put a sentence classifying birds into language of logic, we might say: _**If an animal has feathers, then it is a bird.**_ The sentences are language of logic.

### Predicates
**Predicate** is a function that maps object arguments to true or false values. 
i.e. _**Feathers(animal)**_, **":"** means indicates. 

``` If Feathers(animal): Then Bird(animal)```

### Conjunctions & Disjunctions

``` 
If Feathers(animal) && Files(animal): Then Bird(animal)
If Feathers(animal) || Files(animal): Then ...
If Feathers(animal) && !Files(animal): Then ...
```

### Implies
``` 
If Feathers(animal) || Files(animal) => Then ...
```

### Truth Table
| **A** | **B** | **A || B** |
| ----- | ----- | ---------- | 
| True  | True  | True       |
| True  | False | True       |
| False | True  | True       |
| False | False | False      |

## Properties of Truth Values
### Commutative Property
``` A && B = B && A ```
### Distributive Property
``` A && (B || C) = (A && B) || (A && C) ```
### Associative Property
``` A || (B || C) = (A || B) || C ```
``` A && (B && C) = (A && B) && C ```

The associative property applies when there is only conjunctions or disjunctions.
### De Morgan's Law
```!(A && B) = !A || !B```

### Truth of Implications
```Given A => B, we can rewrite it as !A || B```

## Rules of Inference
