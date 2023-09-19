# lunar-lander: Reinforcement learning algorithms for training an agent to play the game lunar lander

## Introduction

Implemented an agent that is trained to play the game lunar lander using: <br> <i>i)</i> an actor-critic algorithm, <br><i>ii)</i> a (double) deep Q-learning algorithm. 

### Deep Q-Learning (DQL)

Deep Q-Learning is a reinforcement learning algorithm that combines Q-Learning, a classical reinforcement learning method, with deep neural networks. The goal of DQL is to approximate the optimal action-value function, Q(s, a), where 's' represents the state of the environment and 'a' is the action taken by the agent. The Q-value represents the expected cumulative reward the agent will receive when taking action 'a' in state 's' and following the optimal policy thereafter.

Here's a brief overview of the key components of DQL:

1. **Q-Network:** In DQL, a deep neural network is used to approximate the Q-value function. The input to the network is the state of the environment, and the output is a Q-value for each possible action. The network is trained to minimize the mean squared error between the predicted Q-values and the target Q-values.

2. **Experience Replay:** To stabilize training and break correlations in the sequential data, DQL employs experience replay. This means that the agent stores its experiences (state, action, reward, next state) in a replay buffer. During training, random batches of experiences are sampled from this buffer to update the Q-network.

3. **Target Network:** To further stabilize training, DQL uses two Q-networks: the target network and the online network. The target network's parameters are updated less frequently and are used to compute the target Q-values during training. This helps prevent the network from chasing a moving target during training.

4. **Epsilon-Greedy Policy:** DQL typically uses an epsilon-greedy policy to balance exploration and exploitation. With probability ε, the agent selects a random action (exploration), and with probability 1-ε, it selects the action with the highest estimated Q-value (exploitation).

### Application in Lunar Lander

To apply DQL to the Lunar Lander game, we map the game's state to the input of a neural network. This network then learns to estimate the Q-values for different actions (e.g., throttle, rotate left, rotate right) that the agent can take. Here's how DQL can be applied to training an agent for Lunar Lander:

1. **State Representation:** The state of the Lunar Lander game includes information such as the position and velocity of the lander, the angle of the lander, and the positions of landing pads and obstacles. This state information is used as input to the Q-network.

2. **Action Space:** The agent can take discrete actions, such as firing the left or right engine or doing nothing. The Q-network outputs Q-values for these actions, and the agent selects the action with the highest Q-value according to its epsilon-greedy policy.

3. **Reward Function:** The reward function in Lunar Lander typically provides positive rewards for successful landings and penalizes the agent for crashes or using excessive fuel. The agent's goal is to learn a policy that maximizes the expected cumulative reward over time.

4. **Training Loop:** During training, the agent interacts with the environment, collects experiences, and updates its Q-network using gradient descent to minimize the loss between predicted and target Q-values. The target Q-values are computed using the target network, which is updated periodically.

5. **Exploration vs. Exploitation:** The agent's epsilon-greedy policy ensures that it explores the environment initially but gradually shifts toward exploitation as training progresses.

By using DQL, the agent can learn an effective policy for landing the Lunar Lander safely while optimizing fuel usage. Through reinforcement learning, the agent becomes increasingly proficient at navigating the complex and dynamic environment of the game.

In conclusion, Deep Q-Learning is a powerful reinforcement learning algorithm that, when applied to the Lunar Lander game, enables an agent to learn how to make decisions and take actions that lead to successful landings while minimizing fuel consumption. This approach demonstrates the versatility of DQL in solving a wide range of problems in autonomous decision-making and control.
