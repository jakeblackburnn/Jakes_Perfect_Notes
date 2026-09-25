# Intro to RL 


## Bandits 
The one-armed bandit is a cute name for a slot machine because it has one 'arm' (lever) steals your money. 
The multi-armed bandit problem is a hypothetical slot machine with multiple levers, each with its own probability distribution that determines 
the chances of losing, hitting small, and hitting big, and this problem is a simple model problem for illustrating RL in practice.  

the problem: with no information about the probability distributions hidden under each lever, maximize the reward gained from the bandit over such-and-such a number of tries. 

the RL solution: keep a running estimate of the expected value of the reward for each lever (the average reward yielded across tries) and continually 
select levers with some preference for the lever with the highest estimated expected reward.  

### exploration vs exploitation 
If we knew the expected rewards for each lever perfectly, we could simply select the most rewarding lever each time, but since we don't, 
there is a trade off between getting good estimates for each lever (exploration) and making use of the information already gathered about the levers 
in the form of our estimates (exploitation)

### the model 
We can model a k-armed bandit easily by creating k probability distributions with pythons random package. 
Our RL model then just needs to track the running averages for each distribution, and define some criteria for selecting one at each try. 
the conventional, basic criteria used in RL is to select the argmax of the expected values (exploitation) some large percentage of the time
and to select randomly from the other distributions the rest of the time (exploration).
