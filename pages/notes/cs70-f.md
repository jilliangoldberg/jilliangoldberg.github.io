---
layout: note
permalink: /notes/cs70-f
---

# **CS 70 Final Review**

### Countability

**Definition**

- a set is **countable** if you are able to match every element up with the set of positive integers $$\N$$
- in other words, if there is a bijection between $$S$$ and $$\N$$

**Bijections**

- **Injection** = $$f$$ maps distinct inputs to distinct outputs
- **Surjection** = $$f$$ "hits" every element in range, in other words: $$(\forall y \exist x)(f(x) = y)$$
- **Bijection** = both! every $$x$$ maps to a distinct $$y$$

<img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-12-14%20at%204.32.36%20PM.png" alt="Screen Shot 2021-12-14 at 4.32.36 PM" style="zoom:40%;" />

**Cardinality**

- when two sets have the same size, which can be found by demonstrating a pairing between elements in two sets
- shows a bijection

**Ways to Prove Countability**

- **On a graph:** demonstrate that you are able to connect all the dots in an "endless" or "infinite" way.

  <img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-12-14%20at%204.36.00%20PM.png" alt="Screen Shot 2021-12-14 at 4.36.00 PM" style="zoom:50%;" align="left"/>

- **In a set:** use diagonalization!

  - prove that for an infinite amount of numbers, you can always find one number that you "forgot" to list if you go diagonally in the list and differ from that number each time.

  <img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-12-14%20at%204.38.22%20PM.png" alt="Screen Shot 2021-12-14 at 4.38.22 PM" style="zoom:50%;" align="left"/>

- so if you have some real number $$s = 0.6570...$$ by adding $$1$$ to every diagonalized digit, then we would know that we "forgot" to include it, since this contradicting number would be infinitely different than any number we can find with $$f(x)$$

**Uncountable Sets**

- compare a set of numbers to a mapping of an uncountable set, such as the real numbers $$\R \in [0,1]$$ 

- Ex: **the Cantor set**

  - defined by removing the middle third of line segments infinitely many times

    <img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-12-14%20at%204.58.32%20PM.png" alt="Screen Shot 2021-12-14 at 4.58.32 PM" style="zoom:50%;" align="left"/>

  - eventually, as you iterate this pattern an infinite amount of times, you will get a set of isolated points with **no more intervals**

    <img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-12-14%20at%205.01.16%20PM.png" alt="Screen Shot 2021-12-14 at 5.01.16 PM" style="zoom:50%;" align="left"/>

  - this can be broken down into ternary numbers, where you can say that for every number, it can be represented by $$[0, 1, 2]$$, such as $$0.02020022...$$

  - if you divide this by two, you get a binary representation of the interval from $$[0,1]$$, which represents the set of real numbers between $$0$$ and $$1$$, thus, the Cantor set is **uncountable**

**Power Sets**

- if $$S$$ is a set, the power set of $$S$$, $$\mathcal{P}(A)$$, is the set of all subsets of $$S$$

  - Ex: $$S = \{1,2,3\}$$, so $$\mathcal{P}(S) = \{\{\},\{1\},\{2\},\{3\},\{1,2\}, \{1,3\},\{2,3\},\{1,2,3\}\}$$

  - if the size of $$S = k$$ is finite, then $$\mathcal{P}(S) = 2^k$$

  - $$|\mathcal{P}(\N)| > |\N|$$

  - says that the cardinality (size) of the power set is greater than the cardinality of N

  - even if the set $$\N$$ is countable, the power set $$\mathcal{P}(\N)$$ is uncountable because we can use diagonalization to always find a subset we forgot by finding the contradiction to the set that we've mapped out.

    <img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-12-14%20at%205.11.43%20PM.png" alt="Screen Shot 2021-12-14 at 5.11.43 PM" style="zoom:50%;" align="left"/>

  - using binary strings, we can use diagonalization to flip the bits, in order to find the $$b$$ bit that we infinitely missed in our set

### Computability

**Self-Replicating Programs**

- **Quine** = a program that can print itself
  - Ex: in English pseudocode:

<img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-12-14%20at%205.39.59%20PM.png" alt="Screen Shot 2021-12-14 at 5.39.59 PM" style="zoom:50%;" align="left"/>

**Recursion Theorem**

- used to explain how we generate quines!

- given any program $$P(x, y)$$, we can always convert it to another program $$Q(x)$$, such that $$Q(x) = P(x, Q)$$
  - in other words, $$Q$$ behaves exactly as $$P$$ would if its second input is the description of the program $$Q$$
  - $$Q$$ = the "self-aware" version of $$P$$, where $$Q$$ has access to its own description

**The Halting Problem**

- there **does not exist** a program that can tell us if a program halts on an input x (**uncomputable**)

  <img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-12-14%20at%205.48.49%20PM.png" alt="Screen Shot 2021-12-14 at 5.48.49 PM" style="zoom:50%;" align="left"/>

- when solving a problem, we are trying to prove the contradiction that there exists a program $$TestHalt$$

```python
def Turing(P)
	if TestHalt(P,P) = “yes” then loop forever
	else halt
```

- if a program P when given P as an input halts, then Turing(P) loops forever

  - otherwise, Turing(P) halts

  <img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-12-14%20at%205.54.56%20PM.png" alt="Screen Shot 2021-12-14 at 5.54.56 PM" style="zoom:50%;" align="left"/>

- we can say that Turing either Halts or Loops forever, but by diagonalization, we can find a program that contradicts every entry in the mapping of the $$(i, j)^{th}$$ entries
  - thus, the behavior of Turing is different from that of $$P_n$$, since it will contradict itself, because if TestHalt(P, P) returns "yes" then that will loop forever, but contradict the meaning of the original test, since the programs should be telling us that the test *did* halt and stop looping
  - therefore, our list of $$P_n$$ "forgot" to list Turing as one of the programs with results H or L, so we can conclude that TestHalt does not exist and the Halting Problem cannot be solved!



### Intersection of Events

**Union of Events**

- **Principle of Inclusion-Exclusion** = used when events are independent, but not disjoint
  - <img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-12-07%20at%2010.19.16%20PM.png" alt="Screen Shot 2021-12-07 at 10.19.16 PM" style="zoom:50%;" align="left"/>
  - basically starts by summing all the event probabilities, then *subtracts* the probabilities of all pairwise intersections, then *add* back in the probabilities of all three-way intersections
- **Ex:** Vegas dice rolling!

<img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-12-07%20at%2010.22.54%20PM.png" alt="Screen Shot 2021-12-07 at 10.22.54 PM" style="zoom:50%;">

- usually too computationally-expensive
- Just look at the first term!
- **Mutually exclusive events** = if $$A_1, ..., A_n$$ are mutually exclusive, then:
  - <img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-12-07%20at%2010.33.21%20PM.png" alt="Screen Shot 2021-12-07 at 10.33.21 PM" style="zoom:50%;" align="left"/>
- **Union Bound** = if we add up $$P[A_i]$$, it will always be equal to or an overestimate of the probability of the union
  - <img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-12-07%20at%2010.35.15%20PM.png" alt="Screen Shot 2021-12-07 at 10.35.15 PM" style="zoom:50%;" align="left"/>

### Random Variables

Random variables are defined by two things:

1. the set of values it can take
2. the probability with which it takes on the values

$$E[X] = $$ mean/expectation of the distribution

$$Var(X) = E[X^2] - E[X]^2$$

#### Bernoulli Distribution

- $$X$$ ~ $$Bernoulli(p)$$

<img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-12-07%20at%2010.37.44%20PM.png" alt="Screen Shot 2021-12-07 at 10.37.44 PM" style="zoom:50%;" align="left"/>

##### Binomial Distribution

- $$X$$ ~ $$Bin(n, p)$$
  - where n is the number of trials and p is the probability of something occuring
- $$\sum_{i=0}^n P[X = i]=1$$
- implies that $$\sum_{i=0}^n {n \choose i} p^i (1-p)^{n-i}=1$$
- which basically means that if you are choosing $$i$$ cases to succeed, you would need to find how many different ways there are to choose i out of n, find the p probability i times, and the (1-p) probability the remainding times out of n

<img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-12-07%20at%208.20.01%20PM.png" alt="Screen Shot 2021-12-07 at 8.20.01 PM" style="zoom:40%;" align="left"/>

- **Ex:** Error correction problem
  - we want to encode $$n$$ packets into $$n + k$$ packets, how do we choose k?
  - model each packet getting lost with probability $$p$$ and the losses are indep, then if we transmit $$n + k$$ packages, the number of packets received is a random variable $$X$$ with binomial distribution
    - $$X$$ ~ $$Bin(n + k, 1 - p)$$
  - <img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-12-07%20at%2010.44.12%20PM.png" alt="Screen Shot 2021-12-07 at 10.44.12 PM" style="zoom:50%;" align="left"/>

**Hypergeometric Distribution**

- $$Y$$ ~ $$Hypergeometric(N, B, n)$$
  - N = the total number of items
  - B = the number of specific items
  - n = the number out of B that you want to pick
- picking a certain number of items **without replacement**
- take into account what we want and don't want
- <img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-12-07%20at%2010.50.33%20PM.png" alt="Screen Shot 2021-12-07 at 10.50.33 PM" style="zoom:50%;" align="left"/>
- **Ex**: if we have a bucket with 30 red balls and 70 blue balls
  - now there are $${100 \choose 20}$$ ways to choose 20 balls since there is no replacement anymore
  - <img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-12-07%20at%202.28.23%20PM.png" alt="Screen Shot 2021-12-07 at 2.28.23 PM" style="zoom:50%;" align="left" />

**Geometric Distribution**

- $$X$$ ~ $$Geometric(p)$$
  - p = probability of the event happening
- number of trials until a certain event happens
  - Ex: how many tosses before the first head appears, how many picks until we get a red ball
- $$P[X = i] = (1 - p)^{i-1}p^1$$
  - since $$i$$ trials have been unsuccessful and only the most recent trial has probability $$p$$ of being successful
- $$E[X] = \sum_{i=1}^\infin i \times P[X=i] = p\sum_{i=1}^\infin i(1 - p)^{i-1} = \frac{1}{p}$$
- $$Var(X) = \frac{1-p}{p^2}$$
- the **Tail Sum Formula** is used to say that the expectation of X will always be the sum of all probabilities where X is greater than or equal to i, or $$E[X] = \sum_{i=1}^\infin P[X \geq i]$$
  - this simplifies the **expectation** to be $$E[X] = \frac{1}{p}$$

**Poisson Distribution**

- $$X$$ ~ $$Poisson(\lambda)$$
  - $$\lambda$$ = average number that an event happens per a unit of time
  - Ex: number of clicks of a Geiger counter, how many times the bus comes within the hour, how many fish are caught in an hour
- $$P[X=i] = \frac{\lambda^i}{i!}e^{-\lambda}$$
- $$E[X] = \lambda$$
- $$Var(X) = \lambda$$
- The **sum of independent poisson random variables** becomes a bell curve as $$\lambda$$ increases
  - if we have $$X$$ ~ $$Poisson(\lambda)$$ and $$ Y$$ ~$$ Poisson(\mu)$$, then $$X + Y$$ ~ $$Poisson(\lambda + \mu)$$
  - a poisson distribution is the limit of the binomial distribution

**Exponential Distribution**

- $$X$$ ~ $$Exp(\lambda)$$
  - $$\lambda$$ is the success rate per unit of time
- $$E[X] = \frac{1}{\lambda}$$
- $$Var(X) = \frac{1}{\lambda^2}$$
- an event can happen at any time, what is the time until the event happens?
  - Ex: a system to fail, a clock to ring, a train to reach the station

<img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-12-14%20at%202.21.03%20PM.png" alt="Screen Shot 2021-12-14 at 2.21.03 PM" style="zoom:50%;" align="left"/>

continuous version of the geometric distribution

- since the exponential distrubution is time-dependent, it's like taking a geometric distribution and performing 1 trial every $$\delta$$ seconds, and our success probability is $$p = \lambda\delta$$, since the first success will be at the end of the time it takes for the event to occur, which is the success rate per unit of time * the number of trials, or $$\lambda\delta$$.

**Normal Distribution (Gaussian Distribution)**

- $$X$$ ~ $$N(\mu,\sigma^2)$$

  - $$\mu$$ is the mean/expectation

  - $$\sigma^2$$ is the variance with the pdf:

    <img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-12-14%20at%202.43.49%20PM.png" alt="Screen Shot 2021-12-14 at 2.43.49 PM" style="zoom:50%;" align="left"/>

- in the special case that $$X$$ ~ $$N(0, 1)$$, this means that X has a **standard normal distribution**
- **Standard Normal Distribution Lemma**
  - if $$X$$ ~ $$N(\mu,\sigma^2)$$, then Y = $$\frac{X - \mu}{\sigma}$$ ~ $$N(0,1)$$
  - equivalently, $$X$$ is just $$X = \sigma Y + \mu$$, which means that X is translated into a standard normal distribution ($$Y$$) just by shifing the origin to the expectation/mean ($$\mu$$) and scaling by the standard deviation ($$\sigma$$)

- The **sum of independent normal random variables** **are also** **normally distributed!**

  - Since we know that $$X$$ and $$Y$$ are independent, the joint density of $$(X, Y)$$ is $$f(x,y) = f(x)f(y) = \frac{1}{2\pi} e^{\frac{x^2+y^2}{2}} .$$

  - Therefore, for any constants $$a, b \in \R$$, the random variable $$Z = aX + bY$$ is normally distributed:

    - $$\mu = E[Z] = a\mu_x + b\mu_y$$
    - $$\sigma^2 = Var(Z) = a^2\sigma_x^2 + b^2\sigma_y^2$$

  - **Key Observation:** the function is rotationally symmetric around the origin (like a dome), which means that $$f(x,y)$$ only depends on the value $$x^2 + y^2$$, which is the distance of the point $$(x, y)$$ from the origin

    <img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-12-14%20at%203.02.14%20PM.png" alt="Screen Shot 2021-12-14 at 3.02.14 PM" style="zoom:20%;" align="left"/>

- this can also be thought of as $$f(T(x, y)) = f(x, y)$$ where $$T$$ is any rotation of the plane $$\R^2$$ about the origin
  - this would follow that for any set of $$A \subseteq \R^2$$, we have $$P[(X,Y) \in A] = P[(X,Y) \in T(A)]$$, which means that the probability of $$(X, Y)$$ in any part of the plane is the same as the probability of $$(X, Y)$$ in any part of the joint normal distribution.
  - if we take any rotation in $$\R$$, we will still get that the probability is the same in $$t$$ vs $$A$$, so we know that the boundary line $$ax + by = t$$ lies at a distance $$d = \frac{t}{\sqrt{z^2+b^2}}$$
- therefore, Z has the same distribution as $$\sqrt{a^2 + b^2}X$$ and the expectation and variance are combinations of the two distributions. 

### Multiple Random Variables and Independence

**Joint Distribution**

-  the collection of values $$\{((a,b),P[X = a,Y = b]) : a \in A , b \in B\}$$, 
  - A = the set of all possible values taken by X
  - B = the set of all possible values taken by Y
- Sum over B to find the marginal distribution for X
  - $$P[X = a] = \sum_{b \in B} P[X=a, Y=b]$$
  - independent if you can multiply them together to find the joint distribution

### Expectation 

- $$E[X] = \sum_{a \in A} a \times P[X=a]$$
- basically sum over all the values of A * P(a)
- basically the mean or average

**Linearity of Expectation**

For any two random variables X and Y on the same probability space:

- $$E[X + Y] = E[X] + E[Y]$$

For any constant c

- $$E[cX] = c \times E[X]$$

### Quick Facts

- graphs
  - when talking about components, it means the number of collections of nodes
  - if you have a graph with n vertices with exactly one cycle and m edges, the number of connected components is $$n - m + 1$$
- law of large numbers
- central limit theorem













### Picking k items

**exact number with replacement**

- we have to take into account what we want AND what we don't want
- **Ex**: if we have a bucket with 30 red balls and 70 blue balls
  - pick 20 balls with replacement, what is the probability of getting exactly k red balls
  - <img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-12-07%20at%202.20.09%20PM.png" alt="Screen Shot 2021-12-07 at 2.20.09 PM" style="zoom:50%;" align="left"/>
  - you can pick any 20 balls $$100^{20}$$ different ways
  - if you want to k out of 20 to be red, then you do $${20 \choose k} * 30^k * 70^{20-k}$$ 
  - aka you want the exact number so you have to specify what the other 20-k balls will be

**exact number without replacement**

- still take into account what we want and don't want
- **Ex**: if we have a bucket with 30 red balls and 70 blue balls
  - now there are $${100 \choose 20}$$ ways to choose 20 balls since there is no replacement anymore
  - <img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-12-07%20at%202.28.23%20PM.png" alt="Screen Shot 2021-12-07 at 2.28.23 PM" style="zoom:50%;" align="left"/>

**at least one value is observed more than once**

- take into account the values already seen by k roll
- **Ex:** roling a 6-sided dice 5 times
  - there are $$6^5$$ ways to get a value since there is "replacement"



### Vocab

- mean = $$\mu$$
- variance = $$\omicron$$
- Geometric Random Variable 
  - X ~ Geom(p)
    - where X is the number of trials UNTIL something occurs with p probability
  - $$P[X=i] = (1-p)^{i-1}p^1$$$$

- Binomial Random Variable
  - X ~ Binom(n, p)
    - where n is the number of trials and p is the probability of something occuring
  - $$\sum_{i=0}^n P[X = i]=1$$
  - implies that $$\sum_{i=0}^n {n \choose i} p^i (1-p)^{n-i}=1$$
  - which basically means that if you are choosing $$i$$ cases to succeed, you would need to find how many different ways there are to choose i out of n, find the p probability i times, and the (1-p) probability the remainding times out of n
- <img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-12-07%20at%208.20.01%20PM.png" alt="Screen Shot 2021-12-07 at 8.20.01 PM" style="zoom:40%;" align="left"/>

### to add

- Law of large nums = as u sample more, it will get closer to the expectation

- Central Limit theorem = if we take a group of samples, the expection stays the same but the variance will decrease by a factor of n

  - the distribution of the *sample average* $$\frac{S_n}{n}$$
  - $$Var(cX) = \frac{1}{c^2} Var(X)$$
  - $$E[cX] = \frac{1}{c} E[X]$$
  - <img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-12-15%20at%201.24.28%20AM.png" alt="Screen Shot 2021-12-15 at 1.24.28 AM" style="zoom:50%;" align="left"/>
  - the power of the CLT is that you can take a non-normal distribution and retrieve a normal-looking average
  - standard deviation is the sqrt of the variance

- there are $$\frac{m(m-1)}{2}$$ possible pairs for $$m$$ keys

- a PDF has to satisfy the following cases:

  1. f is non-negative: f(x)
  2. The total integral of f is equal to 1: $$\int_{-\infin}^\infin f(x)dx = 1$$.

  <img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-12-15%20at%201.43.08%20AM.png" alt="Screen Shot 2021-12-15 at 1.43.08 AM" style="zoom:50%;" align="left"/>

  - basically the cdf is the riemann sum; the distribution THUS FAR until a certain point. the pdf is the derivative of this, aka how fast the probability is growing.

- a CDF has to satisfy the following cases: 

  <img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-12-03%20at%206.29.57%20PM.png" alt="Screen Shot 2021-12-03 at 6.29.57 PM" style="zoom:50%;" align="left"/>

  - find the PDF by taking the derivative of the CDF
  - <img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-12-15%20at%201.44.49%20AM.png" alt="Screen Shot 2021-12-15 at 1.44.49 AM" style="zoom:50%;" align="left"/>

- <img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-12-15%20at%201.45.37%20AM.png" alt="Screen Shot 2021-12-15 at 1.45.37 AM" style="zoom:50%;" />

- <img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-12-15%20at%201.45.53%20AM.png" alt="Screen Shot 2021-12-15 at 1.45.53 AM" style="zoom:50%;" />

- <img src="/Users/jilliangoldberg/Library/Application%20Support/typora-user-images/Screen%20Shot%202021-12-15%20at%201.46.17%20AM.png" alt="Screen Shot 2021-12-15 at 1.46.17 AM" style="zoom:50%;" />

- a joint density function makes a surface, and the integral of that is the *volume*

- 

- covariance and correlation























