---
title: Discrete Structure
date: 2025-08-02
tags: 
    - Mathematics
    - UMass Lowell
---
# Set theory

- ## Set 
  Definition: a collection of objects (called **elements**).  
  Notation: {}

  **Example**:  
  {{< math >}}
  S = \{1,2,3,4,5\}
  {{< /math >}}

  “2 is an element of S; 7 is not an element of S”:
  {{< math >}}
  2 \in S,\qquad 7 \notin S
  {{< /math >}}

  **Properties**:  
  - A set is **not ordered**:
    {{< math >}}
    \{3,2,1\} = \{1,2,3\}
    {{< /math >}}
  - The elements of a set are **unique**:
    {{< math >}}
    \{4,4\} = \{4\}
    {{< /math >}}

  **Example** (English letters):  
  {{< math >}}
  A = \{a, b, c, d, \dots, x, y, z\}
  {{< /math >}}

---

- ## Common sets  

  Integers:  
  {{< math >}}
  \mathbb{Z}
  {{< /math >}}

  Positive integers:  
  {{< math >}}
  \mathbb{P}
  {{< /math >}}

  Rationals:  
  {{< math >}}
  \mathbb{Q} = \left\{\frac{a}{b} \,\middle|\, a,b \in \mathbb{Z},\; b \neq 0 \right\}
  {{< /math >}}

  (Here the vertical bar “\(|\)” means **“such that.”**)

  Reals:  
  {{< math >}}
  \mathbb{R}
  {{< /math >}}

  Complex numbers:  
  {{< math >}}
  \mathbb{C} = \{\, a + bi \mid a,b \in \mathbb{R},\; i^2 = -1 \,\}
  {{< /math >}}

  **Example** (finite custom set):  
  {{< math >}}
  P = \{\text{cats in Lowell}\}
  {{< /math >}}

---

- ## Subset:  
  “\(B\) is a subset of \(A\)” means every element of \(B\) is also an element of \(A\)”:
  {{< math >}}
  B \subseteq A \
