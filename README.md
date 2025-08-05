# Reinforcement Learning Assignment 3

**Course**: Reinforcement Learning (6650) at Memorial University\
**Due Date**: August 5, 2025

---

## Overview

This repository implements the Sarsa and Q-learning algorithms on a 5×5 GridWorld. The goal is to learn optimal policies navigating from the start state (20) to one of two terminal states (0 or 4) while avoiding high-penalty red states.

- **Environment**: 5×5 grid, indexed 0–24
- **Start**: 20 (bottom-left)
- **Terminal**: 0 & 4 (top corners, reward = 0)
- **Red states**: 10, 11, 13, 14 (penalty = -20; reset to start)
- **Normal moves**: reward = -1; wall collisions = -1

Both algorithms use ε-greedy exploration (ε = 0.1), learning rate α = 0.5, discount factor γ = 0.95, and run for 300 episodes with a fixed random seed for reproducibility.

---

## Problem Specification

### Environment

- **Terminal states:** 0 and 4 (reward = 0)
- **Penalties:**
  - Reward = -1 for any action (including wall collisions and normal moves between white cells)
  - Entering red states (10, 11, 13, 14) yields reward = -20 and resets the agent to state 20

### Objectives

- Learn the optimal policy using:
  1. Sarsa (on-policy)
  2. Q-learning (off-policy)
- Plot a trajectory of movement under the learned optimal policies for comparison

### Constraints

- Use an ε-greedy action selection strategy (ε = 0.1)

### Approach & Assumptions

- **States:** 25 total, numbered 0–24 and arranged as follows:
  ```
  [ 0  1  2  3  4]
  [ 5  6  7  8  9]
  [10 11 12 13 14]
  [15 16 17 18 19]
  [20 21 22 23 24]
  ```
- **Policy:** a length‑25 vector where each entry indicates the best action for its corresponding state
- **Action-value function:** a 25×4 matrix; each row corresponds to a state, each column to an action
- **Actions encoding:**
  - 0 = up
  - 1 = down
  - 2 = left
  - 3 = right

## Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/fnegari/Reinforcement-Learning-A3.git
   cd Reinforcement-Learning-A3
   ```
2. Create a Python 3 environment and install dependencies:
   ```bash
   pip install numpy matplotlib
   ```

---

## Usage

Run the main script to train both agents, generate trajectories, and plot results:

```bash
python untitled15.py
```

This will:

- Seed the RNG with `np.random.seed(42)`
- Train Sarsa and Q-learning for 300 episodes
- Save the following plots in the working directory:
  - `sarsa_trajectory.png`
  - `qlearning_trajectory.png`
  - `sarsa_rewards.png`
  - `qlearning_rewards.png`
  - `combined_rewards.png`
- Print learned policies, example trajectories, and reward statistics to the console

---

## Implementation Details

- **State representation**: integer 0–24 in row-major order
- **Actions**: 0 = Up, 1 = Down, 2 = Left, 3 = Right
- **Sarsa update**: \(Q(s,a) \leftarrow Q(s,a) + \alpha [r + \gamma Q(s',a') - Q(s,a)]\)
- **Q-learning update**: \(Q(s,a) \leftarrow Q(s,a) + \alpha [r + \gamma \max_{a'} Q(s',a') - Q(s,a)]\)
- **ε-greedy policy**: 10% random, 90% greedy

---

## Results Summary

| Algorithm      | Trajectory (States)              | Avg. Reward (Last 50) | Notes                          |
| -------------- | -------------------------------- | --------------------- | ------------------------------ |
| **Sarsa**      | 20→21→22→17→12→7→2→1→0 (8 steps) | -19.70                | On-policy, safer paths         |
| **Q-learning** | 20→21→16→17→12→7→6→5→0 (8 steps) | -13.34                | Off-policy, faster convergence |

*Average rewards converge toward -6 to -8; increasing episodes or reducing ε can improve performance.*

---

## Reproducibility

- **Random Seed**: `np.random.seed(42)`
- **Parameters**:
  - Learning rate (α): 0.5
  - Discount factor (γ): 0.95
  - Exploration rate (ε): 0.1
  - Episodes: 300

---

## Credits

- **Authors**: Fatemeh Negari & Saba Tamizi
- **Contact**: [fnegari@mun.ca](mailto\:fnegari@mun.ca)

---

*Feel free to open issues or submit pull requests!*

