# Intro to RL 
*Introduction to reinforcement learning: the basics, bandits, and beyond, as well as some code to drive the point home.*

*By J. Blackburn - Sept 16, 2026.*

> [!NOTE] Written entirely without the use of AI.  
> Among more notes on RL, these are part of the [Perfect Notes Project](/weblog/notes)

---

## Basics 
**Reinforcement Learning (RL)** encompasses machine learning methods that involve 
*continual learning through interaction*. 

Unlike a typical supervised learning model, an RL **Agent** is not given a preprocessed and labeled dataset to 
do number-crunching on. 
Instead, it is simply deployed into an **Environment**, where it performs **Actions**, and recieves **Rewards**. 

The goal of an RL agent is to *maximize reward over time*, and it will learn to do so 
in different ways depending on the design of the agent and the nature of the problem.

## Bandits 
> [!NOTE] The one-armed bandit is a cute name for a slot machine because it has one arm (lever) and steals your money. 

**The Multi-Armed Bandit Problem** is a hypothetical slot machine with multiple levers, 
each with different chances (probability distributions) for yielding different amounts of money—in 
reinforcement learning, this hypothetical money is called **Reward**.

***With no information about the probability distributions hidden under each lever, maximize the reward gained from the bandit over such-and-such a number of lever pulls.***

To solve this problem in the general case, we need to define an **Agent** that makes a decision about which
lever to pull at each attempt. By 'solve' we really mean just finding a strategy that works well enough.

In the simplest version of the multi-armed bandit problem,
the best lever to pull is always the one with the highest **expected reward**. Thus, a good approach is 
to design an agent that keeps estimates of these expected rewards.


### exploration vs exploitation 
Since we don't start with any information about the levers,
there is a trade off between getting good estimates of the expected reward from each lever (**exploration**) 
and making use of the information already gathered about the levers 
in the form of our estimates (**exploitation**).

**The Epsilon-Greedy Agent** keeps a running estimate of the expected rewards and continually 
select levers with a large preference for the lever with the highest estimate.  
To ensure that the agent explores, there is a probability, epsilon ($\epsilon$), that the agent picks a lever at 
random, rather than picking its best estimate.

> [!NOTE]
> **Programming Exercise: the two-armed bandit**
>
> Test your understanding by implementing a two-armed bandit: 2 distinct probability distributions, 
> one with a higher expected value. Then create an epsilon-greedy agent that attempts to maximize reward 
> over a certain number of lever pulls. Play around with the distributions, epsilon, and number of turns.
>
>Which epsilon works best? Does the difference in expected rewards change the best epsilon? What about the variances? Can you implement the agent without keeping track of the total yield from each lever? How did you initialize your estimates?

### Reference Notebooks
1. basic_bandit_problem.ipynb - My solution to the programming exercise above.
2. ten_armed_testbed.ipynb - comparison of bandit solutions on a randomly generated 10-armed bandit.

## Beyond
Bandit problems help us explore basic reinforcement learning ideas, but are 
so simple that they miss a lot of **The Full Reinforcement Learning Problem**. 

To begin to approach the 
full problem, understanding **Markov Decision Processes** is essential. It's also useful to see 
how **Dynamic Programming** helps us implement learning agents. 

From there, you can learn about conventional
approaches to RL such as **Monte Carlo Methods** and **Temporal Difference Learning**. 

These, 
along with our bandit agents, are called **Tabular Solution Methods**. In contrast, **Approximate Solution Methods** are less precise but are more practical and can be applied to more general problems. 

