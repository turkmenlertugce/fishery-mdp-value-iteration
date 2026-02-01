# MDP Value Iteration for Fishery Management

This repository contains a Python implementation of **Value Iteration** to solve a **Markov Decision Process (MDP)** modeling a sustainable fish harvesting problem. The project was developed as part of **CENG461 – Artificial Intelligence** coursework.

## Problem Description

A lake contains a fish population with a maximum carrying capacity. Each year:
- A decision must be made on how many fish to harvest
- The remaining population grows stochastically according to several possible growth rates

The objective is to **maximize the long-term discounted reward**, where the reward is the number of fish harvested each year, while accounting for uncertainty in population growth.

## Markov Decision Process Formulation

- **States (s):** Current fish population  
  \( 0 \leq s \leq M \)

- **Actions (a):** Number of fish harvested  
  \( 0 \leq a \leq s \)

- **Transition Model:**  
  The next state depends on stochastic growth rates:
  - Growth rates: {1.0, 1.25, 1.5, 1.75}
  - Each growth rate has an associated probability

  \[
  s' = \min(\text{round}((s - a) \times R), M)
  \]

- **Reward Function:**  
  \[
  R(s, a) = a
  \]

- **Discount Factor:**  
  \( \gamma = 0.9 \)

## Solution Method

The optimal policy is computed using **Value Iteration**, based on the Bellman optimality equation:

\[
U_{k+1}(s) = \max_a \left[ R(s,a) + \gamma \sum_{s'} P(s' \mid s,a) U_k(s') \right]
\]

The algorithm iteratively updates state utilities and extracts the optimal action for each state.

## Implementation Details

- Transition probabilities explicitly computed for each growth rate
- Population capped at the maximum capacity
- Tie-breaking handled by rounding up when needed
- Policy and utility values printed after iterations

## Technologies Used

- Python
- NumPy

