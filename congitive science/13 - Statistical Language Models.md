---
tags:
  - cognitive-science
  - language-models
unit: 6
lecture_pdf: 13
---

# Statistical Language Models — Short Notes

> **Core idea:** Learn word patterns from text to predict the next word and assign probabilities to sentences.

## 1. Language model
- Estimates $P(W)=P(w_1,\ldots,w_n)$ for a word sequence.
- Applications: keyboard prediction, speech recognition, spell correction and translation.
- **Notation:** $P(A\mid B)$ means “probability of A given B”.

## 2. Chain rule vs. Markov assumption
**Chain rule — exact; uses the full history:**
$$
P(w_1,\ldots,w_n)=\prod_{i=1}^{n}P(w_i\mid w_1,\ldots,w_{i-1})
$$
Example: $P(I,love,NLP)=0.2\times0.4\times0.5=0.04$ (illustrative probabilities).

**Markov assumption — approximation; uses only recent words:**
$$
P(w_i\mid w_1,\ldots,w_{i-1})\approx P(w_i\mid w_{i-k},\ldots,w_{i-1})
$$
Remember **k previous words**, reducing the data needed to estimate probabilities.

## 3. N-grams
An **N-gram** is a sequence of N consecutive words. An N-gram model uses **N−1 previous words** as context.

| Model | Context | Next-word probability |
| --- | --- | --- |
| Unigram | None | $P(w_i)$ |
| Bigram | Previous 1 word | $P(w_i\mid w_{i-1})$ |
| Trigram | Previous 2 words | $P(w_i\mid w_{i-2},w_{i-1})$ |

For “I love NLP”, a bigram model uses:
$$
P(I,love,NLP)\approx P(I)P(love\mid I)P(NLP\mid love)
$$

## 4. Maximum Likelihood Estimation (MLE)
Estimate probabilities using observed counts:
$$
P(b\mid a)=\frac{C(a,b)}{C(a)}
$$
$C(a,b)$ = occurrences of the pair; $C(a)$ = occurrences of the preceding context with a next token to predict.

**Lecture corpus:** `I like NLP` · `I like AI` · `I love NLP` · `I like ML`

| Probability | Calculation | Result |
| --- | --- | --- |
| $P(like\mid I)$ | 3/4 | 0.75 |
| $P(love\mid I)$ | 1/4 | 0.25 |
| $P(NLP\mid like)$ | 1/3 | ≈ 0.333 |
| $P(NLP\mid love)$ | 1/1 | 1 |
| $P(NLP\mid I)$ | 0/4 | 0 |

**Sentence example:** Using the explanation’s first-word convention, $P(I)=4/12$:
$$
P(I,like,NLP)\approx\frac{4}{12}\times\frac34\times\frac13=\frac1{12}\approx0.0833
$$
A model with a START token uses $P(I\mid\text{START})$ instead; follow the convention specified in the question.

## 5. Limitations
- **Data sparsity:** Many possible N-grams have few or no observations. Larger N means more context but more sparsity.
- **Zero-frequency problem:** One unseen N-gram gets probability 0 under MLE, making the whole sequence probability 0.
- **OOV:** A word outside the known vocabulary. Different from an unseen combination of known words.
- **Long-distance dependencies:** A short context may miss distant relationships, e.g. **keys … are**, even when “hallway” immediately precedes “are”.

## 6. Laplace / add-one smoothing
Add 1 to each possible next-word count:
$$
P_{\text{Laplace}}(b\mid a)=\frac{C(a,b)+1}{C(a)+|V|}
$$
Here $|V|$ = vocabulary size. The corpus has **6 distinct words**.

- $P(NLP\mid I)=(0+1)/(4+6)=\mathbf{0.1}$.
- $P(like\mid I)=(3+1)/(4+6)=\mathbf{0.4}$.
- Redistributes probability from observed combinations to unseen combinations.
- Does **not** automatically handle OOV words; vocabulary handling is still needed.

## 7. Evaluation and perplexity
- **Extrinsic:** Test usefulness in an application, e.g. improved speech recognition.
- **Intrinsic:** Evaluate prediction directly, often using perplexity.

$$
PP(W)=P(W)^{-1/N}
$$
$N$ = number of predicted tokens under the scoring convention.

For $N=2$: $P(W)=1/16\Rightarrow PP=4$; $P(W)=1/4\Rightarrow PP=2$.

**Lower perplexity means better prediction** when test data, tokenization and scoring conventions are comparable.

## 8. Naive Bayes — introduction
Classifies text, e.g. spam / not spam:
$$
P(C\mid W)=\frac{P(W\mid C)P(C)}{P(W)}
$$
- **Prior:** $P(C)$; **likelihood:** $P(W\mid C)$; **posterior:** $P(C\mid W)$.
- “Naive” assumption: word features are conditionally independent **given the class**.
- Detailed Naive Bayes numericals belong to PDF 14.

## Quick recall
- **Chain rule = exact; Markov = limited-history approximation.**
- **Trigram → 2 previous words.**
- **MLE = pair count ÷ context count.**
- **Laplace = add 1 above, add vocabulary size below.**
- **Unseen N-gram ≠ OOV word.**
- **Lower comparable perplexity = better prediction.**
- These ideas prepare you for **PDF 16 — Hidden Markov Models**.

---
Source: condensed from the last explanation in [Organize PDF Topics](https://chatgpt.com/c/6aef17a8-9c54-83ec-8e63-e1a2ab7ed46f), “Unit 6, Part 1: Statistical Language Models”.
