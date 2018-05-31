---
title:  "Mathematical Foundations: Order Theory"
tags: [maths,foundations,order-theory]
draft: true
---

Comparing objects based on some relation is a basic operation. One might say that person A did better in a race than person B. In this comparison, we compare two people based on a property assigned to them - so if person A came first and person B was 3rd to finish the race, then really the comparison is between those numbers.
In this example we are thus comparing two natural numbers, but the intuition of "order" extends very naturally to real, rational and whole numbers as well.

Looking back at predicate logic (link), comparisons as the placement of people in a race can be evaluated with a binary outcome (TRUE or FALSE). If P is the set of people competing, and we look at the statement A(p1,p2) as "p1 finished the race later than p2" and say whether that statement holds true for a given pair of people p1 and p2 out of the competing racers.

Thus talking about ordering between objects, we are looking at a specific subset of binary relations. Rephrased with infix notation for the relation "finished the race later", we could write p1 R p2.

To distinguish order relations from other types of binary relations, we first look at some of the different properties that relations can have, which will allow us to define different order relations.

## Properties of relations

{{< box definition >}}
Let <span class="math">M</span> be a set and <span class="math">R</span> a binary relation on <span class="math">M</span>.

Then R is

* **reflexive** when <span class="math"> \forall x \in M: xRx</span>.

* **irreflexive** when <span class="math"> \forall x \in M: \neg(xRx)</span>

* **symmetric** when <span class="math"> \forall x,y \in M: xRy \Leftrightarrow yRx</span>

* **antisymmetric** when <span class="math"> \forall x,y \in M: xRy \land yRx \Rightarrow x=y</span>

* **asymmetric** when <span class="math"> \forall x,y \in M: xRy \Rightarrow \neg(yRx)</span>

* **transitive** when <span class="math"> \forall x,y,z \in M: xRy \land yRz \Rightarrow xRz</span>

* **trichotomous** when <span class="math"> \forall x,y \in M: xRy \oplus yRx \oplus x=y</span>

* **total** when <span class="math"> \forall x,y \in M: xRy \lor yRx</span>

{{< /box >}}


## Order relations

{{< box definition >}}
A **Poset** (partially ordered set) is a tuple <span class="math">(M, \le)</span> consisting of a set <span class="math">M</span> and a relation <span class="math">\le</span> that is reflexive, antisymmetric and transitive.
{{< /box >}}

{{< box definition >}}
A **totally ordered set** is a poset where the relation <span class="math">\le</span> is additionally total.
{{< /box >}}

{{< box definition >}}
A **strictly ordered set** is a tuple <span class="math">(M, <)</span> consisting of a set <span class="math">M</span> and a relation <span class="math"><</span> that is irreflexive, asymmetric and transitive.
{{< /box >}}

## Hasse Diagrams

A Hasse diagram represets finite posets as a graph, allwoing for easy visualisations of the order structure imposed on the set.

The vertices in a Hasse diagram are the elements of the poset  <span class="math">(P, \le)</span> and edges are drawn between vertices <span class="math">x, y \in P</span> if  <span class="math">(x \le y) \land (\nexists z \ne x,y \in P: x \le z \le y)</span>. The position of vertex y is then drawn higher up in the diagram than vertex x.

