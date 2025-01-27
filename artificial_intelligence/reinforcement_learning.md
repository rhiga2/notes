# Intro to Reinforcement Learning
## Markov Decision Processes (MDP)
* MDPs consist of $(S, A, T, r)$ (assuming full observability).
  * $S$ = state space
  * $A$ = action space
  * $T$ = transition function, probability of next state given current start, action $p(s' | s, a)$
  * $r$ = rewards function given state and action $r(s, a)$
* Usually we don't know transition function completely.

## Goal of Reinforcement Learning
* A trajectory is a sequence of states and actions taken $\tau = \[(s_1, a_1), ..., (s_T, a_T)\]$. We want to discount rewards (payoff) over this trajectory.
```math
\begin{aligned}
R(\tau) &= r(s_1, a_1) + \gamma r(s_2, a_2) + ... + \gamma^{T - 1} r(s_T, a_T)  \\
  &= r_1 + \gamma r_2 + ... + \gamma^{T-1} r^T = \sum_{t=1}^T \gamma^{t-1} r_t
\end{aligned}
```
* Given MDP, we want to find a policy $\pi$ indicately which actions to taken given current state $p(a | s)$.
* Our objective is to maximize the expected payoff over a trajectory sampled from our policy.
```math
\max_\pi E_{\tau \sim p_{\pi}} \left[ R(\tau) \right] \equiv \max_\pi \sum_{t=1}^T E_{(s_t, a_t) \sim p_{\pi}} \left[ r_t \right] 
```

## Quality, Value, and Advantage Functions
* Quality function tells us what is the future payoff we can expect given we take action $a$ from state $s$. We denote the future trajectory as $\tau_t = [(s_t, a_t), (s_{t+1}, a_{t+1}), ..., (s_T, a_T)]$
```math
Q^{\pi}(s, a) = E_{\tau_t \sim p_\pi } \left[ R(\tau_t) | s_t=s, a_t=a \right]
```
* The value function tells us what the future payoff we can expect given we are in state $s$.
```math
V^{\pi}(s) = E_{\tau_t \sim p_\pi } \left[ R(\tau_t) | s_t=s \right]
```
* By the tower rule, the value function is the expected Q-function over actions in state $s$.
```math
V^{\pi}(s) = E_{a \sim p_{\pi} } \left[ Q(s, a) \right]
```
* The advantage refers to how much better off (or worse off) we are by taking action $a$ compared to average payoff from state $s$.
```math
A^{\pi}(s, a) = Q^{\pi}(s, a) - V^{\pi}(s)
```
