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
**Rules of Inference** instantiates general rules to prove specific claims.

### Modus Ponens
```
Sentence 1: P => Q
Sentence 2: P
thus Sentence 3: Q
```

### Modus Tollens
```
Sentence 1: P => Q
Sentence 2: !Q
thus Sentence 3: !P
```
Those rules can be used for reasoning. For example, let's prove Harry is a bird using Moduc Ponens:
```
S1: Feathers(animal) => Bird(animal)
S2: Feathers(Harry)
S3: Bird(Harry)
```
Although the rules exist for a long time, it is hard to use these rules in AI agent because the computation is not feasible.

### Universal Quantifiers & Existential Quantifier
Propositional logic (zero-order logic) has key aspect that it does not have any variables, while existential and universal quantifier can be used with variables:
- **Universal Quantifier** means give all values for the variable (FOR ALL)
- **Existential Quantifier** means not true for all but is true for at least one (FOR AT LEAST ONE)

## Proof by Refutation (Resolution Theorem Proving)
Steps:
1. Convert every sentence into a conjunctive normal form.
2. RTP is proving by negation, hence we negate the last one
3. List down what agent saw
4. Find out negation of assumptions and cross them out
5. If it is not null after elimination, then it means agent cannot prove it is true.

## The Cognitive Connection 
Logic is a formal and precise way to reason. So far most of the reasoning methods the AI agent used are deductive, but human behaviors are more likely to be inductive. Human use logic sometimes, but it is not a fundamental method.


