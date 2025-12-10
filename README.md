# 🤖 RL: SARSA & Q-Learning on a Custom GridWorld Environment

This project implements and analyzes two foundational reinforcement learning algorithms — **SARSA** and **Q-Learning** — inside a fully custom-designed **5×5 GridWorld**.  
It includes environment construction, reward design, safe movement rules, algorithm implementation, hyperparameter tuning, and visualization of learning performance.

The work is divided into three main parts:

- **Part I — Environment Design & Visualization**
- **Part II — SARSA Implementation & Tuning**
- **Part III — Q-Learning Implementation & Tuning**

---

## 🌍 Environment Overview (5×5 GridWorld)

The GridWorld contains **25 states** (S1–S25), arranged in a 5×5 matrix.  
Each cell contains one of five possible reward types.

### 🔹 Reward Structure

| Object | Count | Locations | Reward |
|--------|--------|-----------|---------|
| **Stones** | 3 | (4,0), (2,2), (1,3) | –5 |
| **Prizes** | 3 | (1,1), (4,2), (0,4) | +10 |
| **Goal** | 1 | (3,3) | +20 |
| **Fences** | 2 | (3,0), (4,4) | –12 |
| **Normal Cells** | remaining | — | 0 |

### 🔹 Action Space  
The agent may take **4 actions**:

- Up  
- Down  
- Left  
- Right  

### 🔹 Safety Rules  

- Initial state: **S1 → (0,0)**  
- Movements use `np.clip()` to avoid leaving the grid  
- All transitions are deterministic  
- Reward computed from the landing cell  

---

# 🧩 Part I — Environment Visualization

This part displays the environment structure:

- 5×5 grid with markers for stones, prizes, fences, and the goal  
- State numbering (S1–S25)  
- Visual confirmation of object placement  
- Simple trajectory examples to validate movement rules  

These plots help verify that environment logic and reward mapping are correct.

---

# 🧠 Part II — SARSA (On-Policy Learning)

SARSA uses the update rule:

\[
Q(s,a) \leftarrow Q(s,a) + \alpha \left[r + \gamma Q(s',a') - Q(s,a)\right]
\]

### ✔ Features Implemented

- Epsilon-greedy exploration  
- Q-table initialization  
- TD update using (state, action, reward, next_state, next_action)  
- Episode-based training  
- Hyperparameter tuning, including:
  - γ (discount factor)
  - ε (epsilon)
  - ε decay schedule
  - Max steps per episode

### ✔ Tuning Approaches

- Manual hyperparameter search  
- Automated **Optuna** tuning for optimal γ and ε schedules  

### ✔ Outputs

- Reward curves across episodes  
- Comparison before and after tuning  
- Stability analysis  

---

# 🧠 Part III — Q-Learning (Off-Policy Learning)

Q-Learning uses the greedy next action as its target:

\[
Q(s,a) \leftarrow Q(s,a) + \alpha \left[r + \gamma \max_{a'} Q(s',a') - Q(s,a)\right]
\]

### ✔ Features Implemented

- Off-policy TD update  
- Epsilon-greedy exploration  
- Manual hyperparameter tuning  
- Reward curve visualization  
- Comparison of learning speed and convergence behavior  

### ✔ Observed Behavior

- Faster convergence than SARSA  
- Higher stability in reward learning  
- More consistent final policy  

---

# 🔄 SARSA vs Q-Learning — Summary Comparison

| Criterion | SARSA | Q-Learning |
|-----------|--------|------------|
| Policy Type | On-policy | Off-policy |
| Update Target | Uses next **chosen** action | Uses next **best** action |
| Convergence | Slower | Faster |
| Stability | Moderate | High |
| Final Reward | Good | Often better |

In this project, **Q-Learning outperformed SARSA**, achieving higher final rewards and more stable training.

---

## 📂 Project Structure

```
project/
├── Code.ipynb        # Environment setup + visualization + SARSA implementation + Q-learning implementation
└── README.md                       # Documentation (this file)
```

---

## 🧰 Tools & Libraries

- Python 3.x  
- NumPy  
- Matplotlib  
- Optuna (for tuning SARSA)  
- Jupyter Notebook  

---

## 🎯 Key Learning Outcomes

Through this project, you gain experience in:

- Designing RL environments from scratch  
- Implementing SARSA and Q-Learning correctly  
- Using TD control methods and exploration strategies  
- Tuning hyperparameters manually and automatically  
- Analyzing learning curves and convergence properties  
- Building safe movement logic and deterministic transitions  

---


