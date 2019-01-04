
[image1]: ./result.png "ResultPlot"

## Description
The goal is to train 2 RL agents to play tennis. Each player want to keep the ball in play.

## Environment
The environment is similar as Unity ML-Agents Tennis environment, but not identical. https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#tennis

## Algorithm
There are some key features of the Tennis project.
- Multiple Agents
- Continuous Action Space

Due to the complexity of this project, the value-based method such as Deep QNetwork is not suitable anymore. The policy-based methods is a good choice. The policy-based method has some advantage, such as continuous action spaces, stochastic policies, and simplicity. 

The algorithm used in this project is Multi-Agent Deep Deterministic Policy Gradient(MADDPG) is extended from DDPG. Here are the papers refered to.
https://arxiv.org/pdf/1509.02971.pdf
https://papers.nips.cc/paper/7217-multi-agent-actor-critic-for-mixed-cooperative-competitive-environments.pdf

Actor-Critic Method
Actor-Critic Method benifits the strength of both policy-based and value-based methods.

While running, collect the score larger than SOLVED_SCORE, save the result model. If a better result found, update it. Until max episode reached or no improvement happens.

## Parameters

- Agent

BUFFER_SIZE = int(1e6)  # replay buffer size <br>
BATCH_SIZE = 128        # minibatch size <br>
LR_ACTOR = 1e-3         # learning rate of the actor <br>
LR_CRITIC = 1e-3        # learning rate of the critic<br>
WEIGHT_DECAY = 0   # L2 weight decay<br>
LEARN_EVERY = 1<br>
LEARN_NUM = 5<br>
GAMMA = 0.99            # discount factor<br>
TAU = 8e-3              # for soft update of target parameters<br>
OU_SIGMA = 0.2<br>
OU_THETA = 0.15<br>
EPS_START = 5.0<br>
EPS_EP_END = 300<br>
EPS_FINAL = 0<br>

## Result

Episode 0000-0010	 Max Reward: 0.000	 Moving Average: 0.000 <br>
Episode 0010-0020	 Max Reward: 0.000	 Moving Average: 0.000 <br>
Episode 0020-0030	 Max Reward: 0.100	 Moving Average: 0.013 <br>
... <br>
Episode 1680-1690	 Max Reward: 0.900	 Moving Average: 0.398 <br>
Episode 1690-1700	 Max Reward: 5.200	 Moving Average: 0.445 <br>
<-- Environment Solved in 1608 episodes.  <br>
 Moving Average: 0.518 over past 100 episodes <br>
Episode 1700-1710	 Max Reward: 4.400	 Moving Average: 0.538 <br>
Episode 1710-1720	 Max Reward: 3.200	 Moving Average: 0.595 <br>
Episode 1720-1730	 Max Reward: 2.000	 Moving Average: 0.617 <br>
Episode 1730-1740	 Max Reward: 1.400	 Moving Average: 0.639 <br>
Best episode so far <br>
 Episode 1742	 Max reward: 5.200 	 Moving average: 0.680 <br>
Episode 1740-1750	 Max Reward: 5.200	 Moving Average: 0.797 <br>
Episode 1750-1760	 Max Reward: 4.100	 Moving Average: 0.939 <br>
Episode 1760-1770	 Max Reward: 5.100	 Moving Average: 1.107 <br>
Episode 1770-1780	 Max Reward: 3.400	 Moving Average: 1.235 <br>
Episode 1780-1790	 Max Reward: 5.100	 Moving Average: 1.331 <br>
Best episode so far <br>
 Episode 1794	 Max reward: 5.200 	 Moving average: 1.439 <br>
Episode 1790-1800	 Max Reward: 5.200	 Moving Average: 1.346 <br>
Best episode so far <br>
 Episode 1805	 Max reward: 5.200 	 Moving average: 1.425 <br>
Episode 1800-1810	 Max Reward: 5.200	 Moving Average: 1.343 <br>
... <br>
Episode 1880-1890	 Max Reward: 2.400	 Moving Average: 1.024 <br>
Episode 1890-1900	 Max Reward: 3.400	 Moving Average: 0.988 <br>
Training stopped. Best score not matched or exceeded for 200 episodes <br>

![ResultPlot][image1]

Best episode solved in Episode 1805	 Max reward: 5.200 	 Moving average: 1.425

## Future Improvements

- Make the result more stable. Not all the result can converge so far.
- Use batch normalization to improve the algorithm