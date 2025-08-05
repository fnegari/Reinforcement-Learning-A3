Reinforcement Learning Assignment 3

This repository contains the implementation of Sarsa and Q-learning algorithms for a 5x5 GridWorld problem, submitted for the Reinforcement Learning course (Course Number: 6650) at Memorial University, Assignment 3, due August 5, 2025.


Project Description
The GridWorld is a 5x5 grid with 25 states, numbered as follows:
[ 0  1  2  3  4]
[ 5  6  7  8  9]
[10 11 12 13 14]
[15 16 17 18 19]
[20 21 22 23 24]


Starting State: State 20 (bottom-left, blue square).
Terminal States: States 0 and 4 (top row, black squares), yielding a reward of 0.
Red States: States 10, 11, 13, 14 (third row, except state 12), incurring a -20 reward and resetting the agent to state 20.
Rewards:
Normal moves to white cells: -1 reward.
Wall collisions (attempting to move outside the grid): -1 reward.
Red states: -20 reward and reset to state 20.
Terminal states: 0 reward.


Actions: Four actions encoded as 0=up, 1=down, 2=left, 3=right.
Objective: Learn optimal policies using Sarsa and Q-learning to navigate from state 20 to a terminal state (0 or 4) through the gap at state 12, avoiding red states.

The implementation in untitled15.py includes:

Sarsa: An on-policy temporal difference (TD) control method, updating Q-values based on the action taken in the next state using the rule:[Q(s, a) \leftarrow Q(s, a) + \alpha [r + \gamma Q(s', a') - Q(s, a)]]
Q-learning: An off-policy TD control method, updating Q-values based on the maximum Q-value of the next state using the rule:[Q(s, a) \leftarrow Q(s, a) + \alpha [r + \gamma \max_{a'} Q(s', a') - Q(s, a)]]
Action Selection: Uses ε-greedy policy with ε = 0.1 for exploration (random action with 10% probability) and exploitation (best action otherwise).
Outputs: Generates optimal policies, trajectories (greedy policy from state 20), reward patterns per episode, and a comparison of Sarsa and Q-learning rewards.

The code produces visualizations (trajectories and reward plots) saved as PNG files for inclusion in the report, along with a detailed analysis of reward behavior and trajectory differences.
Prerequisites
To run the code, you need:

Python: Version 3.6 or higher
NumPy: For numerical computations and Q-table management
Matplotlib: For generating trajectory and reward plots

Install the required libraries using pip:
pip install numpy matplotlib

Installation

Clone this repository to your local machine:git clone https://github.com/[your-username]/rl-assignment3


Navigate to the repository directory:cd rl-assignment3


Ensure Python, NumPy, and Matplotlib are installed (see Prerequisites).

How to Run

Ensure you are in the directory containing untitled15.py.
Run the script using Python:python untitled15.py


The script will:
Set a random seed (np.random.seed(42)) for reproducibility.
Train Sarsa and Q-learning agents for 300 episodes with parameters:
Learning rate (α): 0.5
Discount factor (γ): 0.95
Exploration rate (ε): 0.1


Generate and save plots:
sarsa_trajectory.png: Sarsa trajectory (20→21→22→17→12→7→2→1→0, 8 steps)
qlearning_trajectory.png: Q-learning trajectory (20→21→16→17→12→7→6→5→0, 8 steps)
sarsa_rewards.png: Sarsa reward pattern per episode
qlearning_rewards.png: Q-learning reward pattern per episode
combined_rewards.png: Comparison of Sarsa and Q-learning rewards


Print to console:
Optimal policies (5x5 grids, actions: 0=up, 1=down, 2=left, 3=right)
Trajectories with action names
Reward analysis, including average rewards over the last 50 episodes
Trajectory comparison explaining differences





Expected Outputs
Running untitled15.py produces:

Plots (saved as PNGs in the repository):
Sarsa Trajectory: Path from state 20 to 0 (e.g., 20→21→22→17→12→7→2→1→0, 8 steps), visualized with blue (start), black (terminal), red (penalty), and white (path) states.
Q-learning Trajectory: Path from state 20 to 0 (e.g., 20→21→16→17→12→7→6→5→0, 8 steps), similarly visualized.
Sarsa Reward Pattern: Total rewards per episode for Sarsa, showing convergence toward -6 to -8.
Q-learning Reward Pattern: Total rewards per episode for Q-learning, showing faster convergence.
Combined Reward Pattern: Compares Sarsa and Q-learning rewards, highlighting Q-learning’s lower variance.


Console Output:
Optimal Policies: 5x5 grids for Sarsa and Q-learning, showing the best action per state.
Trajectories: Lists states and actions (e.g., “20 (right) → 21 (right) → ... → 0”).
Reward Analysis:
Sarsa: Average reward over last 50 episodes: -19.70, reflecting occasional red state penalties due to exploration.
Q-learning: Average reward over last 50 episodes: -13.34, showing faster convergence due to off-policy updates.


Trajectory Comparison: Notes differences due to Sarsa’s on-policy updates (safer paths) vs. Q-learning’s off-policy updates (targeting optimal policy).


Analysis: Explains that both algorithms converge through state 12, but 300 episodes may be insufficient for optimal rewards (-6 to -8), as exploration (ε = 0.1) causes red state visits.

The PNG files are included in the repository for inclusion in the report, as required.
Notes on Reproducibility

Random Seed: The code uses np.random.seed(42) to ensure consistent results across runs.
Parameters:
Learning rate (α): 0.5
Discount factor (γ): 0.95
Exploration rate (ε): 0.1
Number of episodes: 300


Environment: Deterministic, with randomness only from the ε-greedy policy, controlled by the seed.
Performance: Average rewards (-19.70 for Sarsa, -13.34 for Q-learning) indicate incomplete convergence, as optimal paths should yield -6 to -8 (6-8 steps at -1 per step). Increasing episodes (e.g., to 1000) or reducing ε (e.g., to 0.05) could improve results.
Code: untitled15.py is fully commented and structured for clarity, following NeurIPS reproducibility guidelines. All dependencies (NumPy, Matplotlib) are standard and easily installed.

Credits
This assignment was completed by Fatemeh Negari and Saba Tamizi for the Reinforcement Learning course (Course Number: 6650).
Contact
For any issues or questions, please contact [Your Email or GitHub Username].
