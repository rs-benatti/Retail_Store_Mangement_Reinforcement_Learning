# Retail Store

This code implements a reinforcement learning model for a toy example of a retail store. It implements simple algorithms with the toys examples: the Q Learning and Policy Iteration.

## Policy Iteration

Policy Iteration is an iterative algorithm used in reinforcement learning for finding the optimal policy. It combines policy evaluation and improvement steps to converge to an optimal policy. The algorithm follows these steps:

1. **Policy Evaluation**:
   - Given a policy π, compute the state-value function ![Vπ](https://latex.codecogs.com/svg.latex?V_%5Cpi) using the Bellman equation:

   ![Bellman Expectation Equation](https://latex.codecogs.com/svg.latex?V_%5Cpi%28s%29%20%3D%20%5Csum_%7Ba%7D%20%5Cpi%28a%7Cs%29%20%5Csum_%7Bs%27%2Cr%7D%20p%28s%27%2C%20r%7Cs%2C%20a%29%20%5B%20r%20&plus;%20%5Cgamma%20%5Ccdot%20V_%5Cpi%28s%27%29%20%5D)
   
2. **Policy Improvement**:
   - Update the policy by selecting the actions that maximize the expected future rewards. 

   ![Policy Update Equation](https://latex.codecogs.com/svg.latex?%5Cpi%27%28s%29%20%3D%20%5Carg%5Cmax_%7Ba%7D%20%5Csum_%7Bs%27%2Cr%7D%20p%28s%27%2C%20r%7Cs%2C%20a%29%20%5B%20r%20&plus;%20%5Cgamma%20%5Ccdot%20V_%5Cpi%28s%27%29%20%5D)

3. **Iteration**:
   - Repeat policy evaluation and improvement until convergence to the optimal policy ![π*](https://latex.codecogs.com/svg.latex?%5Cpi%5E%2A).

Policy Iteration seeks to find the best policy by iteratively evaluating and updating policies based on the expected rewards and transitions between states, aiming to converge to the optimal policy that maximizes cumulative rewards.

## Q-Learning

Q-Learning is a model-free, off-policy reinforcement learning algorithm that learns the value of state-action pairs. It's based on the Bellman equation and updates its Q-values iteratively using a greedy policy and the following update rule:

#### Algorithm Steps:

1. **Initialize Q-Table**: Initialize Q-values arbitrarily for all state-action pairs.
2. **For each episode**:
    - **Choose an action** using an exploration strategy (e.g., ε-greedy) for the current state.
    - **Observe the reward and next state** after taking the action.
    - **Update Q-value**: Use the Q-learning update equation to update Q-values:
    
    ![Q-Learning Update Equation](https://latex.codecogs.com/svg.latex?Q%28s%2C%20a%29%20%5Cleftarrow%20Q%28s%2C%20a%29%20&plus;%20%5Calpha%20%5Ccdot%20%5B%20r%20&plus;%20%5Cgamma%20%5Ccdot%20%5Cmax%28Q%28s%27%2C%20a%29%29%20-%20Q%28s%2C%20a%29%20%5D)
    
    Where:
    - ![alpha](https://latex.codecogs.com/svg.latex?%5Calpha) is the learning rate.
    - ![gamma](https://latex.codecogs.com/svg.latex?%5Cgamma) is the discount factor.
    - ![r](https://latex.codecogs.com/svg.latex?r) is the immediate reward.
    - ![s](https://latex.codecogs.com/svg.latex?s) is the current state.
    - ![a](https://latex.codecogs.com/svg.latex?a) is the action taken.
    - ![s_prime](https://latex.codecogs.com/svg.latex?s%27) is the next state.
    
3. **Repeat** the above steps until convergence or a set number of episodes.

Q-learning learns an optimal policy by iteratively updating Q-values based on rewards obtained from state-action pairs and selecting actions that maximize the expected cumulative reward.

This algorithm aims to converge Q-values to the optimal values that satisfy the Bellman optimality equation:

![Bellman Optimality Equation](https://latex.codecogs.com/svg.latex?Q%5E*%28s%2C%20a%29%20%3D%20%5Cmax_%7Ba%7D%20%5Csum_%7Bs%27%7D%20P%28s%27%7Cs%2C%20a%29%20%5B%20R%28s%27%29%20&plus;%20%5Cgamma%20%5Ccdot%20%5Cmax_%7Ba%27%7D%20Q%5E*%28s%27%2C%20a%27%29%20%5D)

Where ![Q*](https://latex.codecogs.com/svg.latex?Q%5E*) is the optimal Q-function, ![P](https://latex.codecogs.com/svg.latex?P) is the transition probability, ![R](https://latex.codecogs.com/svg.latex?R) is the reward function, and ![gamma](https://latex.codecogs.com/svg.latex?%5Cgamma) is the discount factor.

