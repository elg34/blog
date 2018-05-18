+++
title=  "Mathematical Foundations: Logic"
tags= ["maths","foundations","logic"]
date= "2018-05-15T12:44:40+02:00"
+++

<!--figure class="figright" style="width:70%">
<img src="/images/posts/principia-proof.png"/>
<figcaption>Taken from Russell and Whitehead's <i>Principia Mathematica</i> <a href="https://en.wikipedia.org/wiki/File:Principia_Mathematica_54-43.png">(source)</a>, which famously arrives at this result only after hundreds of pages. Note that this doesn't really mean that without such reasoning you don't understand why 1+1 equals two - clearly, if that statement was not true within PM you would rightfully doubt its formal system long before thinking something was off about your intuition of natural numbers.</figcaption>
</figure>-->

As the formalised study of arguments, logic forms the backbone of modern mathematics. It is tempting to think of it as entirely objective, divorced from human thought processes, and one might believe that there exists one "true" logic. It is unclear, however, how we could hope to access that with our evolved biological brains. Instead, we content ourselves with using natural language to agree on a way to represent the essence of verbal arguments as formal symbolic expressions together with rules to manipulate them. This abandons uniqueness in favor of axiomatizations differing not in correctness but in terms of self-consistency, the features they offer for formulating arguments and the complexity they introduce.

<!--more-->

In this chapter we will start with a few more remarks on mathematical reasoning and terminology and then go through the two most important logical frameworks for practical use: **Propositional logic**, which only deals with simple logical connectives such as AND/ORs, and **predicate logic**, which builds on this by adding propositions whose truth value can depend on variables in a domain of discourse. As it turns out, we then have to discuss some nuances to make sure to not introduce paradoxa. Finally, we'll have a short outlook on systems of logic with more features.

## On mathematical proof
A central tenet of modern mathematics, at least in academia, is that every statement must be rigorously proven to be true by combining definitions, axioms and previously proven statements according to logical inference rules. This (to varying degrees) makes the use of **formal languages**, which constitute a way of communicating using a strict, usually symbolic grammar. Since this short introduction is meant only to prepare us for practical mathematical reasoning and give us an overview of the subject, we will not be very careful about distinguishing between the formal language and its philosophical interpretation and also not express the inference rules formally.

Let's start with our first definition:

{{< box definition >}}
The word **axiom** refers to an *unproven assumption of an argument* and is often used in two (related) ways in mathematics: It can mean that the axiom is just something you need to convince yourself to hold true if you want to apply the argument in a specific situation - for example, you might assume that $x$ is a positive number. This does not mean that you neglected to prove a part of your statement, just that you should not think of using it when, say, $$x=-4$$. Such assumptions are often bundled together by assigning useful names to mathematical objects that fulfill them, so that the properties that make up definitions are also called axioms. For example, the logical statements that have to hold for us to call something a *group* later on will often be referred to as *the group axioms*.

On the other hand an axiom can also be an assumption that is so fundamental to the language or system of logic you are working in that it can't possibly be proven - at most, it can be rooted in our intuition or argued for in natural language. For example, it is impossible to prove that every sensible statement you can make about the world must be either true or false. This fact is deeply intertwined with our thinking and instead of being an absolute truth, it reflects how we choose to try make sense of the world.
{{< /box >}}

This leads us to a common misconception about proofs themselves:

{{< box note "Tangent" >}}
Ultimately, there never is an entirely objective and infallible arbiter of what constitutes a valid proof. We accept a proof as valid if someone managed to somehow convince the rest of the mathematical profession that it is watertight, and that is *all there is to it*.

The fact is that all expressions of ideas are based - first and foremost - in not always reliable natural language. When we introduce formal systems, they can be great tools to keep ourselves from making mistakes and clarify our communication. But they cannot be used to justify absolute truth beyond normal spoken arguments because _formal languages themselves are justified **only** through natural language, intuition and the empirical fact that they seem to be useful tools!_ While computers that check formal languages can certainly help us find errors in our arguments and sometimes even generate proofs themselves, they cannot magically lift formal languages to a higher metaphysical realm of ultimate truth.

This is all largely irrelevant for a practical understanding of mathematics, but it can be tempting to just assume that there must be somebody who figured out all these foundational absolute truths. This is not the case!
{{< /box >}}

It is a common occurence in the history of mathematics that people started out using the word *axiom* in the second sense only to later shift to using it in the first: Once you start thinking about more general objects and situations that do not fulfill the property that is supposedly fundamental to our thinking, it becomes obvious that it was just a property that limits the situations to which we can apply the findings we derive from it.

{{< box example >}}
A prime example for this is the parallel postulate from Euclid's *Elements*, his famous axiomatic treatment of what we now know as Euclidean Geometry. It states that, given a line and a point, there is exactly one line parallel to the first which passes through the point. This was originally seen as a statement that must be necessarily true if we want our language to correspond to our intuitive way of thinking about geometry. Because it didn't feel "obviously true" enough for him, Euclid and many of his successors tried (and failed) to derive it as a consequence of his other, more elementary axioms. Today it has an entirely different standing: It serves only to *define* Euclidean Geometry and as such got demoted from the second kind of axiom to the first. The reason for this is that we can also do geometry on curved spaces such as the surface of a sphere, where those circles that split the sphere into two equal parts are considered "straight" lines. This non-Euclidean geometry fulfills all Euclidean axioms except the parallel postulate, proving all attempts to derive the parallel postulate from them doomed from the beginning.
{{< /box >}}

Don't get me wrong, I'm not saying *all* axioms will eventually turn out to be of the first kind - somewhere in our arguments we will always have to assume the validity of some basic patterns of thought.

Let's move on to more practical and less nuanced terminology:

{{< box definition >}}
A statement in a given system of logic is a **proposition**, a linguistic construct that is formed according to the syntax of a (not necessarily formal) language and interpreted to be either true or false. In common mathematical parlance, there are some more specialized terms that shed light on the relationship between different propositions in a given text:

* A **theorem** is considered of particular importance by the author
* A **lemma** is a small auxiliary proposition used only to prove a more general result (although sometimes they later get recognized as important in their own right while still retaining their historical designation, such as *Zorn's Lemma*)
* A **corollary** is an interesting result that effortlessly follows from a general theorem

All these terms are entirely subjective, of course, but nonetheless useful for effective communication.
{{< /box >}}

## Propositional logic
Within this system of logic, which has been around since at least greek antiquity, we do not care about the interpretation of propositions or how they might be related to the real world - we leave that entirely to natural language. Instead we start with **atomic propositions**, which are just propositions standing in for a specific true or false statements that we know how to interpret, and consider the construction of compound propositions using **logical connectives**. The simplest example of these is the **negation** $\neg A$, which we define as a new proposition that carries exactly the opposite truth value of a given proposition $A$.

{{< box example >}}
Let the symbol $R$ stand for the atomic proposition that *"it rained on tuesday"*; then $\neg R$ is a compound composition that means that *"it did not rain on tuesday"*.
{{< /box >}}

More complex connectives can be defined in a **truth table**, which goes through every true/false combination of two propositions $A$ and $B$:

<figure class="figmiddle" markdown="1">

|  $A$  |  $B$  | $A \land B$ | $A \lor B$ | $A \iff B$ | $A \implies B$ |
|:---:|:---:|:-----:|:-----:|:-----:|:-----:|
|  true  |  true  |   true   |   true   |   true   |   true   |
|  true  |  false  |   false   |   true   |   false   |   false   |
|  false  |  true  |   false   |   true   |   false   |   true   |
|  false  |  false  |   false   |   false   |   true   |   true   |

</figure>

The columns respectively define the logical **conjunction** ("and"), **disjunction** ("or"), **biconditional** ("is equivalent to" or "is true if and only if") and **implication** (the weakest connective whose truth guarantees that if $A$, then also $B$). Note that $A\implies B$ can be read as "A is a sufficient condition for B" or "B is a necessary condition for A".

{{< box example >}}
Given the propositions $R:$ *"its raining"*, $C:$ *"its cloudy"* and $S:$ *"the sky is clear"*, we can construct:

* $C\lor S$: *"the sky is either cloudy or clear"*
* $R\land C$: *"its cloudy and raining"*
* $R\implies C$: *"if it's raining, then it must be cloudy"*
* $S\implies \neg R$: *"if the sky is clear, then it cannot be raining"*

Some of these propositions can be considered to be always true, some only for certain truth values of $R, C$ and $S$, i.e. under certain circumstances. We could also build propositions that are clearly false: $C\land S$.
{{< /box >}}

Any further proposition that we can build from only $A$ and $B$ can be expressed with only the connectives we already defined, using parentheses as usual to specify the order of operations. Indeed, we could even limit ourselves to negation and implication as primitive symbols! This proposition can simply be proven by extensively writing down all possible assignments of true and false in a truth table and finding explicit expressions. As an example, we can introduce the **exclusive or** $A \veebar B :\iff \neg(A\iff B)$, which can be read as "either A or B, but not both". The colon in front of the equivalence symbol is used to indicate that we are defining the left-hand side of this formula via the right-hand side.

In pure propositional logic, the essential tool for proving or disproving theorems, i.e. logical inference, is just writing down the truth table and mechanically checking whether a given statement is true in every row. Using this *decision procedure* is what allows us to comfortably get around formulating all inference rules here. As an exercise, you could use it to prove the following statements:


{% refbox onuliks %}

{% refbox nourssa %}

## Predicate logic
The scope of propositional logic is limited since it only acts on the level of whole propositions. Predicate logic is a more powerful type of framework that includes the notion of objects within a given **universe of discourse**. This allows us to formulate so-called **predicates**, which are just propositions $A(x)$ whose truth value depends on which object the variable $x$ represents. Predicates can also have more than one object as argument, an example being the equality of two objects itself.

{{< box example >}}
In the universe of discourse of all numbers and animals, we could define the following predicates:

* BigNumber(x) :⇔ x is a number and larger than 10,
* IsFish(x) :⇔ x is a fish,
* Animal(x) :⇔ x is an animal,
* HasScales(x) :⇔ x is a fish and has scales,
* First(x,y) :⇔ x and y are numbers with the same most significant digit.

Here, BigNumber(16.7), IsFish(Carp) and First(19, 0.13) would evaluate to true while HasScales(42) and IsFish(Hamster) would be false propositions.
{{< /box >}}

Until now, we can only turn a predicate $A(x)$ into a proposition by inserting a specific object for $x$. In order to represent more of the arguments that appear in natural language, we introduce **quantifiers**:

{{< box definition >}}

* The **universal quantifier $\forall x$** can be read as "for all $x$, ..." and 
* the **existential quantifier $\exists x$** can be read as "there exists an $x$ such that...",
* the **unique existential quantifier $\exists !$** can be read as "there exists exactly one $x$ such that...",
* the **negated existential quantifier $\not\exists$** can be read as "there exists no $x$ such that...".
{{< /box >}}

Not all of these are independent. Starting with the universal quantifier, for example, we can express the other quantifiers through it:

* $\exists x: A(x)$ can be defined as $ \neg(\forall x: \neg A(x)),$
* $\exists ! x: A(x)$ can be defined as $\exists x: \left(A(x) \land \forall y: (A(y)\implies x=y)\right)$ and
* $\not\exists x: A(x)$ can be defined as $\neg (\exists x: A(x))$.

Convince yourself that those equivalences make sense! With them, we can show that we can exchange the order of quantifiers if they are of the same kind. This does not hold in general! 

{{< box example >}}
With the predicates we defined earlier, we can construct the following true propositions:

* $∀x: (\operatorname{IsFish}(x) ⇒ \operatorname{HasScales}(x))$, meaning "Every fish has scalees"
* $∀x: (\operatorname{Animal}(x) ⇒ ¬\operatorname{BigNumber}(x))$, meaning "If x is an animal, then it can't be a big number"
* $∃x,y: (\operatorname{BigNumber}(x) \land \operatorname{BigNumber}(y) \land \operatorname{First}(x,y))$, meaning "A pair (x,y) of big numbers exist that share their most significant digit".

If we were to limit our universe of discourse to fishes, the first statement would be equivalent to $\forall x: \operatorname{HasScales}(x)$, since $\operatorname{IsFish}(x)$ is always true.
{{< /box >}}

## Potential pitfalls

The propositional and predicate calculus we introduced are very versatile in that they allow us a great deal of freedom in defining compound propositions and predicates. So let's play the devil's advocate and try to malignantly misuse this power placed in us to construct contradictions!

{{< box proposition Paradox >}}
In propositional logic, we might get away with defining a proposition $A$ in the following puckish manner:

$A :⇔ ¬A$

Clearly, this is enough to break our system - we require every proposition to be either true or false, but if we assume either of this was the case then the definition implies that it actually isn't. This is nothing but the translation of a well-known **paradox** into propositional logic:

**This sentence is false.**

The crux of the matter is the recursivity of the definition - it tries to tell us what $A$ is by saying how it relates to $A$ itself. This is problematic - even if we remove the inbuilt contradiction and just define $A :⇔ A$, that doesn't tell us what $A$ actually is. In other words, a statement such as *"we define recursivity to be what recursivity is"* is vacuous. We should better agree to not use this kind of sly trick in our definitions and thereby rid us of this paradox.
{{< /box >}}

Are our troubles over now? Not quite yet.

{{< box proposition Paradox >}}
In predicate logic, we have the additional power to define predicates. This actually allows us to sneak recursivity back in by defining

$A(x) :⇔ ¬x(x),$

meaning that given a parameter $x$ that is itself a predicate, $A(x)$ is true if and only if $x$ is false when taking itself as argument. To see why this leads to a contradiction, inserting $x=A$ leaves us with basically the same conundrum we were in earlier:

$A(A) ⇔ ¬A(A)$

While we did not explicitly refer to $A$ in its definition, the recursivity arises through the argument $x$ ranging over *all possible things $x$*, including $A$ itself. We can get around this, though, by taking seriously what we said earlier: We need to limit the objects $x$ to a **fixed** universe of discourse, **before** we go on and define predicates. This means that predicates themselves cannot be objects, precluding both $x=A$ and $x(x)$ and the contradiction that arises from them.
{{< /box >}}

## Higher-order logic and beyond
What we did when extending propositional calculus to predicate calculus was essentially the introduction of quantifiers that range over objects in a universe of discourse. We can actually make an analogous leap and allow quantification over predicates themselves in what we call **second-order logic**, but only if we take care in preventing paradoxes.

The trick is to introduce a separate new class of **second-order predicates**. Only they are allowed to take as arguments the usual predicates, which we call **first-order** in this context. Since second-order predicates still cannot take themselves as argument, we prevent any dangerous recursivity in our definitions.

{{< box example >}}
An **example** would be the second-order predicate $R(A)$, which tells us whether there exists an object for which a given predicate $A$ is realised,

$R(A) :⇔ \exists x: A(x),$

and now quantify over all predicates $A$ to express the trivial statement

$\forall A:  (\exists x : A(x)\iff R(A)).$
{{< /box >}}

From this new perspective we can call propositional logic **zeroth-order logic**, since there is no quantification at all there, and predicate logic would be **first-order logic**, since we have exactly one level of quantification (over objects). Repeating the process above yields second- and **higher-order logics**, where an $n$-th order predicate can take as arguments only predicates of order strictly smaller than $n$. We could even go so far and allow predicates of any finite order, yielding a prototypical **type theory** (in which every object of a theory has a type that determines what you can do with it).

{{< box note >}}
All these formalizations are considered part of **classical logic**, since they share a number of conventional features. There are a number of more exotic **non-classical logics**:

* **Modal logics** introduce operators that express modal modifications of a proposition $A$, capturing linguistic constructs such as *"it is necessary that $A$"*, *"it is possible that $A$"* or even *"there was a time, when $A$ held"*.

* **Intuitionistic logic** rejects *tertium non datur*, the idea that for every proposition either itself or its negation is true. This prohibits proofs by contradiction, instead aiming for constructive proofs which proponents consider more intuitive.

* **Many-valued logics** such as **fuzzy logic** don't restrict statements to be either true or false, instead allowing for a graded truth judgement.
{{< /box >}}

Apart from just using inference rules to prove theorems in a given formal system, there are properties of that system itself that we can investigate, relying on the validity of a method of reasoning outside of it. We could consider whether it is **consistent**, i.e. that one cannot derive contradictions within it, or check if it is **complete**, that is whether every true theorem can also be actually derived with a proof. Some famous results of this **metalogic** are the completeness theorems of propositional and predicate calculus, Gödel's two incompleteness theorems and Church and Turing's solutions to the *Entscheidungsproblem*.

Predicate logic is not only sufficiently powerful for an axiomatization of number theory but also simple enough that strong metalogical results can be derived. For this reason, contemporary mathematics uses it as a foundation in the standard construction of sets and numbers, which we are now prepared to rigorously understand in future articles.
