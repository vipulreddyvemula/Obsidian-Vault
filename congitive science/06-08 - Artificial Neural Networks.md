---
tags: [cognitive-science, ann, revision]
unit: 2
lecture_pdfs: [6, 7, 8]
updated: 2026-11-10
---

# Artificial Neural Networks — Revision Notes

> [!abstract] At a glance
> **Neuron:** $z=\sum w_ix_i+b$, then $a=f(z)$.
> **Training:** Forward → Loss → Backpropagate → Update → Repeat.
> **Backprop calculates gradients; gradient descent updates parameters.**
> **Single perceptron:** linear boundary; OR works, XOR does not.
> **Must practise:** perceptron PYQ, 2–2–1 forward pass, six-weight backprop table.

## 1. Neuron, bias and architecture
- Traditional programming: data + written rules → answers. ML training: data + answers → learned model.
- Inputs = evidence; weights = influence; bias = baseline; activation = output transformation.
- **Bias shifts the boundary**, independently of weight orientation: $w^Tx+b=0$. A raw threshold $\theta$ is equivalent to bias $b=-\theta$.
- **Input → hidden → output layers.** Hidden neurons learn useful representations through weight changes. A 28×28 grayscale image has **784 inputs**.
- Vectorized layer, using faculty notation: $Z=W^TX+b$; apply $f$ element by element. Check dimensions.

## 2. Activation functions — memorize this table

| Function | Formula | Range / key point |
| --- | --- | --- |
| Step | 1 if $z\ge0$, else 0 | Binary; unsuitable for ordinary gradient backprop |
| Sigmoid | $\sigma(z)=1/(1+e^{-z})$ | (0,1); $\sigma(0)=0.5$ |
| Tanh | $(e^z-e^{-z})/(e^z+e^{-z})$ | (−1,1); zero-centered |
| ReLU | $\max(0,z)$ | [0,∞); suppress negatives |
| Leaky ReLU | $z$ if nonnegative; $0.01z$ otherwise | Small negative-side slope |

**Why nonlinear?** Stacking only affine layers still gives one affine transformation.

## 3. Small faculty numericals

| Example | Weighted sum | Result |
| --- | --- | --- |
| Umbrella: inputs rain/cloud/sun/wind = 0/1/0/1, weights 5/2/−2/1 | 3 | Threshold 4 → 0; rain=1 makes sum 8 → 1 |
| $x=(2,1),w=(0.8,-0.5),b=-0.2$ | 0.9 | Step 1; ReLU 0.9; sigmoid 0.711; tanh 0.716 |
| $x=(1,2),w=(-1,0.5),b=-0.5$ | −0.5 | Step 0; ReLU 0; sigmoid 0.378; tanh −0.462 |

> [!tip] Numerical routine
> **Multiply → sum → add bias → activate.** Never apply sigmoid/ReLU to each input separately.

## 4. PDF 07 — 2–2–1 forward pass
Input $x=(1,0.5)$; hidden activation ReLU; output sigmoid.

1. $z_1=0.8(1)+0.4(0.5)-0.2=0.8\Rightarrow h_1=0.8$.
2. $z_2=-0.5(1)+0.6(0.5)+0.1=-0.1\Rightarrow h_2=0$.
3. $z_o=0.7h_1-0.4h_2-0.1=0.46$.
4. $\hat y=\sigma(0.46)=\mathbf{0.6130}$ → class 1 at threshold 0.5.

## 5. Learning — essential formulas
For the faculty’s **sigmoid + half squared-error** network:
$$
L=\tfrac12(y-\hat y)^2,\qquad \sigma'(z)=\sigma(z)(1-\sigma(z))
$$
$$
\delta_o=(\hat y-y)\hat y(1-\hat y)
$$
$$
\delta_h=\delta_o\,w_{h\to o}\,h(1-h),\qquad
\frac{\partial L}{\partial w}=\delta\times\text{input to the weight}
$$
$$
w'=w-\eta\frac{\partial L}{\partial w},\qquad b'=b-\eta\delta
$$
- **Positive gradient → decrease weight; negative → increase.** Large learning rates can overshoot.
- **Epoch:** one full dataset pass; not necessarily one update.
- Random initialization breaks symmetry between otherwise identical hidden neurons.

> [!warning] Backprop traps
> Use **old weights** for every gradient, then update together. Include the sigmoid derivative and the input multiplier. The delta formula above is for this loss/activation combination.

## 6. PDF 08 — main training numerical
**Given:** $x=(1,2)$; target $y=1$; learning rate $\eta=0.1$; sigmoid throughout.

| Neuron | Weights | Bias | Sum | Activation |
| --- | --- | --- | --- | --- |
| Hidden 1 | $w_1=0.2,w_2=0.4$ | 0.1 | 1.1 | 0.7503 |
| Hidden 2 | $w_3=0.5,w_4=0.3$ | 0.2 | 1.3 | 0.7858 |
| Output | $w_5=0.6,w_6=0.8$ | 0.3 | 1.3788 | **0.7988** |

$L\approx0.0202$; $\delta_o\approx-0.03234$; $\delta_{h1}\approx-0.003635$; $\delta_{h2}\approx-0.004354$.

**One update:**

| Weight | Gradient | New value |
| --- | --- | --- |
| $w_1$ | −0.003635 | 0.2004 |
| $w_2$ | −0.007271 | 0.4007 |
| $w_3$ | −0.004354 | 0.5004 |
| $w_4$ | −0.008707 | 0.3009 |
| $w_5$ | −0.024260 | 0.6024 |
| $w_6$ | −0.025411 | 0.8025 |

Example: $\partial L/\partial w_2=\delta_{h1}x_2\approx-0.007271$; $w'_2=0.4-0.1(-0.007271)$.
Bias updates, if requested: **0.10036, 0.20044, 0.30323**. The faculty’s main table updates only weights.

## 7. CNNs — why images need them
Fully connected image networks have many parameters, inefficient spatial processing and overfitting risk. 100×100 grayscale pixels → 100 neurons needs **1,000,000 weights**, excluding biases.

**CNN:** local connectivity + shared filters + learned features + pooling. A single-channel 3×3 filter has **9 weights**, reused across positions. Hierarchy: pixels → edges → shapes → objects.

Architecture cues: **CNN = spatial/images; RNN = sequences; Transformer = attention; GAN = generation; reinforcement learning = rewards.**

## 8. PYQ patterns
- **2023/2025 perceptron:** $w=(0.5,-0.7),b=0.1,x=(1,2)$ → $z=-0.8$, sigmoid **0.3100**. Boundary $0.5x_1-0.7x_2+0.1=0$.
- **2024 Q2:** general boundary; OR vs XOR; backprop role. Diagram labels unavailable in the source, so only the general boundary is supplied.
- **OR:** only (0,0) is negative; $x_1+x_2=0.5$ separates classes. **XOR:** (0,1),(1,0) positive; opposite corners cannot be separated by one line.
- Memory subparts in Q2: **implicit memory** lacks conscious recollection; **chunking** groups items into meaningful units, e.g. `1947 | 2026`. Full Memory PDF remains separate.

## Test yourself — answer before expanding

> [!question]- What are the four steps of a neuron numerical?
> Multiply inputs by weights → sum → add bias → apply activation.

> [!question]- How does backprop differ from gradient descent?
> Backprop uses the chain rule to calculate gradients; gradient descent uses them to change weights/biases.

> [!question]- Why can a multilayer nonlinear network represent more than a single perceptron?
> Nonlinear activations allow nonlinear decision regions; one perceptron has a linear boundary and cannot solve XOR.

---
Source: condensed from the latest ANN and Linguistics/NLP explanations in [Organize PDF Topics](https://chatgpt.com/c/6aef17a8-9c54-83ec-8e63-e1a2ab7ed46f). Checked 10 November 2026.
