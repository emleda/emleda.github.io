---
layout: post
title: Worked Probability Questions
description: >
  Worked examples to demystify counting and probability.
sitemap: false
hide_last_modified: true
---
 
Let's go through a few questions together to check our understanding! 

## What is the probability of getting 3 of a kind in a 5 card poker hand?

First, let's take an overall view of what the question is really asking, which is to find:

$$P(\text{3 of a kind}) = \frac{\text{Number of ways to get 3 of a kind}}{\text{Total number of possible hands}}$$

The numerator is the more complex part, so we can start there. We want to know: how many ways can I get 3 of a kind. First, collate what we know: 
- A 3 of a kind means: Cards 1-3 must be from the same rank, then card 4 has to be from a different rank, and card 5 has to be from another different rank.
- One rank has 4 cards, and each deck has 13 ranks.

So, starting with just one rank, how many combinations of 3s of a kind can we get from one rank? $$\binom{4}{3} = 4$$. 

One thing to note here: there are actually 4 unique cards (Aces, Clubs, Spades, Hearts). So, when there are 4 combinations, we mean that there can be (Ace, Club, Spade), (Ace, Spade, Heart), (Ace, Club, Heart) and (Club, Spade, Heart). We do not care about order, so for example (Ace, Spade, Heart) is the same (Ace, Heart, Spade). In a different case, where all cards were completely the same, then there would only be 1 way to draw 3 from the same rank: (4,4,4). 

So, if there are 4 ways to get 3 of a kind from one rank, and there are 13 ranks, then the amount of ways to get 3 of a kind in the first 3 cards is $$13\times \binom{4}{3}$$. To rephrase, we have 4 ways to get 3 aces, then 4 ways to get 3 1s and so on, so we can add them all together for the total. 

Then, we move to the remaining 2 cards. We know that the fourth card cannot from be the same rank as the first 3, so there are only 12 ranks that we can draw from. With four in each rank, there are $$12\times 4=48$$ different cards from which we can choose 1. So there are 48 choices for the fourth card. The finally card needs to be from another different rank, so there are now 11 ranks to choose from. There are $$11\times 4=48$$ different ways to pick the final card.

So, the number of ways to get 3 of a kind is equal to $$13\times \tbinom{4}{3}\times 48 \times 44$$. 
 
For the denominator, calculate the total number of possible hands which, because it is a combination, is simply $$52 \choose 5$$.

Finally, combine it all, 

$$\begin{aligned}
P(\text{3 of a kind}) = \frac{13 \binom{4}{3} \times 48 \times 44}{\binom{52}{5}} \approx 0.04
\end{aligned}$$

## If you shuffle a standard deck of 52 plaing cards, what is the probability that the first 4 cards are aces, the next 4 are 1s, the next 4 2s and so on, until the last 4 cards are kings?

In this case, we care about the order. So, what we need to find is 

$$\begin{aligned}
P(\text{This permutation}) = \frac{\text{Ways to get this permutation}}{\text{Possible permutations}}
\end{aligned}$$

We'll start with the numerator. The possible permutations of getting 4 of the same card in a row are $$4!= 24$$. We need this to happen for every rank, so we will multiply each rank like this: $$4! \times 4! \times 4!... = (4!)^{13}$$. 

Next, calculate the possible permutations of a deck of cards, which is simply $$52!$$.

Finally, combine together:

$$\begin{aligned}
P(\text{This permutation}) = \frac{(4!)^{13}}{52!} \approx 1\times 10^{-50}
\end{aligned}$$

## If I flip 10 coins, what is the probability that exactly 7 are heads?

This is a classic binomial probability question. We can use the binomial formula: 
$$\begin{aligned}
\binom{n}{x} \times p^n\times (1-p)^{n-p}
\end{aligned}$$


We have $$n$$, the number of trials which is 10. Then $$x$$, the number of successes which is 7. Then we have $$p$$, the probability of success or heads which is 0.5. All that's left is to substitute in our values:
$$\begin{aligned}
P(7 Heads) = \binom{10}{7} (0.5)^{7}(0.5)^{3} \approx 0.11
\end{aligned}$$
