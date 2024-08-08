### Project Details

#### Overview
This notebook is about the implementation of a Multi-Agent Deep Deterministic Policy Gradient (MADDPG) algorithm to solve the Tennis environment from the Unity ML-Agents toolkit. 

The goal is for agents to cooperate to keep the ball in play. After each episode, we add up the rewards that each agent received to get a score for each agent. This yields 2 scores. We then take the maximum of these 2 scores. This yields a single score for each episode.

The environment is solved when the average of total scores over 100 episodes is at least 0.51.

#### Content

- One random model not achieving the result
- One model achieving result (MADDPG)

#### To test the model

Model weights for both Actor and Critic networks are saved as PyTorch state dictionaries. The weights can be loaded for further evaluation or continued training.

- Run the code except the "Train agent and get results" and "Plot Scores" sections
- Initialize agent

agent = MADDPG(state_size=state_size, action_size=action_size, num_agents=num_agents, random_seed=89)

- Load the saved weights for each agent
for i in range(num_agents):
    agent.agents[i].actor_regular.load_state_dict(torch.load(f'checkpoint_actor_agent_v2_{i}.pth', map_location=DEVICE))
    agent.agents[i].critic_regular.load_state_dict(torch.load(f'checkpoint_critic_agent_v2_{i}.pth', map_location=DEVICE))

- Run the test episodes
scores = np.zeros(num_agents)
env_info = env.reset(train_mode=False)[brain_name]
states = env_info.vector_observations
while True:
    actions = agent.act(states)
    env_info = env.step(actions)[brain_name]
    next_states = env_info.vector_observations
    rewards = env_info.rewards
    dones = env_info.local_done
    scores += rewards
    states = next_states
    if np.any(dones):
        break

- Print the total score averaged over all agents
print('Total score (averaged over agents) this episode: {}'.format(np.mean(scores)))

#### Notes

It is required to start the kernel two times two grant the torch installation

## Requirements
In order to prepare the environment, follow the next steps after downloading this repository:
* Create a new environment:
	* __Linux__ or __Mac__: 
	```bash
	conda create --name drlnd python=3.6
	source activate drlnd
	```
	* __Windows__: 
	```bash
	conda create --name dqn python=3.6 
	activate drlnd
	```
* Min install of OpenAI gym
	* If using __Windows__, 
		* download [swig for windows](http://www.swig.org/Doc1.3/Windows.html) and add it the PATH of windows
		* install [ Microsoft Visual C++ Build Tools ](https://visualstudio.microsoft.com/es/downloads/).
	* then run these commands
	```bash
	pip install gym
	pip install gym[classic_control]
	pip install gym[box2d]
	```
* Install the dependencies under the folder [python/] (https://github.com/udacity/deep-reinforcement-learning/tree/master/python).
```bash
	cd python
	pip install .
```
* Create an IPython kernel for the `drlnd` environment
```bash
	python -m ipykernel install --user --name drlnd --display-name "drlnd"
```

* Download the environment from one of the links below.  You need only select the environment that matches your operating system:
     - Links
        - Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Linux.zip)
        - Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis.app.zip)
        - Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Windows_x86.zip)
        - Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Windows_x86_64.zip)

    (_For Windows users_) Check out [this link](https://support.microsoft.com/en-us/help/827218/how-to-determine-whether-a-computer-is-running-a-32-bit-version-or-64) if you need help with determining if your computer is running a 32-bit version or 64-bit version of the Windows operating system.

    (_For AWS_) If you'd like to train the agent on AWS (and have not [enabled a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md)), then please use [this link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Linux_NoVis.zip) (version 1) or [this link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Linux_NoVis.zip) (version 2) to obtain the "headless" version of the environment.  You will **not** be able to watch the agent without enabling a virtual screen, but you will be able to train the agent.  (_To watch the agent, you should follow the instructions to [enable a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md), and then download the environment for the **Linux** operating system above._)

* Unzip the downloaded file and move it inside the project's root directory
* Change the kernel of your environment to `drlnd`
