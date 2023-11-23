# Reatil Store

This code implements a reinforcement learning model for a toy example of a retail store. It implements simple algorithms with the toys examples: the Q Learning and Policy Iteration.

## Policy Iteration

**Algorithm Overview**

Policy Iteration is an iterative algorithm in reinforcement learning used to find the optimal policy by alternating between policy evaluation and policy improvement steps.

### Steps:

1. **Policy Evaluation**:  
   Evaluate the value function \( V^{\pi}(s) \) for the current policy \(\pi\).
   
   \[ V^{\pi}(s) = \sum_{s', r} p(s', r \mid s, \pi(s)) \cdot [r + \gamma \cdot V^{\pi}(s')] \]
   
2. **Policy Improvement**:  
   Improve the policy by selecting actions greedily based on the computed value function.
   
   \[ \pi_{\text{new}}(s) = \text{argmax}_a \sum_{s', r} p(s', r \mid s, a) \cdot [r + \gamma \cdot V^{\pi}(s')] \]
   
3. **Iteration**:  
   Repeat steps 1 and 2 until the policy converges to the optimal policy \(\pi^*\).

### Convergence:

- **Guaranteed Convergence**:  
  Policy Iteration converges to the optimal policy for finite Markov Decision Processes (MDPs) under certain conditions:
  - Finite state and action spaces
  - Accurate representation of the environment's dynamics

  ### Q-Learning

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

