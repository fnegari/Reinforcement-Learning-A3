Reinforcement Learning Assignment 3

This repository contains the implementation of Sarsa and Q-learning algorithms for a 5x5 GridWorld problem as part of the Reinforcement Learning course (Course Number: 6650) Assignment 3.

Project Description

The GridWorld is a 5x5 grid where an agent starts at state 20 (blue square) and aims to reach one of the terminal states (0 or 4, black squares) while avoiding red states (10, 11, 13, 14). Red states incur a -20 reward and reset the agent to the starting state. Normal moves yield a -1 reward, and terminal states yield a 0 reward. The goal is to learn optimal policies using Sarsa and Q-learning algorithms with an ε-greedy action selection strategy (ε = 0.1).
The code implements:

Sarsa: An on-policy temporal difference (TD) control method that updates Q-values based on the action taken in the next state.
Q-learning: An off-policy TD control method that updates Q-values based on the maximum Q-value of the next state.

The implementation includes functions to plot the agent's trajectories, reward patterns for each algorithm, and a combined reward comparison. The results are analyzed to compare the performance of the two algorithms.
Prerequisites
To run the code, you need the following:

Python: Version 3.6 or higher
NumPy: For numerical computations
Matplotlib: For generating plots

You can install the required libraries using pip:
pip install numpy matplotlib

Installation

Clone this repository to your local machine:git clone https://github.com/your-username/rl-assignment3


Navigate to the repository directory:cd rl-assignment3


Ensure Python, NumPy, and Matplotlib are installed (see Prerequisites).

How to Run

Ensure you are in the directory containing untitled15.py.
Run the script using Python:python untitled15.py


The script will:
Train Sarsa and Q-learning agents for 300 episodes.
Generate plots for trajectories and reward patterns.
Save the plots as PNG files (sarsa_trajectory.png, qlearning_trajectory.png, sarsa_rewards.png, qlearning_rewards.png, combined_rewards.png).
Print the optimal policies, trajectories, and reward analysis to the console.



Expected Outputs
Running the script will produce the following outputs:

Plots:
Sarsa Trajectory: Visualizes the path taken by the Sarsa agent from state 20 to a terminal state (e.g., 20 → 21 → 22 → 17 → 12 → 7 → 2 → 1 → 0).
Q-learning Trajectory: Visualizes the path taken by the Q-learning agent (e.g., 20 → 21 → 16 → 17 → 12 → 7 → 6 → 5 → 0).
Sarsa Reward Pattern: Shows the total reward per episode for the Sarsa agent.
Q-learning Reward Pattern: Shows the total reward per episode for the Q-learning agent.
Combined Reward Pattern: Compares the reward patterns of both algorithms.


Console Output:
Optimal policies for Sarsa and Q-learning (5x5 grids with actions: 0=up, 1=down, 2=left, 3=right).
Trajectories for both algorithms.
Analysis of reward behavior, including average rewards over the last 50 episodes (-19.70 for Sarsa, -13.34 for Q-learning).
Comparison of trajectories, noting differences due to Sarsa's on-policy vs. Q-learning's off-policy nature.



The plots are saved as PNG files in the same directory as the script for inclusion in the report.
Notes on Reproducibility

The code uses np.random.seed(42) to ensure reproducible results.
Parameters used:
Learning rate (α): 0.5
Discount factor (γ): 0.95
Exploration rate (ε): 0.1
Number of episodes: 300


The environment is deterministic, but the ε-greedy policy introduces randomness during training, which is controlled by the random seed.
The average rewards (-19.70 for Sarsa, -13.34 for Q-learning) suggest incomplete convergence, as optimal paths should yield -6 to -8. Increasing the number of episodes (e.g., to 1000) or reducing ε (e.g., to 0.05) may improve results.

Credits
This assignment was completed by Fatemeh Negari and Saba Tamizi for the Reinforcement Learning course (Course Number: 6650).
Contact
