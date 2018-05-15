---
title:  "Mathematical Foundations: Axiomatic Set Theory"
tags: [maths,foundations,set-theory]
draft: true
---


<figure class="figright" style="width:42%">
<img src="/images/posts/foundations-sets.png"/>
</figure>

Since roughly the beginning of the 20th century, most mathematical results are formulated in the language of **set theory**. Georg Cantor, who is considered one of the founders of the discipline, introduced sets as "the collection of certain distinguishable objects of our intuition or thought (called elements of the set) into a whole". While unpublished letters show that Cantor already had a much more sophisticated understanding of the subject than many give him credit for today, the problem with using this formulation as a definition is that it can be interpreted very differently by different people - even to the point of leading to paradoxes.

Now, what to do when different people think different properties are "natural" to hold true, and we can derive paradoxes from some of those properties? We try to find a **consistent axiomatization** of set theory, i.e. agree on a few definite axioms that we regard as part of what we mean by talking about sets and try to make sure that those axioms we chose cannot be used to derive a contradiction. Humans, being their usual quarrelsome selves, could not agree on one universal set of axioms, so I will try to provide an overview rather than tie us to a specific system. Luckily, the choice ultimately does not really matter that much for most of practical mathematics.

<!--more-->
1. TOC
{:toc}

## Keeping it visual with Euler diagrams

Before we start our attempt at an axiomatization, let us survey what we want to capture abstractly by visualizing it first. You probably know the standard method of visualizing sets: In a **Euler diagram**, we think of sets as two dimensional shapes in a plane that represents the space of possible elements. For simple sets, we might explicitly draw points in the plane and label them as objects that belong to any set whose shape contains them:

<figure class="figmiddle">
<img src="/images/posts/foundations-sets-1.png" style="margin-left:auto; margin-right:auto;width:75%"/>
</figure>

When we have more complicated sets, especially for infinite ones, we refrain from drawing in *all* elements (although we might include some especially interesting ones):

<figure class="figmiddle">
<img src="/images/posts/foundations-sets-2.png" style="margin-left:auto; margin-right:auto;width:75%"/>
</figure>

We can imagine sets that share some elements as shapes with an overlap. This leads us to several notions that express relationships between sets: We call two sets that don't have any overlap **disjoint**, and **subsets** are sets that are entirely contained in a second set.

<figure class="figmiddle">
<img src="/images/posts/foundations-sets-3.png" style="margin-left:auto; margin-right:auto;width:75%"/>
</figure>

The usual convention is that if you draw sets without an overlap, you're implying that they do not share elements. But if you do draw an overlap, they might share elements, but you're also leaving open the possibility that there happen to be no elements within that overlap and the sets are disjoint after all. This allows you to visualize sets *without yet knowing* if they are disjoint or not. Those Euler diagrams which leave open all possibilities - where every set has an overlap with every combination of all other sets - are called **Venn diagrams**. It is possible to show that you can draw such diagrams for any possible number of sets, but they become visually complex very quickly. These are possible Venn diagrams for two, three and four sets:

<figure class="figmiddle">
<img src="/images/posts/foundations-sets-4.png" style="margin-left:auto; margin-right:auto;width:75%"/>
</figure>

Given two sets $$A$$ and $$B$$, there are natural ways to combine them: The **union $$A\cup B$$** contains the elements of either of them; the **intersection $$A\cap B$$** contains those elements that are in both; the **difference $$A\setminus B$$** contains all elements of $$A$$ that are not in $$B$$ and, finally, the **symmetric difference $$A\Delta B$$** contains exactly those elements that are in either one or the other set, but *not* both. Finally, if we're talking about sets that are all part of a specific larger set $$M$$, we often speak of the context-dependent **complement $$A^c := M\setminus A$$**. Visually, these constructions look like this:

<figure class="figmiddle">
<img src="/images/posts/foundations-sets-operations.png" style="margin-left:auto; margin-right:auto;width:78%"/>
</figure>

Be aware that there are spurious features of this visualization. For example, it suggests connectedness, finiteness, a sense of direction and distance. There are sets for which it makes sense to talk in such terms, such as the real number line - but these are special cases which require the sets to have some kind of additional structure, something we will consider later.

Something that is harder to visualize in this image are sets that themselves are *elements of another set* - note the difference to sets that are subsets of other sets!

<figure class="figmiddle">
<img src="/images/posts/foundations-sets-7.png" style="margin-left:auto; margin-right:auto;width:90%"/>
</figure>

One typical such set that contains sets is the **power set $$\mathcal{P}(A)$$** of a given set $$A$$. It contains all sets that are a subset of $$A$$. By convention, we usually count the **empty set $$\emptyset$$** as a subset of any other set, so that any power set always contains the empty set as an element.

Another construction that is not quite obvious is the **cartesian product $$A\times B$$**. Here, we start out with two sets $$A$$ and $$B$$ and then construct the set of all **pairs** of objects, where the first object of the pair is taken from $$A$$ and the second from $$B$$. Note that these pairs have to be **ordered** for that, i.e. a pair $$(a,b)$$ does not equal a pair $$(b,a)$$!

You could think of this construction as a table: you arrange the elements of the sets $$A$$ and $$B$$ as the headings of rows and columns of a table, respectively. In a given cell of the table, you find the pair of elements that corresponds to exactly the headings of the row and column that you find it in. The whole body of the table, containing all cells as elements, then represents the product set.

<figure class="figmiddle">
<img src="/images/posts/foundations-sets-8.png" style="margin-left:auto; margin-right:auto;width:40%"/>
</figure>

This mental image becomes more vivid when you consider the special case of sets that can be considered to be continuous. Consider, say, the cartesian product of two line segments. The resulting object can be thought of as a kind of *continuous table*, or just a two-dimensional surface. You could repeat the process and take the cartesian product of this surface with another line segment to arrive at a three-dimensional cube. Alternatively, you could take the cartesian product of a line segment with a set that corresponds to a disc and think of the result as a cylinder:

<figure class="figmiddle">
<img src="/images/posts/foundations-sets-9.png" style="margin-left:auto; margin-right:auto;width:60%"/>
</figure>

This kind of visualization is no longer a Euler diagram, of course.

This construction was used by Descartes, after whom the cartesian product is named, to express space in **cartesian coordinates**: You can identify every point in the plane with a pair $$(x,y)$$ of real numbers that stand for the horizontal and vertical distances to a fixed origin. But $$(x,y)$$ is just an element of the cartesian product of the real numbers with itself! This was a huge step forward since it made it possible to use the tools of algebra to investigate geometry and formalize notions such as velocity, acceleration and forces.

You might wonder why we call this a product - one way to see the correspondence is to think of how multiplication is first taught at school: you count the boxes you get when constructing a retangle that is $$x$$ boxes high and $$y$$ boxes wide. This parallels the result of the cartesian product of two fnite sets with $$x$$ and $$y$$ elements!


## The universe of discourse

{% box note %}
**Warning.** Be aware that I am by no means an expert on axiomatic set theory; this is only my best attempt at an introduction!
{% endbox %}

In the spirit of axiomatizations, the intuitive concept that cantor described - "the collection of certain distinguishable objects of our intuition or thought into a whole" - is not specific enough for us to call a definition. Instead, we regard this and the constructions of the last section as a **notion**: An informal concept that guides our thinking. When we want to stress the difference, we today often use the term **collection** for this intuitive notion and reserve the designation **set** for specific formal objects. Actually, there are up to three different kinds of objects that might come up - we start our journey with a...

{% box definition %}
**Definition.** We introduce the two-argument **membership predicate** $$x\in M$$ for our intuitive notion of "x is an element of M". The purpose of the remaing axioms will be to unambiguously state the nature of this predicate. There's also a shorthand for its negation: $$x\not\in M$$.

Our universe of discourse is spanned by these different **sorts** of objects:

* **Urelements** are objects that can only be elements of something, not contain elements themselves.
* **Sets** can sensibly be found on both sides of the membership predicate.
* **Proper classes** are objects that can only have elements, but can never be elements of something themselves.

We will collectively refer to objects that make sense on the left-hand side of the membership predicate, i.e. urelements and sets, as **elements**, and to objects that make sense on the right-hand side, i.e. sets and proper classes, as **classes**. 

A statement using the membership predicate with incompatible objects always evaluates to *false*.
{% endbox %}

{% box example %}
**Examples.**

* Think of **urelements** as any regular thing, like the number 5 or the color blue.
* Any kind of collection whose definition doesn't sound suspiciously recursive is likely to be a **set**, such as the set of natural numbers, the set of colours or the set of letters in the latin alphabet. The latter, for example, can also be seen as an element in the set which contains a set of letters for every possible alphabet in the world.
* Think of **proper classes** as a tool to group together urelements and sets, but which do not make sense as definite objects in their own right. We will soon see why some collections cannot always be formalized as sets!
{% endbox %}

This partition of our universe of discourse into three makes our background logic a **three-sorted predicate logic**. Note that a given axiomatization does not neccessarily introduce urelements and proper classes - the most common one, due to Zermelo and Fraenkel, is entirely content with using only sets themselves! But whichever of these three kinds of objects we allow, their totality is what makes up the universe.

{% box definition %}
**Definition.** In many-sorted predicate logic, we introduce quantifiers that range only over a given specific sort of object. In our case, if *sort* is one of (ur-) elements, sets and (proper) classes, we write $$\forall \text{sort }X$$ and read it as "for all objects $$X$$ of sort *sort*".

Similar definitions apply for the other quantifiers.
{% endbox %}

{% box definition %}
**Definition.** For any class $$M$$ we also define a shorthand $$\forall x\in M:A(x)$$ that is true if and only if $$\forall \text{elements } x: (x\in M \implies A(x)).$$

Similar definitions apply for the other quantifiers.
{% endbox %}

In natural language, this reads as "for all elements $$x$$ of $$M$$, $$A(x)$$ holds". Note that this sentence doesn't really specify how to interpret the case when $$M$$ contains no elements at all, but the symbolic definition makes it clear that this expression is then true independently of $$A(x)$$.

Now we already have enough machinery in place to define subsets and supersets:

{% box definition %}
**Definition.** We can define predicates that allow us to specify relationships between classes $$A$$ and $$B$$:

* $$A$$ is a **subclass** of $$B$$, $$A\subseteq B$$, if and only if $$\forall\text{elements } x: x \in A \implies x\in B$$,
* its negation $$A \not\subseteq B :\iff \neg(A\subseteq B)$$,
* $$A$$ is a **proper subclass** of $$B$$, $$A\subsetneq B$$, if and only if $$A\subseteq B$$ but $$A\not=B$$,
* $$A$$ and $$B$$ are **disjoint**, if and only if $$\not\exists\text{element }x: x\in A \land x\in B.$$ We call more than two classes **pairwise disjoint**, if any pair of them are disjoint.

The symbol $$\subset$$ is used by some authors to refer to general subclasses, while others use it only for proper subclasses in analogy to the strict order &lt; on the real numbers. To avoid this ambiguity, we won't use this symbol at all. If we flip these symbols, we obtain the **superclass** $$A\supseteq B \iff B \subseteq A$$ and analogous constructions.

If a sub- or superclass actually is a set, we use the more specific names **sub- and superset** (which are of course much more common in mathematical practice).
{% endbox %}

Note that the informal sentence "A contains B" can be understood to mean either $$B\in A$$ or $$B\subseteq A$$. For this reason, mathematicians often differentiate such statements by appending either "as an element" or "as a subset/class".

{% box example %}
**Examples.**
* The set of even numbers is a proper subset of the set of integers.
* The set of even numbers, the set of odd numbers and the set of polar bears are pairwise disjoint.
* Any set is a subset of itself, but no set is a proper subset of itself.
* The set of positive numbers is a superset of the set of numbers larger than three.
* The set of equilateral triangles is a subset of the set of triangles.

{% endbox %}

## Extensive classes

Up to now, we have not really filled the membership predicate $$\in$$ with any meaning - we only used it to characterize our universe of discourse and the concept of subsets, *presupposing* the intended meaning. In the spirit of Wittgenstein's "meaning is use", our task now is to give meaning to it by specifying the axioms that govern its use.

One axiom is blessfully unproblematic and found in practically any axiomatization:

{% box definition %}
**Definition (Axiom of Extensionality).**

$$\forall \text{classes } x,y: \left(\forall \text{elements }z: (z\in x\iff z\in y) \implies x=y\right)$$

{% endbox %}

The introduction of this axiom is necessary to ensure that the notion of "equality", which we automatically inherited from predicate logic, is compatible with what we think of as equal collections. What it says is just that two classes are the same if and only if they have exactly the same elements!

This already allows us to formulate our first proposition. And it is a very useful one:

{% box proposition %}
**Proposition.** For any two classes $$A$$ and $$B$$:

$$A=B \iff A\subseteq B \land A\supseteq B$$

{% morebox Proof: %}
**Re $$(\Rightarrow)$$:**<br/>
For all elements $$x$$, the statement $$x\in A \implies x\in A$$ is trivially true (any proposition implies itself). Since $$A=B$$, we can replace $$A$$ and $$B$$ with each other in any context. In this case, this yields $$\forall\text{elements }x: x\in A\implies x\in B$$ as well as $$\forall\text{elements }x: x\in B\implies x\in A$$, which are just the definitions of $$A\subseteq B$$ and $$B\subseteq A$$.

**Re $$(\Leftarrow)$$:**<br/>
Per definition of $$A\subseteq B$$ and $$B\subseteq A$$ we have $$\forall\text{elements }x: x\in A \Rightarrow x\in B \land x\in B \Rightarrow x\in A.$$ But in propositional calculus, implication in both directions implies equivalence, so we find $$\forall\text{elements }x: x\in A \iff x\in B$$, which by the Axiom of Extensionality implies $$A=B$$.
{% endmorebox %}
{% endbox %}

In mathematical practice, you would probably not spell out the proof at this level of detail but accept a statement like this without question. Indeed, we only do it here since we are currently investigating the foundations of our way of thinking.

{% box definition %}
**Definition.** We call a class $$\emptyset$$ **empty**, if $$\forall\text{elements }x: x\not\in\emptyset.$$

{% endbox %}

We introduced the special symbol $$\emptyset$$, since empty classes are basically unique:

{% box proposition %}
**Proposition.** Any two empty classes are equal.

{% morebox Proof: %}
Let $$A$$ and $$B$$ be two empty classes and $$x$$ any element whatsoever. Then $$x\in A$$ and $$x\in B$$ are both false since $$A$$ and $$B$$ are empty, so that $$x\in A \iff x\in B$$, which directly implies $$A=B$$ via the Axiom of Extensionality.
{% endmorebox %}
{% endbox %}

Now, we're off to a good start, but we are lacking a very important ingredient: We know how to see if two given sets or more generally two given classes are equal, but we have not yet ascertained the existence of any class at all! Not even that of an empty class, even though we know it's unique if it exists.

Since we determine equality based on a classes elements, there seems to be a natural candidate for the job:

## Unrestricted comprehension!

{% box definition %}
**Definition (Axiom Schema of Unrestricted Set Comprehension).**
For any predicate $$A(x)$$, we introduce the following axiom:

$$\exists\text{set }M: \forall\text{elements }x:(x\in M \iff A(x)).$$

We introduce the notation $$M=\{x\vert A(x)\}$$ for the set that is generated by $$A(x).$$
{% endbox %}

What this axiom tells us is that for every predicate $$A(x)$$ there is a set $$M$$, so that $$A(x)$$ determines whether any element $$x$$ is in or out: $$x\in M \iff A(x).$$ Basically: *if we know what elements we want to collect together, they make up a set.* In case you're worried: The uniqueness of the set $$\{x\vert A(x)\}$$ is guaranteed by the Axiom of Extensionality in a very similar manner to the uniqueness of the empty set.

{% box note %}
**Note.** You might have noticed either that we dubbed this an axiom *schema*, or that we did something that should ring alarm bells when dealing with *first-order* predicate calculus: We quantified over *all predicates*, something that should only be possible in a second-order logic! Indeed, if we were using second-order logic, we would simply have called this a normal axiom. But we, and many others, chose a different path: We say that we want to introduce one specific axiom for any possible predicate, and describe this infinite number of axioms using the axiom schema. In other words, we do not quantify over predicates within the logic system, but only within the natural language we use to describe axioms. This might feel like cheating, but it saves us from having to also allow second-order statements *within* the formal language, which would considerably drive up its complexity. Sometimes, we can even replace axiom schemas with a few regular axioms and demonstrably arrive at the same theory - we then say that the theory is *finitely axiomatizable*, which some people might find ontologically reassuring.
{% endbox %}

Sadly, the story turns out to be more complicated than just taking this very nice and powerful axiom schema. Betrand Russell and Ernst Zermelo independently came across the following argument:

{% box example %}
**Russell's Paradox.** The Axiom of Unrestricted Comprehension asserts the existence of the following set:

$$M = \{x \vert x\not\in x \},$$

i.e. the *set of all sets that do not contain themselves*. The paradox is this: **Does $$M$$ contain itself as an element?** Per the definition of $$M$$, we directly obtain

$$ M\in M \iff M\not\in M. $$

Something clearly went awry here, since the proposition $$M\in M$$ must be either true or false and can't be equivalent to its own negation!
{% endbox %}

These few lines are the root of most of our troubles in set theory! We introduced proper classes for the sole purpose to describe something like the collection of all sets that do not contain themselves. And indeed, if we took $$M$$ to be a proper class instead of a set then no problem would arise: As per our axiom, the equivalence $$x\in M \iff x\not\in x$$ is supposed to only hold for all *elements* $$x$$. For a proper class $$M$$, $$M\in M$$ would simply be set to false without contradicting that statement at all!

We therefore refine our previous axiom. Instead of guaranteeing the existence of the appropriate set we only guarantee the existence of a class - which might or might not be a set. Russell's argument can then be considered as the proof that the class of all sets that do not contain themselves can only consistently be formalized as a proper class.

{% box definition %}
**Definition (Axiom Schema of Unrestricted *Class* Comprehension).** For any predicate $$A(x)$$, we introduce the following axiom:

$$\exists\text{class }M: \forall\text{elements }x:(x\in M \iff A(x)).$$

We introduce the notation $$M=\{x\vert A(x)\}$$ for the class that is generated by $$A(x).$$

This or comparable axioms can indeed be found in most axiomatizations whose universe of discourse actually encompasses proper classes.

{% endbox %}

## Construction of classes

With this axiom at hand, we can start constructing some properly useful classes:

{% box definition %}
**Definition.** Given a finite number $$n$$ of elements that we here label $$a_1, ..., a_n$$, we can define a class that contains exactly these elements:

$$\{a_1, ..., a_n\} := \{x \vert x=a_1 \lor x=a_2 \lor ... \lor x=a_n\}$$
{% endbox %}

Note that the ellipsis "…" is not part of the formal language, but has to be interpreted as a way for us to simultaneously define this notation for any finite number of elements. This corresponds exactly to the difference between an axiom and an axiom schema.

{% box definition %}
**Definition.** Let $$A$$ and $$B$$ be classes. We define...
* the **empty class** $$\emptyset := \{ x \vert x\neq x \},$$ 
* the **union** $$A\cup B := \{ x \vert x\in A \lor x\in B \},$$ 
* the **intersection** $$A\cap B := \{ x \vert x\in A \land x\in B \},$$
* the **difference** $$A\setminus B := \{ x \vert x\in A \land x\not\in B\},$$
* the **symmetric difference** $$A\Delta B := (A\cup B)\setminus (A\cap B),$$
* if it is clear from context that we are considering only subclasses of a given big class $$M$$, we define the **complement** $$A^c := M\setminus A,$$
* the **power class** $$\mathcal{P}(A) := \{x \vert x \subseteq A \}$$, which contains all subsets (not subclasses!) of $$A$$ as elements including the empty set $$\emptyset,$$
* the **cartesian product** $$A\times B$$, which contains all pairs/2-tuples $$(a,b)$$ of two elements with $$a\in A$$ and $$b\in B.$$
{% endbox %}

You might (rightly) complain about the lack of rigour in the definition of the cartesian product, since pairs of elements are a completely new ingredient to our formal system. That is actually one way to deal with this: Introduce pairs of elements (not of proper classes!) as new primitive sorts of urelements into our universe of discourse. But this is not actually necessary - if you want to see a (somewhat complex) formalization that uses only our existing machinery to introduce pairs and thereby cartesian products, check out appendix BLUB BLUB.

Since the logical "and" and "or" are associative, the definitions above imply that the union and intersection are also associative, i.e. $$(A\cup B)\cup C = A\cup(B\cup C)$$. For this reason, we can drop parentheses when repeating these operations without introducing an ambiguity in the order of operations. We often drop parentheses around repeated cartesian products too, athough it is **not** associative: The elements $$(a,(b,c))\in A\times(B\times C)$$ and $$((a,b),c)\in (A\times B)\times C$$ are not actually the same! But usually, it doesn't really matter which order of parentheses you choose as long as you stick to it. To adopt a convenient notation that doesn't care about the parentheses, we often just write $$(a,b,c)\in A\times B\times C$$.

For the union and intersection, we can generalize these set operations somewhat:

{% box definition %}
**Definition.** For a class $$M$$, whose elements are all sets (not urelements), we define

* the **arbitrary union** $$\bigcup M = \{x\vert \exists y\in M: x\in y\}$$,
* the **arbitrary intersection** $$\bigcap M = \{x\vert \forall y\in M: x\in y\}.$$

Alternatively, if we have a set $$A_i$$ for every element $$i\in I$$ of an **index class**, we introduce shorthands

* for the **indexed union** $$\bigcup\limits_{i\in I} A_i = \bigcup\{ y \vert \exists i \in I: y=A_i  \} = \{x\vert \exists i\in I: x\in A_i  \},$$
* for the **indexed intersection** $$\bigcap\limits_{i\in I} A_i = \bigcap\{ y \vert \exists i \in I: y=A_i  \}= \{x\vert \forall i\in I: x\in A_i  \}.$$

{% endbox %}

This is a generalization in the sense that $$A\cup B = \bigcup\{A, B\}$$ as well as $$A\cap B = \bigcap\{A, B\}$$ - the arbitrary union is just the union over all sets within the class $$M.$$ This class can even be infinite, just like the index class $$I$$!

{% box definition %}
**Definition.** The **disjoint union** $$A\dot\cup B$$ of two classes $$A$$ and $$B$$ is similar to the union $$A\cup B,$$ but *artificially treats the classes $$A$$ and $$B$$ as if they were disjoint*. If indeed $$\exists x\in A\cap B,$$ then we would include one copy of $$x$$ in $$A\dot\cup B$$ for each of $$A$$ and $$B$$ (usually inventing some kind of notation like $$x_A$$ and $$x_B$$ to not mix them up).

This notion can be rigorously implemented in several equivalent ways. One possibility is to define $$A\dot\cup B := (A\times \{a\})\cup(B\times \{b\}),$$ where $$a$$ and $$b$$ are any two distinct fixed elements such as, for example, the numbers 1 and 2 that we will define in the next chapter.
{% endbox %}

{% box note %}
**Note.** Confusingly, the proposition $$C=A\dot\cup B$$ is often also used as a shorthand for
* $$C=A\cup B$$ and
* the classes A and B are disjoint already.

I will not use it in this sense, but one can often deduce what an author means: If $$C=A\dot\cup B$$ is used to *define* a new set $$C$$, she usually refers to our definition. If $$A, B$$ and $$C$$ are already defined, then $$C=A\dot\cup B$$ serves as the shorthand for the two propositions above. 
{% endbox %}

We have gotten quite far now and entered a landscape of different kinds of classes, which we can combine using a variety of operations. However, we initially wanted to learn about the existence of sets. And for good reason: With the axioms we have now, there is no way to tell if any gives class is also a set - but only sets can be nested within other sets, which is central to provide the power and versatility that is absolutely neccessary for much of modern mathematics.

There are several paths to pursue here, of which we will only present two. The first is the approach chosen by Betrand Russell for his theory of types. It certainly does the job, but turns out to be somewhat unwieldy. The second is employed in the currently most widely accepted foundational axiomatization due to Zermelo and Fraenkel, which we will consider in more detail.

## Type theory

If you take a look back at the pitfalls of predicate calculus, you might realize that Russell's paradoxon is just a new face on an old foe: If predicates are turned into sets and the evaluation $$A(x)$$ of a predicate into the membership proposition $$x\in A$$, then our old friend

$$A(x):\iff \neg x(x)$$

reveals itself to be Russell's set:

$$x\in A \iff x\not\in x.$$

Russell's idea to allow nested sets but still keep around the possibility to define sets using something like set comprehension now mirrors the construction that allowed us to have a higher-order predicate calculus without succumbing to contradictions. As for predicates, which could only take predicates of lower order as an argument, we assign a type to each set and only allow it to contain sets of lower type as elements.

A set comprehension axiom schema could then be introduced that allows one to construct a set of $$(n+1)$$-th type, which contains only sets of $$n$$-th type that fulfill a predicate $$A(x)$$, which we might denote $$\{x^n\vert A(x) \}.$$

Russell's paradoxon would be defused since with $$M := \{x^n\vert x\not\in x \},$$ the equivalence

$$y\in M \iff y\not\in y$$

would only hold for sets $$y$$ of $$n$$-th type, not for the $$(n+1)$$-th type set $$M.$$ For that, $$M\in M$$ would simply be false due to our rule to disallow sets to contain sets of the same type.

The problem with this approach, which Russell and Whitehead worked out in great detail in their *Principia Mathematica*, is that it takes a lot of bookkeeping to perform very simple mathematical tasks- you always have to keep in mind the type of any set you're dealing with and carefully match the types of your constructions. Instead, we will focus on a more comfortable axiomatization.

## Zermelo-Fraenkel axiomatization

In Zermelo-Fraenkel set theory, everything is a set - and if it's not a set, it doesn't exist. What I mean is that ZF only formalizes sets, without urelements or proper classes.

everything is a set

We can restrict what we have discussed already to this smaller universe of discourse,  . In particular, the membership predicateis still around, this time without limitations since everything is a set

definitions stick around

classes informal notion - if a set, then 

The Axiom Schema of Class Comprehension doesn't get us anywhere   instead

{% box definition %}
**Definition (Axiom Schema of Restricted Comprehension).**

!

{% endbox %}
 

{% box definition %}
**Definition (Axiom of Regularity).**

!

{% endbox %}

replacement


axiom of choice

Class extensions of ZF

## Actual results!

I'd like to give one example of a simple proposition of pure set theory:

ONE VERY SIMPLE EXAMPLE

disjoint ... intersection is empty

{% box proposition %}
**Proposition (de Morgan's Rules for Sets).** For two sets $$A$$ and $$B$$ with respect to a common superset $$M$$, the following equalities hold:

\begin{equation}
(A\cup B)^c = A^c \cap B^c \qquad (A\cap B)^c = A^c \cup B^c \notag
\end{equation}

{% morebox Proof: %}
The proof immediately follows from de Morgan's rules in propositional calculus due to the correspondence of unions and intersections to the logic AND and OR.
{% endmorebox %}
{% endbox %}

ONE MORE EXAMPLE

Many more of the simple propositions in propositional calculus can be "translated" to sets using this correspondence of logical connectives and set operations, like the symmetry $$A\cup B = B\cup A$$ of the union. Try to do this yourself!

## Proving propositions with Venn diagrams

Venn diagrams are useful beyond just having a visual image of a given construction of a set. You can actually use them to prove some simple equalities this way, and probably faster and more reliable than by spelling out the argument in a formal system!

Suppose you have a number of sets

proof de Morgan BLUB

<figure class="figmiddle">
<img src="/images/posts/foundations-sets-de-morgan.png" width="30%" style="margin-left:auto; margin-right:auto;"/>
</figure>


## Outlook

Besides functions, obvs

alternative axiomatizations
consistency, finitely axiomatiyable

cardinal and ordinal numbers
cumulative hierarchy neumann




##################################### CUT!


The most successful and widely adopted axiomatization was introduced by Zermelo and Fraenkel (**ZF**). Since a number of theorems can only be proven with an additional axiom, the **axiom of choice**, this is often included as **ZFC**. 


{::comment}
{% box definition %}
**Axioms (Zermelo-Fraenkel set theory and axiom of choice).**
1. **Axiom of Extensionality:** *If two sets have the same elements, they are equal*<br/>
   $$\forall x,y: \left(\forall z: (z\in x\iff z\in y) \implies x=y\right)$$
2. **Axiom of regularity:**
3. **Axiom schema of specification:**
4. **Axiom of pairing:**
5. **Axiom of union:**
6. **Axiom schema of replacement:**
7. **Axiom of infinity:**
8. **Axiom of power set:**
9. **Axiom of choice:**
{% endbox %}
{:/comment}

Since we saw that it is possible to generate contradictions if we define sets to broadly, it would be nice to prove the consistency of an axiomatic system of logic. We cannot use that system itself to formulate the proof, of course. Instead, one of the tasks the mathmaticians of the early 20th century set themselves was to formulate it with so-called "finitary reasoning", which was seen as particularly philosophically persuasive. This task was indeed archieved for propositional and predicate logic itself, but Kurt Gödel overthrew the program when he showed that the consistency of **ZF** and similarly powerful systems is impossible to prove. Therefore, it can ultimately be seen as just a working hypothesis. The fact that no contradiction has been found over one hundred years of intense study suggests it is not a bad one at least.


* for the **cartesian product** $$x\in ⨉\limits_{i\in I} A_i$$, which contains all **families** $$(x_i)_{i\in I}$$ with $$x_i\in A_i$$ as elements (we will later define families in the section on functions, but you can think of them as infinitely long tuples for now).

## Appendix A: Pairs and cartesian products


