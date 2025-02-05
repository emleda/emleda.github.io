---
layout: post
title: Basic Probability
description: >
  Deep dive into the fundamentals of understanding probability.
sitemap: false
hide_last_modified: true
---

Probability has never felt intuitive to me, however in undergoing a degree in Data Science and Statistics, it must become intuitive. I have compiled a few key areas of probability and counting to serve as guiding principles when dealing with probability.

# Key rules

## Binomial Distributions
- Requirements
	- Always with replacement
	- Must have binary outcomes for each trial
	- Must know number of trials
	- Probability does not change over time
- Data
	- $$n$$: The number of trials
	- $$p$$: Probability of 1 success
	- $$1-p$$: Probability of 1 failure
	- $$x$$: Number of successes 
- Parameters
	- EV of Sum: $$n\times p$$
	- SE of Sum: $$\sqrt{n\times p \times (1-p)}$$
- Formula  
	$$\begin{aligned}
	  P(X=x) ={n \choose x}p^x(1-p)^{n-x}
  \end{aligned}$$   
	- $$p^x(1-p)^{n-x}$$: Say that we are rolling a dice. We want to know the probability that we roll '3' twice out of 5 rolls. This part of the equation tells us, what is the chance that we win (roll 3) 2 times and fail 3 times. It is like saying $$(P(succeed) \times 2)\times(P(fail) \times 3)$$. But, this only tells us the chance of it happening in one way: succeed, succeed, fail, fail, fail. Now we need to find the probability for all possible combinations.
	- $${n\choose x}$$: See *Counting - Combinations* for more explanation - this gives the total number of ways for $$x$$ successes out of $$n$$ trials. When we multiply the probability we calculated in the step above, then we have the probability of this combination of events happening, multiplied by the number of ways (ordering) it can happen. The formula is $$\frac{n!}{(n-x)!x!}$$.


## Counting

With counting, we can find how many ways a set of objects can be ordered. For example, you can find how many possible poker hands. 
### Combination vs Permutation

A combination is where order matters, and a permutation is where it does not. So when you pick fruit from a bowl, you don't care if you get an apple or banana first, this is a *combination*. If you are entering a code, it has to be the right order, so it will be a *permutation*. 

This is a very simple definition but I find it can be difficult to apply in complex probability questions. A way I've found to think of it is that permutations are combinations with more information. 

Consider that you are picking 2 letters from 'a', 'b', 'c'. How many *combinations* can we have? 'ab', 'bc', 'cb'. But if we want to know how many *permutations*, then we can take the combinations as a blueprint and see how many ways those combinations can be arranged.
- 'ab' -> 'ab', 'ba'
- 'ac' -> 'ac', 'ca'
- 'bc' -> 'bc', 'cb'

So there will be 3 combinations, that when we expand them, become 6 permutations.

### How do we count?

#### Permutations
##### With Replacement

Imagine you are guessing someone's bank pin so you can buy a beautiful cream Abarth. The pin is 3 numbers long and only includes 0 and 1. From its nature, we know the order is important and the options are repeated. We also know that there are 2 options, and 3 times to choose between those 2 options. 

Let's use a decision tree to walk through:

![image](/assets/img/blog/perm_wrep.jpg)

First, you have 2 choices: 0, 1. Then, you have another 2 choices for the first 0 and 1, so that is $$2\times 2= 4$$ choices. Then for each of those 4 choices, you have another 2, so it is $$2\times2\times2$$. To generalise you have $$2^3$$ or $$n^r$$ where $$n$$ is the number of choices and $$r$$ is the number of trials.

Let's try an example, imagine you are picking a password that must be 6 letters long, can can only contain letters of the alphabet (26 letters). There are 26 choices at each trial, and 6 stages. So, there will be $$26^6=308915776$$ possible passwords.
##### Without Replacement

Permutations without replacement are similar to with replacement, but each time you make a choice, the number of options reduces by one. 

Let's take a debating team speaking order as an example. The debating team has 5 members. They enter a competition where 3 people are chosen to speak. How many different speaking orders can they have?

The first time, you have 5 choices, then 4 choices, then 3 choices. So instead of $$5^3$$, we need to use the factorial function. This gives us $$5\times4\times3\times2\times1$$. But this will give us the total number of permutations if **all** members speak, while only 3 members can speak. So we need to divide by the factorial of people who can't speak to cancel out those permutations. 2 people cannot speak so we have $$\frac{5\times 4 \times 3 \times 2 \times 1}{2 \times 1} = 5\times4\times3$$.

So we have $$\frac{n!}{(n-r)!}$$ where $$n$$ is the number of options at the beginning and $$r$$ is the number of trials.

#### Combinations

##### With Replacement

The formula is $$\frac{(r+n-1)!}{r!(n-1)!}$$

##### Without Replacement

Imagine you have 5 candidates: **A**my, **B**ob, **C**indy, **D**erek, **E**mily) and you have 3 positions to offer. How many combinations can we have?

Recall that combinations are just reduced permutations so let's start by considering the permutations: We have $$\frac{5!}{2!} = 60$$ possible permutations of hires. This includes duplicates, but how many duplicates are there? Well, how many different ways can we arrange the same 3 letters? We can arrange it $$3!=6$$ times. So, to get rid of the duplicates we need to remove $$r!$$ options. 

In our example, we now have $$\frac{5!}{2!}*\frac{1}{3!} = \frac{5!}{3!2!}$$, or $$\frac{n!}{r!(n-r)!}$$.

This is the same as the binomial coefficient $$n \choose r$$ - it gives the total number of possible combinations without replacement. 


### Summary

|             | With Replacement           | Without Replacement     |
|:-----------:|:--------------------------:|:-----------------------:|
| Permutation | $$n^r$$                    | $$\frac{n!}{(n-r)!}$$   |
| Combination | $$\frac{r+n-1}{r!(n-r)!}$$ | $$\frac{n!}{r!(n-r)!}$$ |
{:.stretch-table}
