
# Nim AI using Q-Learning

## Background

In the game of Nim, players take turns removing objects from piles, and the player who removes the last object loses. To build an AI for Nim, we'll use reinforcement learning, specifically Q-learning. Q-learning helps the AI learn the best actions to take in different states of the game by assigning Q-values to (state, action) pairs.

## Representation of States and Actions

A state in the Nim game is represented as a list of integers, where each element corresponds to the size of a pile. For example, the state [1, 1, 3, 5] represents 1 object in pile 0, 1 object in pile 1, 3 objects in pile 2, and 5 objects in pile 3.

An action in the Nim game is represented as a pair of integers (i, j), where i is the pile index, and j is the number of objects to remove from that pile. For example, the action (3, 5) represents the action "take away 5 objects from pile 3".

## The Q-Learning Formula

Q-learning involves updating the Q-values for (state, action) pairs based on the rewards received. The key formula for Q-learning is as follows:

Q(s, a) <- Q(s, a) + alpha * (new value estimate - old value estimate)

Here, alpha is the learning rate, and the new value estimate represents the sum of the immediate reward and the estimate of future rewards the player will receive. The old value estimate is the existing Q-value for the (state, action) pair.

## The Nim Class

The Nim class represents the Nim game and defines gameplay. It keeps track of the current state (piles), the current player (0 or 1), and the winner (if any). The available_actions function returns all possible actions for a given state.

## The NimAI Class

The NimAI class implements the AI for playing Nim using Q-learning. It uses a dictionary called self.q to store Q-values for (state, action) pairs. The alpha and epsilon values control learning rate and action selection, respectively.

### Functions Implemented in NimAI

#### `get_q_value(state, action)`

This function returns the Q-value for a given (state, action) pair. If the Q-value does not exist, it returns 0.

#### `update_q_value(state, action, old_q, reward, future_rewards)`

This function updates the Q-value for the (state, action) pair using the Q-learning formula. It takes the current state, action, existing Q-value, immediate reward, and estimated future rewards as input.

#### `best_future_reward(state)`

This function returns the best possible reward for any available action in a given state, based on the data in self.q.

#### `choose_action(state, epsilon=False)`

This function selects an action to take in a given state, either greedily or using the epsilon-greedy algorithm. If epsilon is False, it chooses the best action based on the highest Q-value. If epsilon is True, it behaves according to the epsilon-greedy algorithm.

## Train and Play Functions

The `train` function trains the AI by running simulated games against itself. It returns the fully trained AI. The `play` function lets a human player play a game of Nim against the AI.

## Conclusion

By implementing the Q-learning functions in NimAI, the AI can learn the optimal strategy for playing Nim. The AI repeatedly plays and learns from experience, updating Q-values to make better decisions in different game states. The Nim game is a great example of how reinforcement learning can be applied to train an AI to play strategic games.
