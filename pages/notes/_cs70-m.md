---
layout: note
permalink: /notes/cs70-m
---

# **CS 70 Midterm Review**

### Number Sets and Notation

**Subsets**

- **Intersection** = $A \cap B$ = all elements that are in A **and** B
- **Union** = $A \cup B$ = all elements in A **or** B
- **Disjoint** = no similar elements in a or B
- **Relative Complement** or **Set Difference** = $B - A$ or $B$ \ $A$ = set of elements in B but not A

**Significant Sets**

<img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-10-14%20at%2012.02.48%20PM.png" alt="Screen Shot 2021-10-14 at 12.02.48 PM" style="zoom:40%;" align="left"/>

### Propositions

- $P \implies Q \equiv \lnot P \or Q$
- $\lnot (P \implies Q) \equiv (P \and \lnot Q)$
- $\lnot (P \and \lnot Q) \equiv (\lnot P \or Q)$

### Proofs

**Types**

- Direct proof
  - assume P is true, then prove Q
- Proof by contraposition
  - assume notQ is true, then prove notP
- proof by contradiction
  - assume the claim (P --> Q) is false, then prove that it leads to a contradiction
- Proof by cases
  - split the claim up into cases which, when combined, encompass the entire domain of the claim
  - prove that the claim (P --> Q) holds true in every case

**Tips**

- prove something is true, try to find a counterexample and think about why you can't find one
- plug in the definition of any symbol or operator
- if and only if = prove that P--> Q and Q --> P

**Example**

Prove that there are no positive integer solutions that satisfy the equation: $x^2 - y^2 = 1$

- if we are trying to prove something is impossible, choose proof by contradiction

- solution:
  - assume that there are two positive integers
  - by factoring, $(x - y)(x + y) = 1$, so 
    - $(x - y) = 1$ AND $(x + y) = 1$ 
    - OR $(x - y) = -1$ AND $(x + y) = -1$

### Induction

**Steps**

- Base Case: prove that the proposition is true for P(0)
- Inductive Hypothesis: Assume that the P(k) is true (for some k)
- Inductive Step: Prove that P(k+1) is true using P(k)

**Key Idea**

- domino effect!
- if we prove the induction step, then P(0) => P(1), P(1) >= P(2), and so on

- ALWAYS reference the inductive hypothesis in your inductive step
  - how does it help the proof? CITE it!

**Strong Induction**

- In standard induction, assuming P(k) enables you to prove P(k+1)
  - assume some combo of P(1), P(2), ..., P(k) to prove P(k + 1)
  - this is still equivalent to simple induction!

**The Game of Nim**

- there are two non-empty piles of matches and two players, on each turn a player can remove any nonzero number of matches from any of the two piles
  - whoever removes the last match wins
  - What are the conditions under which each player can force a win?

==FILL IN==

**Interesting Sequence**

<img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-10-10%20at%2012.36.19%20PM.png" alt="Screen Shot 2021-10-10 at 12.36.19 PM" style="zoom:50%;" align="left"/>

*How to solve: strengthen hypothesis!*

- we can try to prove that $X_n = 2^n - 1$ for all natural numbers!
- Base Case
  - $X_0 = 0 = 2^0 - 1$, $X_1 = 1 = 2^1 - 1$
- Inductive Hypothesis
  - assume that this holds to $X_{n-1} = 2^{n-1} - 1$
- Inductive Step
  - <img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-10-10%20at%2012.41.07%20PM.png" alt="Screen Shot 2021-10-10 at 12.41.07 PM" style="zoom:50%;" align="left"/>

### Stable Matching

**Overview**

- two sides (i.e., not the roommates problem)
  - J = Jobs, C = Candidates
- ranked preference lists
- create stable pairing, aka no rogue couples
  - rogue couple (J, C) exists if both J and C prefer each other to their current partner

**Propose and Reject Algorithm**

- Job optimal and candidate pessimal
  - aka works in favor of the job preferences (prove this by contradiction)
  - a candidate could never get proposed to by their top choice job because the jobs could have been accepted by a diff candidate

- How it works:
  1. Every job proposes to their fav candidate who hasn't already rejected it
  2. Each candidate rejects all but their most preferred job and saves that job
  3. Each rejectd job removes the candidate who rejected it
- Once no job is rejected, and everyone has one proposal, they accept!

- Halts = n elements on 2 lists has finite combos
- Improvment Lemma
  - once a candidate gets proposed to, they will only ever stay the same or improve
  - Proof by Well-Ordering or Induction (on the days during the matching)

- Terminates with everyone paired by improvement lemma
- Produces stable pairings
  - uses improvement lemma: one rogue couple member rejected in favor of stable partner
- Rogue Couple = there is a man and a woman who prefer each other to their current partners

**Notes about SMP and Propose-and-Reject**

- for Stable Matching Problem
  - it helps to argue for rogue couples
  - does NOT prove anything for overall pairs
- Propose and Reject
  - use the algorithm with your proof, with induction or the well-ordering principle
  - well-ordering principle = there is always a "least element"

### Graphs

- **Walk** - A sequence of vertices and edges, where the edges connect the adjacent vertices in the sequence
- **Tour** - a walk with no repeated **edges** and ends where it began
- **Path** - a walk with no repeated **vertices** (and thus no repeated edges either)If a walk or path has $v_0 = v_n$, it is **closed**, else it is **open**
- **Cycle** = A walk with no repeated vertices except for $v_0 = v_n$

**Summary**

- Paths and Cycles **cannot** repeat edges; Walks and Tours **can** repeat edges.
- Paths and Walks start and end at **different** places; Cycles and Tours start and end at the **same** place.

|                                  | Can Repeat Edges | Cannot Repeat Edges |
| -------------------------------- | ---------------- | ------------------- |
| **Start and End at Diff Places** | Walk             | Path                |
| **Start and End at Same Places** | Tour             | Cycle               |

- **Hamiltonian walk** = a walk that visits each **vertex** in a graph exactly once. 
  - If it ends where it began (is closed), it’s a **Hamiltonian** **tour**
- **Eulerian walk** = visits every **edge** exactly once
  - If it ends at the same vertex, it's a **Eulerian tour**
- If it is a straight line, it is **both** a Eulerian and Hamiltonian walk!

**Graphs**

- in a disconnected graph, with k vertices in one group and n-k in the other, the maximum edges they can have is $\frac{k(k−1)}{2} + \frac{(n−k)(n−k−1)}{2}$

**Trees**

- every path has 2 leaves
- To translate a n-dimensional hypercube to a tree, trees must have $2^n-1$ edges

**Planarity**

- a graph is planar if you can draw it in a plane (draw it on paper without crossing edges)
- **Euler's Formula:** v + f - e = 2
- Planar graphs with v >= 3 satisfy Euler's formula ($v + f = e + 2$)
  - Euler's formula cannot verify of a graph is planar, because nonplanar graphs don't have faces!
- **Euler's Corollary** = all planar graphs satisfy *e* ≤ 3*v* - 6, but the converse is *not* true.
- **Kuratowski's theorem** = a graph is planar if and only if it doesn’t “contain” $K_5$ or $K_{3,3}$

**Hypercubes**

- generalization of cubes in higher dimensions
- $(n+1)$-dimensional hypercube generated by combining two n-dimensional hypercubes
  - 2 connected lines = square
  - 2 connected squares = cube
- each edge can only connect vertices that differ by one bit
  - x = 0000 and y = 1000 are neighbors
  - x = 000 and y = 101 are not neighbors

<img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-10-11%20at%204.55.13%20PM.png" alt="Screen Shot 2021-10-11 at 4.55.13 PM" style="zoom:50%;" />

### Modular Arithmetic

**Properties**

- in mod n space, all objects are in {0, 1, 2, ... , n - 1}
- DEFINITION: $a \equiv b$ (mod n) **iff** $a = kn + b$ for some integer k
- you can add, subtract, and multiple, but NOT divide
- for all integers x and y, there exists a, b where ax + by = d where d = gcd(x, y)
- when x, n are coprime
  - x has an inverse mod n
- when n is prime
  - all nonzero elements in mod n space have an inverse
  - this space is a field --> GF(n)

**Example 1**

==FILL IN==

**Extended Euclid Example**

==FILL IN==

**Fermat's Little Theorem (FLT)**

- huge powers? how to do this using mod
- if $a$ = # of colors and $p$ = length
  - there are $a^p - a$ number of strings, since we need to subtract the strings with only 1 type of $a$
  - each string can be rotated $p$ times to get the same string if the number is **prime**, so we know that $a^p - a$ is divisible by p
- modular arithmetic
  - $\frac{a^p}{p} = x$ remainder $a$
  - aka ==$a^p \equiv a$ (mod $p$)== 
- if p is prime, p does not divide a, and a > 0
  - $a^{p-1} \equiv 1$ (mod $p$)
  - By FLT, we have $a^x \equiv a^{x(mod (p-1))}$ (mod p)

**Chinese Remainder Theorem**

- Given *x =* 13 (mod 15), we can convert it to *x* = (3, 1) 
- Can we convert back from *x* = (3, 1) (mod 5, mod 3) to *x =* 13 (mod 15)?
- Solve:
  - mod 15 is a vector space
  - we need to convert (3, 1) to mod 15 space
  - use basis vectors 6 (0 mod 3, 1 mod 5) and 10 (1 mod 3, 0 mod 5)
    - ==look at how tf to dO tHIS==

**Chinese Remainder Theorem**

- first make sure that all nums we are mod-ing by (mod __) have a gcd = 1 when compared to each other
- 

### RSA

**Terminology**

- $N = pq$
- $E(x) = x^e (mod N)$
- $D(x) = x^d (mod N)$, $d = e^{-1} (mod (p-1)(q-1))$
- Public key: (N, e)
- Private key: d
- How it works
  - Alice calculates N by picking 2 prime numbers and multiplying them together to get N
  - then calculate $\phi (N)$ which we know is $(p-1)(q-1)$ which is how many numbers from 1 to N are relatively prime to $N$
    - whenever p and q are prime, the phi of $N = (p-1)(q-1)$
  - then she picks a public exponent $e$, which must be an odd number that does not share a factor with $\phi (N)$
  - find the value of the private key $d =(2 * (3016) + 1)/3 = 2011$ 
  - then Alice hides everything except (N, e)
  - send this to Bob as an open lock and let him put the message in
  - Bob calculates his encrpted message $m$ by doing $m^e$ (mod $N$) and sends it back to alice
  - Since Alice has her key d, she can do $m^d$ (mod N) = the original message!

**Example**

==practice this bruh==

### Polynomials

**Terminology**

- $p(x) = a_dx^d + a_{d-1}x^{d-1} … + a_0$
- If $a_d ≠ 0$, d is the degree of p(x)
- c is a zero of polynomial p if p(c)=0
- Can be mod q - GF(q)

**Properties**

- if p is not the zero polynomial and is of degree d, it has at most d roots
- a degree d polynomial is uniquely defined by d + 1 points
  - like $(x, p(x))$

**Interpolation**

- Say we have (d + 1) points of a polynomial p
- How do we construct a polynomial that fits these points?
- Let the points and evaluations be $(a_i, p(a_i))$, where i can go from 0 to d.

**Lagrange Interpolation**

==REVIEW AND PRACTICE THIS==

**Example**

- Two non-zero polynomials $p(x)$ and $q(x)$ of degree d over $GF(m)$ have r unique roots and s unique roots respectively.
  - What is the maximum number of unique roots for the polynomial $p(x)q(x)$? Answer may include d, r, and s.

- Answer: $min(m, r + s)$. There can’t be more than m roots, or any new roots that are not roots of p and q.

**Polynomial Applications**

- Secret sharing
- Error-correcting codes

**Secret Sharing**

- Say we have a secret that we need at least k people to be able recover.
- We know that we need $(d + 1)$ points to recover a polynomial of degree d.

==pick up at slide 145!==

### Counting

*Sampling k items from n choices:*

**Order matters**

- with replacement = $n^k$
- without replacement = $\frac{n!}{(n-k)!}$

**Order doesn't matter**

- with replacement = $(n + k - 1$ choose $n-1$ )
- without replacement = $\frac{n!}{(n-k)!k!}$

**Example**

- balls and bins! the dividers are the 1s and balls are 0s so u just have to figure out where to put the 1s!!!! THIS MAKES SENSE OMFG

### GCD Algorithm

- Algorithm:

  - If A = 0 then GCD(A,B)=B, since the GCD(0,B)=B, and we can stop.  

  - If B = 0 then GCD(A,B)=A, since the GCD(A,0)=A, and we can stop.  

  - Write A in quotient remainder form (A = B⋅Q + R)

  - Find GCD(B,R) using the Euclidean Algorithm since GCD(A,B) = GCD(B,R)

- $x - y < x/2$
  - so $y > x/2$
- if $gcd(x, y) = 1$ then a and b are coprime
- proves that the gcd algorithm's first argument decreases by a factor of two every other iteration
- How it works:
  - $gcd(m,n) = gcd(n, m$ mod $n)$
  - continue computing until there is a remainder of 0







