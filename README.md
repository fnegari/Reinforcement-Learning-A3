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


---

## 🌐 GridWorld Environment

