# MADDPG (Multi-Agent Deep Deterministic Policy Gradient)

## Key Points:
Multi-Agent: Designed for multiple interacting agents in a shared environment.
Centralized Training, Decentralized Execution: During training, all agents’ experiences are shared. Each agent uses its own policy during execution.
Actor-Critic Architecture: Each agent has its own actor (for action selection) and critic (for evaluating actions).
Replay Buffer: Utilizes a shared replay buffer to store experiences from all agents for training.
Policy Update: Updates policies using policy gradients based on the critic’s feedback.

## How It Works:
Initialize: Policies and value functions for all agents, and a shared replay buffer.
Interact: Agents take actions, and experiences are stored in the replay buffer.
Train: Sample from the buffer, train critics, and update actors.
Deploy: Agents use their policies independently.

## MADDPG vs. DDPG:

### Multi-Agent vs. Single-Agent:
DDPG is for single-agent scenarios.
MADDPG extends DDPG to multi-agent environments.
### Centralized Training vs. Decentralized Training:
DDPG trains a single agent in isolation.
MADDPG uses centralized training with shared experiences but decentralized execution.
### Replay Buffer:
DDPG has a replay buffer for a single agent.
MADDPG uses a shared replay buffer for all agents.
### Policy Evaluation:
DDPG uses a single actor-critic pair.
MADDPG employs multiple actor-critic pairs, one for each agent.