---
title: Discrete Structure
date: 2025-08-02
tags: 
    - Mathematics
    - UMass Lowell
---
# Set theory

- ## Set 
  Defination: a collection of objects (called **elements**).  
  Notation: {}

  **Example**:  
  {{% math %}}
  $$
  S = \{1,2,3,4,5\}
  $$
  {{% /math %}}

  “2 is an element of S": 
  {{% math %}}
  $$
  2 \in S
  $$
  {{% /math %}}
  "7 is not an element of S”:
  {{% math %}}
  $$
  \qquad 7 \notin S
  $$
  {{% /math %}}

  **Properties**:  
  - A set is **not an ordered list** so we can understand that:
    {{% math %}}
    $$
    \{3,2,1\} = \{1,2,3\}
    $$
    {{% /math %}}
  - The elements of a set are **unique**:
    {{% math %}}
    $$
    \{4,4\} = \{4\}
    $$
    {{% /math %}}
     But nobody using the set on the right side
  **Example** (English letters):  
  {{% math %}}
  $$
  A = \{a, b, c, d, \dots, x, y, z\}
  $$
  {{% /math %}}

---

- ## Common sets  

  Integers:  
  {{% math %}}
  $$
  \mathbb{Z}
  $$
  {{% /math %}}

  Positive integers:  
  {{% math %}}
  $$
  \mathbb{P}
  $$
  {{% /math %}}

  Rationals: any number can be written as a fraction
  {{% math %}}
  $$
  \mathbb{Q} = \left\{\frac{a}{b} \,\middle|\, a,b \in \mathbb{Z},\; b \neq 0 \right\}
  $$
  {{% /math %}}

  (Here the vertical bar “\(|\)” means **“such that.”**)

  Reals: 
  {{% math %}}
  $$
  \mathbb{R}
  $$
  {{% /math %}}

  Complex numbers: including imaginary number,.... 
  {{% math %}}
  $$
  \mathbb{C} = \{\, a + bi \mid a,b \in \mathbb{R},\; i^2 = -1 \,\}
  $$
  {{% /math %}}

  We cam also create our custom set
    **Example** (finite custom set):  
    {{% math %}}
    $$
    P = \{\text{cats in Lowell}\}
    $$
    {{% /math %}}

---

- ## Subset:  
  “\(B\) is a subset of \(A\)” means every element of \(B\) is also an element of \(A\)”:
  {{% math %}}
  $$
  B \subseteq A \;\Longleftrightarrow\; \forall x\, (x \in B \Rightarrow x \in A)
  $$
  {{% /math %}}

  **Example**:  
  {{% math %}}
  $$
  S = \{3,4,\{3,4\},7,\{1\}\}
  $$
  {{% /math %}}

  Then:
  {{% math %}}
  $$
  1 \notin S,\qquad \{1\} \in S,\qquad \{1\} \subseteq S
  $$
  {{% /math %}}

---

> **Facts**
>
> Every set is a subset of itself:
> {{% math %}}
$$
> A \subseteq A
$$
> {{% /math %}}
>
> Two sets are equal iff they are subsets of each other:
> {{% math %}}
$$
A = B \;\Longleftrightarrow\; (A \subseteq B \;\wedge\; B \subseteq A)
$$
> {{% /math %}}
