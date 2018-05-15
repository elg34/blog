+++
title=  "Mathematical Foundations - Exercises"
tags= ["maths","foundations","logic","exercises"]
categories= ["exercises"]
draft= true
+++
1. TOC
{:toc}

## Mathematical reasoning



{% box example %}
**Exercise.** Come up with more examples of axioms of the first and second kind!
{% endbox %}

## Propositional logic

{% box example %}
**Exercise.** Prove the following propositions from the section on propositional calculus using truth tables. Try to understand the meaning of their names and learn them by heart.

(a) Prove for all propositions $$A$$, $$B$$ and $$C$$:
* *Tertium non datur:* $$A \lor \neg A$$
* *Double negation:* $$A \iff \neg(\neg A)$$
* *Contraposition:* $$(A\implies B) \iff (\neg B \implies \neg A)$$
* *Chain inference:*
  $$(A\iff B \iff C) \iff \left( (A\implies B) \land (B\implies C) \land (C\implies A) \right)$$

(b) Prove for all propositions $$A$$, $$B$$ and $$C$$:
* *Idempotence:* $$A \iff (A\lor A)$$
* *Commutativity:* $$(A\lor B) \iff (B \lor A)$$
* *Associativity:* $$(A\lor B)\lor C \iff A \lor (B\lor C)$$
* *de Morgan's Rules:* $$\neg(A\land B) \iff (\neg A \lor \neg B)$$
* *Distributivity:* $$A\land (B\lor C) \iff (A\land B)\lor (B\land C)$$
* Also prove the result of simultaneously exchanging $$\land$$ and $$\lor$$ in all of the above!

{% endbox %}

{% box example %}
**Exercise.** Either prove that the following theorems hold for all propositions $$A$$ and $$B$$ or give a counterexample.

* $$A\land\neg A$$,
* $$(A\land\neg A)\implies B$$,
* $$(A\land B) \implies (A \lor B) $$,
* $$(A\land B)\iff \neg(A\implies\neg B)$$,
* $$(A\implies\neg B)\iff \neg(A\implies B)$$,
* $$(A\implies B) \lor (B\implies A)$$,
* $$[(A\land B)\lor (B\implies A)]\iff (B\implies A)$$.

{% endbox %}

{% box example %}
**Exercise.** Which of the following propositions are equivalent?

* $$A\lor \neg B$$,
* $$A\land\neg A$$,
* $$(A\land(B\lor C))\land \neg (B\land C)$$,
* $$A\land B$$,
* $$\neg A \iff B$$,
* $$\neg(\neg A \land B)$$,
* $$(B\implies\neg A)\land(A\implies B)$$,
* $$A \lor \neg B \lor \neg(B\implies A)$$.

{% endbox %}

{% box example %}
**Exercise. (Lost in Translation)** 

(a) Translate the following propositions to natural language, where the atomic propositions are given by $$J$$: *You are Kathryn Janeway*, $$H$$: *You are the Holodoc*, $$C$$: *You are a Captain*, $$V$$: *You are in the Voyager's crew* and $$B$$: *We are the Borg*, $$R$$: *Resistance is futile*.

* $$B\land R$$,
* $$J\implies V$$,
* $$J\iff V\land C$$,
* $$(J\lor H)\implies V$$,
* $$(J\lor H)\land\neg(J\land H)$$,
* $$(B\land J)\implies \neg R$$,

(b) Translate the following statements into formal propositions. Choose appropriate atomic propositions for this purpose!

* *Babel fish exist*,
* *You don't have a Babel fish in your ear unless they exist.*,
* *You understand all languages in the universe if and only if you have a Babel fish in your ear*,
* *If you are human, then you have been captured by Vogons and escaped them if and only if you are Arthur Dent*,
* *If you are neither human nor an alien organism but live aboard the Heart of Gold, then not being Eddie implies that you are not only Marvin but also depressed*.

{% endbox %}

{% box example %}
**Exercise. (The Principle of Explosion)** Assume that you have somehow derived a contradiction $$A\land\neg A$$. Derive the truth of any other proposition $$B$$ from it!
{% endbox %}

{% box example %}
**Exercise. (Independent Connectives)**

(a) How many possible connectives of two propositions $$A$$ and $$B$$, i.e. assignments of truth values depending on $$A$$ and $$B$$, are there?

(b) Prove that all possible connectives of two propositions can be expressed using only negation and implication!
{% endbox %}

## Predicate logic


{% box example %}
**Exercise. (Lost in Translation II)**

(a) Translate the following propositions to natural language, where the universe of discourse is given by computer games and the predicates are $$\operatorname{Valve}(x):$$ *$$x$$ is a game by Valve*, $$\operatorname{Steam}(x):$$ *$$x$$ is published on Steam*, $$\operatorname{Cheap}(x):$$ *$$x$$ is a cheap game*, $$x>y:$$ *$$x$$ is a better game than $$y$$*.

* $$\forall x: \operatorname{Valve}(x)\implies \operatorname{Steam}(x)$$,
* $$\forall x: \exists y: y>x$$,
* $$\exists y: \forall x: y>x$$,
* $$\forall x: (\operatorname{Valve(x)}\implies (\text{Portal2}>x \lor \text{Portal2}=x))$$,
* $$\forall x,y,z: (x>y \land y>z \implies x>z)$$,
* $$\forall x: (\operatorname{Cheap}(x)\implies\exists y: (\neg \operatorname{Cheap}(y) \land x>y))$$.

(b) Translate the following statements into formal propositions. Choose appropriate universes and predicates for this purpose!

* *All humans are mortal and Aristotle is human. Therefore, Aristotle is mortal* (Note that all of Aristotle's classical *syllogisms* can be expressed in predicate calculus!)
* *For all numbers, there exists a natural number that is greater than it* (the 'Archimedean property')
* *There exists precisely one Person with the surname 'Shakespeare' who wrote the famed play 'Hamlet'*
* *No one else was in the room where it happened*
* *There is no number so that every other number is smaller than it*
* *In every election, there is a candidate that performs better than any other candidate*
* *There is a candidate, that performs better than any other candidate in any election*


{% endbox %}

{% box example %}
**Exercise. (Swapping quantifiers)** Come up with formal examples of propositions containing two quantifiers together with true real-word interpretations where the order of quantifiers cannot be changed without invalidating the proposition!
{% endbox %}

{% box example %}
**Exercise. (Epimenides paradox)** You might have heard of a variation of the following: *The Cretan Epimenides said: "All Cretans are liars."*

Translate this to predicate logic and decide whether it really is a paradox!
{% endbox %}


{::comment}
## Set theory

{% box example %}
**Exercise. (Simple propositions of pure set theory)** de Morgan's rules for sets could be derived by exploiting a correspondence between logical connectives and set operations.

* Find more propositions from propositional calculus and turn them into propositions of set theory!
* Also prove these propositions using Venn diagrams!
* What logical connective corresponds to the disjoint union?

{% endbox %}

{% box example %}
**Exercise. (Venn Diagrams)** We saw the following constructions for ...:

* Our construction for four sets looks different from that for three and two sets. Whats wrong with the more natural :


* How many different regions does a Venn Diagram of $$N$$ sets have to have at least?

{% endbox %}

{% box example %}
**Exercise. (Relations)** Come up with more examples of relations from everyday life! Also find two different relations that have the same graph.
{% endbox %}

{% box example %}
**Exercise. (Relations)** Come up with more examples of relations from everyday life! Also find two different relations that have the same graph.
{% endbox %}

{% box example %}
**Exercise. (Equivalence relations)** 
{% endbox %}


## Numbers

## Ordered sets

## Categories


{:/comment}
