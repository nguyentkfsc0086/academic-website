---
title: Discrete Structure
date: 2025-08-02
tags: 
    - Mathematics
    - UMass Lowell
---
# Set theory

- ## Set: a collection of objects (called **elements**).  
  Notation: `{ }`

  **Example**:  
  $S = \{1,2,3,4,5\}$ → the elements of $S$ are integers.  
  - $2 \in S$ → “2 is an element of $S$”  
  - $7 \notin S$ → “7 is not an element of $S$”  

  **Properties**:  
  - A set is **not ordered**: $\{3,2,1\} = \{1,2,3\}$  
  - The elements of a set are **unique**: $\{4,4\} = \{4\}$  

  **Example**:  
  $A = \{a, b, c, d, \dots, x, y, z\}$  
  → here the dots mean “keep going.”  
  In this case, $A$ is the set of English letters.

---

- ## Common sets:  
  - $\mathbb{Z}$ = the set of integers (positive, negative, and $0$).  
  - $\mathbb{P}$ = the set of positive integers.  
  - $\mathbb{Q}$ = the set of rational numbers (fractions):  

    $$\mathbb{Q} = \left\{ \tfrac{a}{b} \;\middle|\; a,b \in \mathbb{Z},\; b \neq 0 \right\}$$  

    (The vertical bar `|` means *“such that”*.)  

  - $\mathbb{R}$ = the set of real numbers (all numbers on the number line).  
  - $\mathbb{C}$ = the set of complex numbers:  

    $$\mathbb{C} = \{ a + bi \;\mid\; a,b \in \mathbb{R},\; i^2 = -1 \}$$  

    (In this class, $\mathbb{R}$ and $\mathbb{C}$ will not appear much.)  

  **Example**:  
  $P =$ the set of cats in Lowell → this is a finite set.  

---

- ## Subset:  
  Given sets $A$ and $B$, we say **“$B$ is a subset of $A$”** if every element of $B$ is also an element of $A$:  

  $$B \subseteq A \;\;\Longleftrightarrow\;\; \forall x \;(x \in B \implies x \in A)$$  

  **Example**:  
  $S = \{3,4,\{3,4\},7,\{1\}\}$  
  - $1 \notin S$  
  - $\{1\} \in S$  
  - $\{1\} \subseteq S$  

---

> **Facts**:  
> - Every set is a subset of itself:  
>   $$A \subseteq A$$  
> - Two sets are equal if and only if they are subsets of each other:  
>   $$A = B \;\;\Longleftrightarrow\;\; (A \subseteq B \;\wedge\; B \subseteq A)$$
