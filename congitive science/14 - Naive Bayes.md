---
tags: [cognitive-science, naive-bayes, probability]
unit: 6
lecture_pdf: 14
updated: 2026-11-10
---

# Naive Bayes — Short Notes

> [!abstract] At a glance
> **Prior × word likelihoods → score → normalize for posterior.**
> **Naive:** features are conditionally independent **given class**.
> **Priors use DOCUMENTS; likelihoods use WORD TOKENS; vocabulary uses UNIQUE WORDS.**
> Add-one: $(C(w,C)+1)/(N_C+|V|)$.
> Faculty “good movie”: $|V|=7$, class tokens=8 → denominator=15 → **Positive posterior 80%**.
> **Trap:** score 0.026667 is not posterior 0.8.


## 1. Core idea
A **classifier** assigns an input to a predefined category using features, e.g. email words → spam/not spam.

**Naive Bayes:** a classifier applying Bayes’ theorem while treating features as **conditionally independent given the class**. For spam classification, it multiplies separate word likelihoods rather than estimating every complete word combination.

**Feature** = input clue, e.g. the word “free”; **class** = output category, e.g. spam. The independence assumption ignores relationships such as “not good”.

$$
P(C\mid X)=\frac{P(X\mid C)P(C)}{P(X)}
$$
| Term | Definition | Spam example |
| --- | --- | --- |
| Prior $P(C)$ | Class probability before observing this input | Proportion of training emails labeled spam |
| Likelihood $P(X\mid C)$ | Probability of the observed features if the class is known | Likelihood of “free” in spam |
| Evidence $P(X)$ | Overall probability of the observed features across classes | Overall likelihood of observing “free” |
| Posterior $P(C\mid X)$ | Updated class probability after observing features | Probability of spam given “free” |

$P(C\mid X)$ and $P(X\mid C)$ generally differ.

**Faculty Bayes example:** $P(A)=0.20$, $P(B\mid A)=0.85$, $P(B)=0.25$:
$P(A\mid B)=0.85\times0.20/0.25=\mathbf{0.68}$.

## 2. Formulas and numerical method
For the lecture’s **multinomial word-frequency model**:
$$
P(C)=\frac{\text{documents in C}}{\text{all documents}},\qquad
P(w\mid C)=\frac{C(w,C)}{N_C}
$$
**Document** = one training review/message. **Token** = one word occurrence; “good good movie” has 3 tokens. **Vocabulary** = distinct known words; that text has 2 unique words.

$N_C$ = total word tokens in class C; $C(w,C)$ = occurrences of word w in C; $|V|$ = distinct words across the full training vocabulary. The multinomial method uses word occurrence counts.

**Laplace/add-one smoothing:** give each vocabulary word one extra count in every class; add $|V|$ to the class total to keep probabilities normalized:
$$
P(w\mid C)=\frac{C(w,C)+1}{N_C+|V|}
$$
**Score:** prior × word likelihoods, before normalization. **MAP (Maximum A Posteriori):** choose the class with the largest posterior; the largest score gives the same class:
$$
Score(C)=P(C)\prod_iP(w_i\mid C),\qquad \hat C=\arg\max_C Score(C)
$$
Count repeated test words repeatedly. The common evidence denominator is unnecessary for choosing a class.

**Normalization:** divide each score by the sum of all class scores so the resulting posterior probabilities add to 1:
$$
P(C\mid X)=\frac{Score(C)}{\sum_{C'}Score(C')}
$$
**Procedure:** document priors → class token counts → global vocabulary → word likelihoods → multiply with prior → compare → normalize if requested.

## 3. Faculty movie-review example
**Positive:** `good movie`, `good acting`, `excellent movie`, `good story`.
**Negative:** `bad movie`, `bad acting`, `poor movie`, `bad story`.

Both priors = **4/8 = 0.5**. Both classes contain **8 word tokens**. Global vocabulary size = **7**, so smoothed denominators = **8+7=15**.

| Word | Positive count | Negative count | Smoothed P(word given Pos) | Smoothed P(word given Neg) |
| --- | --- | --- | --- | --- |
| good | 3 | 0 | 4/15 | 1/15 |
| movie | 2 | 2 | 3/15 | 3/15 |
| acting | 1 | 1 | 2/15 | 2/15 |
| excellent | 1 | 0 | 2/15 | 1/15 |
| story | 1 | 1 | 2/15 | 2/15 |
| bad | 0 | 3 | 1/15 | 4/15 |
| poor | 0 | 1 | 1/15 | 2/15 |

**Classify “good movie”:**

| Method | Positive score | Negative score |
| --- | --- | --- |
| Unsmoothed | $0.5(3/8)(2/8)=0.046875$ | $0.5(0/8)(2/8)=0$ |
| Add-one | $0.5(4/15)(3/15)=2/75$ | $0.5(1/15)(3/15)=1/150$ |

After smoothing: **P(Pos given review) = 0.8**, **P(Neg given review) = 0.2** → **Positive**.

“Good” is four times as likely in Positive; “movie” has equal likelihood in both classes and provides no preference here.

## 4. Additional practice from the explanation
These are practice examples, not identified as actual PYQs.

| Review, with smoothing | Positive score | Negative score | Result |
| --- | --- | --- | --- |
| excellent story | 2/225 | 1/225 | Positive, posterior 2/3 |
| bad movie | 1/150 | 2/75 | Negative, posterior 0.8 |

**Unequal-class example:** Spam = `free win`, `free prize`, `win prize`; Not Spam = `team meeting`, `project meeting`. Classify **“free meeting”**.
- Priors: Spam **3/5**, Not Spam **2/5**; global $|V|=6$.
- Token totals: 6 and 4 → smoothing denominators **12 and 10**.
- Spam score: $(3/5)(3/12)(1/12)=0.0125$.
- Not Spam score: $(2/5)(1/10)(3/10)=0.012$.
- Normalize → **Spam ≈ 0.5102**, Not Spam ≈ 0.4898.

## 5. Limits and common mistakes
- **Zero-frequency problem:** one zero likelihood makes the entire class score zero. Smoothing prevents this for known vocabulary words.
- Independence ignores relationships such as **“not good”**; word representation affects results.
- Priors use **documents**; word likelihoods use **class token totals**; vocabulary uses **unique words**.
- Each class may have a different denominator. Always include the prior.
- **Score ≠ posterior**: divide by the sum of scores when asked for a probability.

Related: [[13 - Statistical Language Models]] · [[16 - Hidden Markov Models]]

## Test yourself — answer before expanding

> [!question]- Why can we omit P(X) when selecting a class?
> It is the same positive denominator for every class.

> [!question]- What are the three different counts?
> Documents for priors; class word tokens for likelihood denominator; unique training words for vocabulary.

> [!question]- How do scores become posteriors?
> Divide each score by the sum of class scores.


---
Source: condensed from [Organize PDF Topics](https://chatgpt.com/c/6aef17a8-9c54-83ec-8e63-e1a2ab7ed46f). Updated 10 November 2026.
