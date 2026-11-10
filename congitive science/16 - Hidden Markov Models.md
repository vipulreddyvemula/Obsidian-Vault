---
tags: [cognitive-science, hmm, probability]
unit: 6
lecture_pdf: 16
updated: 2026-11-10
---

# Hidden Markov Models — Short Notes

> [!abstract] At a glance
> **HMM = hidden states + observed evidence.** $\lambda=(A,B,\pi)$.
> **Transition:** state→state. **Emission:** state→observation.
> **Forward = SUM. Viterbi = MAX + backtrack. Baum–Welch = LEARN.**
> Weather U,U,no umbrella → **RRS**; joint **0.06804**, observation probability **0.120445**.
> **2024 Q11:** NNN; joint **0.000512**. Include START/END and use the given tags.


## 1. Core idea and components
An **HMM** infers hidden states from observable evidence over time: weather is hidden; umbrella use is observed. A Markov chain observes the states directly.

$$
\lambda=(A,B,\pi)
$$
- $\pi_j=P(S_1=j)$: initial-state probability.
- $A_{ij}=P(S_t=j\mid S_{t-1}=i)$: **transition**, hidden state → hidden state.
- $B_j(o)=P(O_t=o\mid S_t=j)$: **emission**, hidden state → observation.
- **First-order Markov assumption:** next state depends only on the current state.
- **Emission assumption:** each observation depends only on its current hidden state.

## 2. Three HMM problems

| Problem | What to find | Algorithm |
| --- | --- | --- |
| Evaluation | Total observation probability $P(O\mid\lambda)$ | Forward: **sum** paths |
| Decoding | Most probable hidden-state sequence | Viterbi: **max** path |
| Learning | Estimate $A,B,\pi$ | Baum–Welch: EM |

**Baum–Welch:** initialize parameters → estimate hidden-state/transition probabilities given observations → update parameters → repeat.

## 3. Essential formulas
**One path’s joint probability:**
$$
P(Q,O\mid\lambda)=\pi_{q_1}B_{q_1}(o_1)\prod_{t=2}^{T}A_{q_{t-1},q_t}B_{q_t}(o_t)
$$
Initial × first emission × each subsequent transition and emission.

**Viterbi initialization and recurrence:**
$$
\delta_1(j)=\pi_jB_j(o_1),\qquad
\delta_t(j)=B_j(o_t)\max_i[\delta_{t-1}(i)A_{ij}]
$$
Store the best predecessor for **each state**; select the final maximum and **backtrack**. Include END transitions if specified. Complexity: $O(TK^2)$ for K states, versus $K^T$ brute-force paths.

**Forward:** same initialization, but replace max with sum:
$$
\alpha_t(j)=B_j(o_t)\sum_i\alpha_{t-1}(i)A_{ij},\qquad P(O)=\sum_j\alpha_T(j)
$$
**Posterior:** $P(Q\mid O)=P(Q,O)/P(O)$. Joint probability and posterior are different.

## 4. Faculty example — Rainy/Sunny
State order R, S; $\pi=[0.5,0.5]$. Observations: **U, U, No umbrella**.

| State | Next R | Next S | Umbrella | No umbrella |
| --- | --- | --- | --- | --- |
| R | 0.7 | 0.3 | 0.9 | 0.1 |
| S | 0.3 | 0.7 | 0.2 | 0.8 |

Each transition row and each emission row sums to 1 separately.

**Viterbi table:**

| State | Day 1: U | Day 2: U | Day 3: No umbrella |
| --- | --- | --- | --- |
| R | 0.45 | 0.2835 | 0.019845 |
| S | 0.10 | 0.027 | **0.06804** |

Example cell: $\delta_2(S)=0.2\max(0.45\times0.3,0.10\times0.7)=0.027$.

Backtrack: **R → R → S**. Joint probability:
$0.5\times0.9\times0.7\times0.9\times0.3\times0.8=0.06804$.

**Forward table:**

| State | Day 1 | Day 2 | Day 3 |
| --- | --- | --- | --- |
| R | 0.45 | 0.3105 | 0.022965 |
| S | 0.10 | 0.041 | 0.09748 |

$P(U,U,\text{No umbrella})=0.120445$; posterior of RRS $=0.06804/0.120445\approx0.5649$.

## 5. November 2024 Q11 — “he raises purses”
**Training corpus:** `their/N raises/N`; `he/N raises/V`; `my/N purses/N`.
Use the supplied tags exactly, even when they differ from ordinary grammar.

**Transition MLE:** count(source → destination) ÷ all outgoing transitions from source, **including END**.

| From / To | N | V | END |
| --- | --- | --- | --- |
| START | 1 | 0 | 0 |
| N | 2/5 | 1/5 | 2/5 |
| V | 0 | 0 | 1 |

N has **5** outgoing transitions, not 3. There are no observed transitions into START.

**Emission MLE:** count(word, tag) ÷ total occurrences of tag.
- N: `their`, `raises`, `he`, `my`, `purses` each have probability **1/5**.
- V: `raises` has probability **1**; other words have probability **0**.

| Tag | he | raises | purses |
| --- | --- | --- | --- |
| N | 0.2 | 0.016 | 0.00128 |
| V | 0 | 0.04 | 0 |

Terminate: $0.00128\times P(END\mid N)=0.000512$.

**Answer: he/N raises/N purses/N.** Joint probability **0.000512**; normalized posterior **1** under this unsmoothed model. NVN fails because $P(N\mid V)=0$. Do not choose the largest intermediate score greedily.

## 6. Applications and limits
- **POS tagging:** hidden states = tags; observations = words.
- Also speech perception, noisy-sensor inference and modeling attention.
- Limited history and simplified emissions miss long-range relationships.
- A model fitting behavior does not establish that the brain uses that algorithm.

**Recall:** Forward = sum; Viterbi = max + backtrack; Baum–Welch = learn.

Related: [[13 - Statistical Language Models]] · [[14 - Naive Bayes]]

## Test yourself — answer before expanding

> [!question]- Why is Forward different from Viterbi?
> Forward sums over paths for P(O); Viterbi retains the best path per state and backtracks.

> [!question]- Why does the PYQ give NNN instead of NVN?
> The unsmoothed training data gives V→N probability 0.

> [!question]- Is 0.06804 the posterior of RRS?
> No. It is the joint probability. Divide by 0.120445 for posterior ≈ 0.5649.


---
Source: condensed from [Organize PDF Topics](https://chatgpt.com/c/6aef17a8-9c54-83ec-8e63-e1a2ab7ed46f). Updated 10 November 2026.
