Probability has never felt intuitive to me, however in undergoing a degree in Data Science and Statistics, it must become intuitive. I have compiled a few key areas of probability and counting to serve as guiding principles when dealing with probability.

### Key rules
### Binomial Distributions
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
	- EV of Sum: $$n\cdot p$$
	- SE of Sum: $$\sqrt{n\cdot p \cdot (1-p)}$$
- Formula  
	$$\begin{aligned}
	  P(X=x) ={n \choose x}p^x(1-p)^{n-x}
  \end{aligned}$$   
	- $$p^x(1-p)^{n-x}$$: Say that we are rolling a dice. We want to know the probability that we roll '3' twice out of 5 rolls. This part of the equation tells us, what is the chance that we win (roll 3) 2 times and fail 3 times. It is like saying $$(P(succeed) \cdot 2)\cdot(P(fail) \cdot 3)$$. But, this only tells us the chance of it happening in one way: succeed, succeed, fail, fail, fail. Now we need to find the probability for all possible combinations.
	- $${n\choose x}$$: See *Counting - Combinations* for more explanation - this gives the total number of ways for $$x$$ successes out of $$n$$ trials. When we multiply the probability we calculated in the step above, then we have the probability of this combination of events happening, multiplied by the number of ways (ordering) it can happen. The formula is $$\frac{n!}{(n-x)!x!}$$.


### Counting
#### Combinations
#### Permutations
