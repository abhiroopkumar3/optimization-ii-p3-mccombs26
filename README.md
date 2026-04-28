# 🎮 Connect-4 Reinforcement Learning Engine

**Optimization II – Project 3 | Group 3**  

---

## 📌 Project Overview

This project explores **Reinforcement Learning (RL)** to develop competitive strategies for the game **Connect-4**. The objective is to train agents that can learn optimal gameplay through **self-play, adversarial training, and dynamic decision-making**.

We implement and compare two core RL approaches:

* **Policy Gradient (PG)** – probabilistic action learning
* **Deep Q-Network (DQN)** – value-based learning using Bellman updates

This aligns with the project requirement of building RL agents for sequential decision-making problems .

---

## 🧠 Key Concepts

* Reinforcement Learning (Approximate Dynamic Programming)
* Exploration vs Exploitation
* Self-play & Adversarial Training
* Policy Optimization vs Value Function Learning
* Tournament-based evaluation

---

## 📂 Repository Structure

```
.
├── abhiroop_CNN_v2_deep_best.h5         # Teammate model (CNN)
├── aileen_connect4_cnn_final.*          # Teammate models (not used due to compatibility issue)
├── jake_cnn_best.keras                  # Baseline model
├── Riju_cnn_model_2.h5                  # Selected base model (M1)
│
├── Optimization-II Project 3 (G3) - Final Report.pdf
├── Optimization-II_Project3_G3_-_Analysis_Notebook__Final.ipynb
│
├── project3_artifacts/
│   ├── *.csv                            # Metrics, summaries, evaluation outputs
│   ├── plots/                           # Training curves, heatmaps, comparisons
│   ├── trained_models/                  # Final trained RL models (PG, DQN)
│
├── tounament_helpers/
│   ├── Gameplay_Helper_0-6.ipynb        # Tournament interface (0–6 indexing)
│   ├── Gameplay_Helper_1-7.ipynb        # Tournament interface (1–7 indexing)
│   ├── pool_3_gameplay_results.xlsx     # Tournament results
│
├── old_scripts/
│   ├── project3_connect4_rl_complete.ipynb
│   ├── project3_infrastructure.ipynb
```

---

## ⚙️ Core System Architecture

The project is built around a reusable RL infrastructure:

1. **Game Environment**

   * Connect-4 board logic (6×7 grid)
   * Legal moves, win detection, encoding
   * State representation: `(6, 7, 2)` tensor

2. **Model Interface**

   * Supports CNN & Transformer models
   * Unified `get_move()` function with:

     * argmax (deterministic)
     * stochastic (sampling)
     * epsilon-greedy (exploration)

3. **Agents**

   * ModelAgent (CNN-based)
   * DQNAgent (value-based)
   * Random & Tactical baselines

4. **Evaluation Engine**

   * Head-to-head matches
   * Round-robin tournaments
   * Metrics: win rate, moves, performance

This modular design enables flexible experimentation and aligns with RL simulation workflows described in class .

---

## 🚀 Methodology

### 1️⃣ Baseline Evaluation

* Compare all teammate models
* Generate round-robin win-rate matrix
* Validate environment correctness

---

### 2️⃣ Policy Gradient (PG)

* Start with base model **M1 (Riju_CNN)**
* Play against a pool of opponents (M2)
* Sample moves probabilistically (not greedy)
* Update using REINFORCE:

$$[
\text{Loss} = - \mathbb{E}[R \cdot \log \pi(a|s)]
]$$

* Use:

  * Replay buffer
  * Randomized openings
  * Adversarial opponent pool

---

### 3️⃣ Deep Q-Network (DQN)

* Learn action-value function $( Q(s,a) )$
* Use Bellman update:

$$[
Q(s,a) \leftarrow r + \gamma \max Q(s', a')
]$$

* Techniques used:

  * Epsilon-greedy exploration
  * Target network
  * Replay buffer
  * Randomized initial states

---

### 4️⃣ Final Evaluation

* Compare:

  * Original M1
  * PG-improved model
  * DQN model
  * Baselines

* Metrics:

  * Win rate
  * Average moves
  * Stability

---

## 📊 Outputs & Artifacts

### 📁 CSV Files

* `baseline_round_robin_win_rates.csv`
* `pg_training_history.csv`
* `dqn_training_history.csv`
* `final_round_robin_win_rates.csv`
* `pg_dqn_comparison_summary.csv`

### 📈 Visualizations

Located in `project3_artifacts/plots/`:

* Learning curves (PG & DQN)
* Loss curves
* Win-rate heatmaps
* Model comparison charts
* Move preference analysis

---

## 🏆 Tournament Integration

* Supports **2-game match format (first/second player)**
* Compatible with:

  * 0–6 indexing
  * 1–7 indexing (for UI consistency)
* Tracks:

  * Wins
  * Moves (tie-breaker)
  * Match outcomes

---

## ⚠️ Known Issues

* `aileen_connect4_cnn_final.h5` not used due to **Lambda layer deserialization issue**
* Requires TensorFlow/Keras compatibility for model loading
* GPU recommended for faster training (optional)

---

## 🧪 How to Run

### 1. Setup Environment

```bash
pip install numpy tensorflow pandas matplotlib
```

---

### 2. Run Notebook

```bash
jupyter notebook Optimization-II_Project3_G3_-_Analysis_Notebook__Final.ipynb
```

Run all cells sequentially.

---

### 3. Tournament Gameplay

Use helper notebooks:

```
tounament_helpers/
```

---

## 📌 Key Insights

* **Policy Gradient**

  * Stable but slower improvement
  * Benefits from diverse opponents

* **DQN**

  * Faster learning via value approximation
  * Sensitive to hyperparameters

* **Best Performance**

  * Improved PG model showed strong consistency
  * DQN competitive but less stable

---

## 💼 Business Perspective

* RL is effective for **strategic decision-making under uncertainty**
* Applicable to:

  * Gaming AI
  * Pricing strategies
  * Operations optimization
* Hiring RL expertise can accelerate innovation but requires:

  * Strong infrastructure
  * High compute
  * Careful tuning

---

## 👥 Team

Group 3 – Optimization II
MS Business Analytics – UT Austin
