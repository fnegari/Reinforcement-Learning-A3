```markdown
# Reinforcement Learning Assignment 3

This repository contains the implementation of **Sarsa** and **Q-learning** algorithms for a 5×5 GridWorld problem, submitted for the Reinforcement Learning course (Course Number: 6650) at Memorial University.  
**Assignment 3 — Due August 5, 2025**

---

## 📖 Overview

- **Goal:** Learn optimal policies for a 5×5 GridWorld using on-policy (Sarsa) and off-policy (Q-learning) methods.  
- **Action selection:** ε-greedy (ε = 0.1)  
- **Training:** 300 episodes, α = 0.5, γ = 0.95  
- **Outputs:**  
  - Optimal policy grids  
  - Trajectories under greedy policy  
  - Reward-per-episode plots  
  - PNG files for inclusion in the report

---

## 🌐 GridWorld Environment

```

0   1   2   3   4
5   6   7   8   9
10  11  12  13  14
15  16  17  18  19
20  21  22  23  24

````

- **Start:** State 20 (bottom-left)  
- **Terminal:** States 0, 4 (top row) reward = 0  
- **Red states:** 10, 11, 13, 14 (reward = –20, reset to 20)  
- **Rewards:**  
  - Normal move (white cell): –1  
  - Wall collision: –1  
  - Red cell: –20 + reset  
  - Terminal: 0  

---

## ⚙️ Implementation

- **Sarsa (On-Policy):**

  \[
  Q(s,a) \leftarrow Q(s,a) + \alpha \bigl[r + \gamma\,Q(s',a') - Q(s,a)\bigr]
  \]

- **Q-learning (Off-Policy):**

  \[
  Q(s,a) \leftarrow Q(s,a) + \alpha \bigl[r + \gamma\,\max_{a'} Q(s',a') - Q(s,a)\bigr]
  \]

- **ε-greedy:**  
  - 10% random action  
  - 90% best action

---

## 🛠 Prerequisites

- **Python 3.6+**  
- **NumPy**  
- **Matplotlib**

```bash
pip install numpy matplotlib
````

---

## 📥 Installation

```bash
git clone https://github.com/[your-username]/rl-assignment3.git
cd rl-assignment3
```

Verify that `untitled15.py` is present and dependencies are installed.

---

## ▶️ How to Run

```bash
python untitled15.py
```

The script will:

1. Seed RNG for reproducibility (`np.random.seed(42)`).
2. Train Sarsa and Q-learning for 300 episodes.
3. Save plots as:

   * `sarsa_trajectory.png`
   * `qlearning_trajectory.png`
   * `sarsa_rewards.png`
   * `qlearning_rewards.png`
   * `combined_rewards.png`
4. Print policies, trajectories, and reward analysis to console.

---

## 🎯 Expected Outputs

* **Trajectories (Greedy after training):**

  * **Sarsa:**

    ```
    20 → 21 → 22 → 17 → 12 → 7 → 2 → 1 → 0  (8 steps)
    ```
  * **Q-learning:**

    ```
    20 → 21 → 16 → 17 → 12 → 7 → 6 → 5 → 0  (8 steps)
    ```

* **Reward Analysis (last 50 episodes):**

  * Sarsa: **–19.70**
  * Q-learning: **–13.34**

---

## 📊 Results Summary

| Algorithm      | Trajectory                       | Avg. Reward (Last 50 Eps) | Notes                          |
| -------------- | -------------------------------- | ------------------------: | ------------------------------ |
| **Sarsa**      | 20→21→22→17→12→7→2→1→0 (8 steps) |                    –19.70 | On-policy, safer path          |
| **Q-learning** | 20→21→16→17→12→7→6→5→0 (8 steps) |                    –13.34 | Off-policy, faster convergence |

---

## 🔄 Reproducibility

* **Random Seed:** `np.random.seed(42)`
* **Parameters:**

  * Learning rate (α): 0.5
  * Discount factor (γ): 0.95
  * Exploration rate (ε): 0.1
  * Episodes: 300
* **Note:** Deterministic environment; only ε-greedy introduces randomness.
* **Tip:** Increase episodes (e.g., 1000) or reduce ε (e.g., 0.05) for better convergence (optimal \~–6 to –8).

---

## 🙏 Credits

Completed by **Fatemeh Negari** and **Saba Tamizi** for RL Course (6650).

---

## 📫 Contact

For issues or questions, open an issue or contact:
`your.email@domain.com` • [GitHub](https://github.com/your-username)

```
```
