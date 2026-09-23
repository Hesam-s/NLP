# 🎮 NPC Mind: Reinforcement Learning & LLM-Powered Game AI (`README.md`)

An end-to-end framework for training intelligent Non-Player Character (NPC) behavior using a hybrid **DistilBert Actor-Critic** architecture. This project bridges natural language understanding and reinforcement learning, taking an NPC model through **Supervised Fine-Tuning (SFT)**, **Proximal Policy Optimization (PPO)**, and **Group Relative Policy Optimization (GRPO)**.

---

## 🚀 Project Overview

Modern game development relies heavily on scripted behaviors or basic finite-state machines. This project introduces a scalable approach where an NPC interprets textual game states (e.g., enemy distance, health levels, ammo status, and tactical environments) and determines optimal tactical decisions (**attack, defend, retreat, advance, reload**).

The pipeline utilizes a frozen `distilbert-base-uncased` backbone with unfrozen top transformer layers, coupled with custom actor and critic heads to execute both policy decisions and value estimations.

---

## 🛠️ Pipeline Architecture & Workflow

The notebook is divided into sequential, modular execution steps:

1. **Data Collection & Simulation**: Generates a synthetic dataset (`war_npc_dataset.csv`) modeling diverse combat scenarios and ground-truth rewards.


2. **Data Preprocessing**: Standardizes attributes, handles categorical encodings, and maps textual descriptions into structured BERT inputs (`bert_input_state`).


3. **Model Initialization**: Instantiates the `NPCMind` architecture combining a DistilBert encoder with actor-critic heads (approx. 14.18M trainable parameters).


4. **Supervised Fine-Tuning (SFT)**: Trains the model to mimic baseline tactical expert decisions using Cross-Entropy and Mean Squared Error losses.


5. **Proximal Policy Optimization (PPO)**: Implements reinforcement learning loops with advantage estimation, policy clipping, and entropy bonuses.


6. **Group Relative Policy Optimization (GRPO)**: Applies group-relative advantage normalization and KL-divergence penalties to stabilize policy drift.



---

## 📦 Project Structure

```text
├── war_npc_dataset.csv        # Generated simulation dataset (5,000 records)[cite: 1]
├── notebook.ipynb             # Main Google Colab / Jupyter Notebook containing all 16 execution steps[cite: 1]
└── README.md                  # Project documentation

```

---

## ⚙️ Installation & Requirements

To run this project locally or in Google Colab, ensure you have the following dependencies installed:

```bash
pip install torch transformers pandas numpy scikit-learn

```

---

## 🚀 Quick Start (Running the Notebook)

If you are running the project in a Jupyter or Google Colab environment with a GPU accelerator enabled (T4 recommended):

1. **Import Libraries & Setup Data**: Run **Steps 0–4** to initialize tensors and build the master train/test split.


2. **Build & Train the SFT Model**: Run **Steps 5–7** to load `distilbert-base-uncased` and execute Supervised Fine-Tuning.


3. **Evaluate Baseline Policy**: Run **Steps 8–9** to check action distributions, sensitivity tests, and human-readable policy reports.


4. **Run Reinforcement Learning (PPO & GRPO)**: Execute **Steps 10–16** to train the agent via PPO and GRPO, followed by final evaluation tests.



---

## 📊 Sample Output & Evaluation

After completing the **GRPO Final Evaluation**, the model outputs structured probabilistic decisions based on dynamic input states:

```text
STATE: Enemy distance is far. Health level is medium. Ammo level is low. Under attack: yes. Allies nearby: yes.
  [advance ]: 0.0000 
  [attack  ]: 0.0000 
  [defend  ]: 0.0000 
  [reload  ]: 0.9999 ███████████████████
  [retreat ]: 0.0000 
🏆 GRPO PREFERENCE: RELOAD

```

---

## 📄 License

This project is open-source and available under the MIT License.
