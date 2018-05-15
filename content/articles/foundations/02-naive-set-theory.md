---
title:  "Mathematical Foundations: Naïve Set Theory"
tags: [maths,foundations,set-theory]
draft: true
---


<figure class="figright" style="width:42%">
<img src="/images/posts/foundations-sets.png"/>
</figure>

Since roughly the beginning of the 20th century, most mathematical results are formulated in the language of **set theory**. Georg Cantor, who is considered one of the founders of the discipline, introduced sets as "the collection of certain distinguishable objects of our intuition or thought (called elements of the set) into a whole".

purpose, link to axiomatic

<!--more-->
1. TOC
{:toc}

## Sets and elements

## Keeping it visual with Euler diagrams

Let us survey what kind of constructions we want to capture abstractly by visualizing them first. You probably know the standard method of visualizing sets: In a **Euler diagram**, we think of sets as two dimensional shapes in a plane that represents the space of possible elements. For simple sets, we might explicitly draw points in the plane and label them as objects that belong to any set whose shape contains them:

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

## Sets as a first-order theory

universe of discourse

again: axiom of extensionality

quantification


## Relations between sets

definitions

deecomposition equality

empty set(s)

## Set constructions

repeat set comprehension

definition simple

axiom of choice

arbitrary and indexed

disjoint union

## Kind Regards, Set Theory

discuss regarding sets as the same or different etc
esp disjoint union and multiple cartesian products

## Propositions

import set theory props, discuss proof methods, including venn

## Basic cardinality NOPE, PUT INTO FUNCTIONS

## Paradoxa and classes


## Outlook




