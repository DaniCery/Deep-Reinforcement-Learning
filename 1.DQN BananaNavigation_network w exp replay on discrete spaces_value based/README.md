# Introduction on Methodologies

## Q-Learning (Sarsamax)

Q-learning is a type of reinforcement learning that helps an agent learn the best action to take in a specific situation without needing to know anything about how the environment works (hence "model-free"). It can deal with problems where outcomes are random and doesn’t need any special adjustments for this.

In any scenario where you can make decisions over time (a Markov decision process), Q-learning finds the best way to act to maximize rewards over the long run. It works by learning the expected rewards for different actions in different states. If the agent explores enough and follows a somewhat random approach, Q-learning can find the optimal way to act. The "Q" in Q-learning stands for the function that estimates these expected rewards.

To put it simply, Q-learning helps an agent figure out which actions are most rewarding in different situations, aiming to maximize overall rewards.


## Deep Q-Network (DQN)

In 2013, DeepMind made a major breakthrough by developing an agent that could learn to play video games more effectively than humans. This was accomplished using a Deep Q-Network (DQN), which combines Q-learning with deep neural networks. The neural network helps the agent learn to make decisions by approximating the Q-values, which estimate the expected rewards for different actions in various states. This approach allowed the agent to master games by learning directly from raw pixel data, without needing explicit instructions.

Note: Double DQN is also possible

### Epsilon-Greedy Strategy

In DQN, the epsilon-greedy strategy is used to select actions during training. This allows the agent to balance exploration and exploitation. It works as follows:

### Exploration: With probability ϵ
the agent chooses a random action. This helps the agent explore new actions and states that it might not have encountered before.
### Exploitation: With probability 1−ϵ
the agent chooses the action that has the highest estimated value based on its current knowledge.

#### How it works

Action Selection: When the DQN agent is deciding which action to take, it uses the epsilon-greedy approach to choose between exploiting the best-known action or exploring new actions.

Training: As the training progresses, ϵ typically decreases over time (decaying epsilon), which means the agent gradually shifts from exploration to more exploitation as it learns more about the environment.

This balance between exploration and exploitation is crucial for DQN to effectively learn and improve its performance in various tasks or games.


# UDACITY Deep Reinforcement Learning: Banana Navigation project

Navigation.ipynb
