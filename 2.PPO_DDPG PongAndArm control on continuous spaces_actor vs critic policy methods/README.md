# Introduction on Methodologies

Policy gradient methods aim to optimize the policy directly by estimating the gradient of the expected reward with respect to the policy parameters. They adjust the policy parameters in the direction that maximizes the expected cumulative reward.

## REINFORCE:
A basic policy gradient method for discrete and continuous spaces, updating the policy using Monte Carlo estimates of rewards.
Type: Policy gradient method
Sampling: Monte Carlo
Variance: High
Stability: Less stable, can be slow to converge
Value Function: Not used
Experience Replay: None.
Exploration: Inherent in the stochastic policy.
Additional Strategies: Uses Monte Carlo sampling to estimate returns and update policies.

## PPO:
An advanced policy gradient method that improves stability and efficiency by using clipped objectives and advantage functions.
Type: Policy optimization method with clipped objective
Sampling: Uses collected experience more efficiently
Variance: Lower, due to value function and clipped updates
Stability: More stable and reliable
Value Function: Often used to reduce variance
Experience Replay: None (uses recent batch of experiences).
Exploration: Handled by the stochastic policy and advantage function.
Additional Strategies: Uses clipped objective function for stability and mini-batch updates.

## DDPG: 
A policy gradient method that is part of the actor-critic framework, suited for continuous action spaces, and combines deterministic policy learning with value function approximation.

Type: Actor-Critic method with deterministic policy
Sampling: Off-policy with experience replay
Variance: Lower, due to value function and deterministic policy
Stability: More stable than simple policy gradient methods, but can still face challenges
Value Function: Used in the critic to estimate action values and stabilize training
Experience Replay: Uses an experience replay buffer.
Exploration: Handled by adding Ornstein-Uhlenbeck noise to actions.
Additional Strategies: Employs target networks to stabilize training and update actor and critic networks.

#### How it works

1. Start with a Policy: Begin with a guess or a starting strategy for making decisions. Policy is a strategy that tells an agent (like a robot or a software) what action to take in each situation (or state) it finds itself in. For example, if you're playing a game, your policy might tell you to jump when you see an obstacle.
2. Try It Out: Let the agent use this strategy to play or act in its environment. This gives us data on how well the strategy is working.
3. Measure Success: Check how well the agent did using the strategy. This could be how many points it scored or how many tasks it completed.
4. Update the Strategy: Adjust the strategy based on how well it performed. If the agent did well, it might tweak the policy to do even better. If it didn't do well, it changes the policy to improve.
5. Repeat: Keep trying out the new policies, measuring success, and updating the policy until the agent gets really good at the task.

Note: Policy Gradient Methods directly teach the agent how to improve its policy. Instead of figuring out the value of each action (like in some other methods), the agent learns how to make better decisions right from the policy itself.


# UDACITY Deep Reinforcement Learning projects

Atari-pong.ipynb (incomplete) (PPO)
Reacher.ipynb (DDPG)
DRL.ipynb (Portfolio_Transactions DDPG)