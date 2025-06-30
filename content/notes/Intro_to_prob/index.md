---
title: Introduction to Probability
date: 2025-05-24
tags:
    - Mathematics
    - Self study
    - MIT Open Course Ware
---
My learning note of the course Introduction to Probability by MIT \
## Lecture 1
There is a few axioms (rules) in probability but they all very powerful

### Sample space
There are basic steps to solve a probability problem:
- Discribe every possible outcome (as a list or set)
- Discribe the beliefs of outcome (by the axioms)

The list (set) of outcome could be:
- Mutudly exclusive: Only 1 possible outcome
- Collectively exhaustive: > 1 possible outcome 

And it must be at the right granularity


**Example of the right granylarity** \
Calculate the probability of head or tail when flipping the coins based on the weather ???

### Discrete/finite sample space example:
**Discrete** \
2 rolls of the tetrehedrid dice, since there is a specific (finite) number of outcome when we roll the dices -> the sample space is discrete.

We can visualize it by 2 ways

table 1 here

graph 1 here

### Continous sample space

It is a space that have infinity possible outome and the outcome is the the range of the sample space

unit square here

### Probability Axioms

What is the probability of 2 points his the same spot in unit square? \
Close to 0 because there are unlimited points in the unit square

img here

But we can calculate the probability of one point that hit a specific area

image here

**Even:** a subset of sample space
- probability is assign to events
- probability is range from 0 - 1
### Axioms

1. **Non-negativity**

P(A) \geq 0
{{< math >}}

2. **Normalization**
P(S) = 1
{{< math >}}

3. **Additivity**  
If \( A \cap B = \varnothing \), then  
{{< math >}}
P(A \cup B) = P(A) + P(B)
{{< math >}}


