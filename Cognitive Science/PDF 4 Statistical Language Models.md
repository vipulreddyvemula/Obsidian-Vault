# Statistical Language Models — Quick Revision 🧠

## 1. Statistical Language Model

**Definition:** A model that assigns probabilities to sequences of words.

[  
$P(W)=P(w_1,w_2,\ldots,w_n)$  
]

**Applications:** Predictive keyboards, speech recognition, spell correction, and machine translation.

**Key idea:** More probable word sequences are generally more natural according to the model's learned language patterns.

## 2. Chain Rule of Probability

The Chain Rule expresses the probability of a complete sentence as a product of conditional probabilities.

[  
$P(w_1,\ldots,w_n)$  
$=P(w_1)\prod_{i=2}^{n}P(w_i\mid w_1,\ldots,w_{i-1})$  
]

Example:

[  
$P(I\ love\ NLP)$  
$=P(I)\times P(love\mid I)\times P(NLP\mid I,love)$  
]

**Problem:** The context grows with sentence length, making probability estimation difficult.

## 3. Markov Assumption

**Definition:** Approximate the next-word probability using only a limited number of preceding words instead of the entire history.

[  
$P(w_n\mid w_1,\ldots,w_{n-1})$  
$\approx P(w_n\mid w_{n-k},\ldots,w_{n-1})$  
]

**Purpose:** Reduce computational complexity by limiting the context.

## 4. N-gram Models

An N-gram model uses the previous **(N-1) words** to predict the next word.

| Model   | Previous words used | Formula                              |
| ------- | ------------------- | ------------------------------------ |
| Unigram | 0                   | $(P(w_i))$                           |
| Bigram  | 1                   | (P(w_i\mid w_{i-1}))                 |
| Trigram | 2                   | (P(w_i\mid w_{i-2},w_{i-1}))         |
| 4-gram  | 3                   | (P(w_i\mid w_{i-3},w_{i-2},w_{i-1})) |

**Why not use a very large N?**

- Too many possible combinations.
    
- Data sparsity.
    
- High computational and storage costs.
    

**Trade-off:** Small N gives less context but more reliable counts; large N gives more context but increases data sparsity.

## 5. Bigram Model and MLE

**MLE = Maximum Likelihood Estimation.**

It estimates probabilities from observed counts.

### Formula

[  
\boxed{  
P(w_i\mid w_{i-1})  
=\frac{\operatorname{Count}(w_{i-1},w_i)}  
{\operatorname{Count}(w_{i-1})}  
}  
]

### Example

Training corpus:

- I like NLP
    
- I like AI
    
- I love NLP
    
- I like ML
    

Count of `I` = 4.

Count of the bigram `I like` = 3.

Therefore:

[  
P(like\mid I)=\frac{3}{4}=\boxed{0.75}  
]

For `pizza`:

[  
P(pizza\mid I)=\frac{0}{4}=\boxed{0}  
]

**MLE pipeline:** Corpus → Count words and word pairs → Normalize → Probability table.

## 6. Long-Distance Dependencies

A **long-distance dependency** occurs when words separated by other words have an important grammatical or semantic relationship.

Example:

"The keys to the old wooden cabinet in the hallway are missing."

The plural subject `keys` determines the use of `are`.

A bigram model sees only the immediately preceding word, `hallway`, and may predict `is`.

**Problem:** Short-context models can miss relationships between distant words.

## 7. Data Sparsity and OOV

**Data sparsity:** Many possible word combinations occur rarely or never in the training corpus.

For a vocabulary of 10,000 words:

[  
\text{Possible bigrams}=10{,}000^2=100{,}000{,}000  
]

[  
\text{Possible trigrams}=10{,}000^3=1{,}000{,}000{,}000{,}000  
]

**OOV = Out of Vocabulary:** A word that is not present in the model's vocabulary.

### Why is zero probability a problem?

Sentence probability is a product of probabilities:

[  
P(w_1,\ldots,w_n)=\prod_i P(w_i\mid context)  
]

If any factor is zero, the entire sentence probability becomes zero.

## 8. Smoothing — Laplace (Add-One)

**Smoothing:** Adjusts probability estimates to give unseen events nonzero probability.

### Formula

[  
\boxed{  
P_{\text{Laplace}}(w_i\mid w_{i-1})  
=\frac{\operatorname{Count}(w_{i-1},w_i)+1}  
{\operatorname{Count}(w_{i-1})+|V|}  
}  
]

Where:

- Count of the bigram = observed word-pair frequency.
    
- Count of the preceding word = frequency of the context word.
    
- (|V|) = vocabulary size.
    
- Add one to the numerator and add vocabulary size to the denominator.
    

### Example

Suppose:

- Count of `I` = 4.
    
- Count of `I pizza` = 0.
    
- Vocabulary size = 10.
    

[  
P_{\text{Laplace}}(pizza\mid I)  
=\frac{0+1}{4+10}  
=\boxed{\frac{1}{14}\approx0.0714}  
]

**Remember:** MLE may assign zero to unseen N-grams; Laplace smoothing prevents this.

## 9. Evaluating Language Models

### Extrinsic evaluation

Evaluates a language model within a real application.

Example: Testing whether speech recognition improves when the language model is used.

### Intrinsic evaluation

Evaluates the language model directly using metrics such as perplexity.

### Perplexity

Measures how well a language model predicts a test sequence.

[  
\boxed{\text{Lower perplexity}=\text{Better predictive performance}}  
]

This comparison applies when evaluating models on the same test data under comparable conditions.

## 10. Language Model vs. Classifier

Consider the message:

"Win a FREE iPhone. Click here now!"

**Language model:**

[  
P(\text{sentence})  
]

Question: How probable is this word sequence?

**Text classifier:**

[  
P(\text{SPAM}\mid\text{sentence})  
]

Question: Given this sentence, how probable is the SPAM class?

**Difference:** A language model estimates sequence probability; a classifier estimates class probability given the input.

## 11. Naive Bayes

**Definition:** A probabilistic classification method based on Bayes' Theorem and a conditional-independence assumption.

### Bayes' Theorem

[  
\boxed{  
P(C\mid X)=\frac{P(X\mid C)P(C)}{P(X)}  
}  
]

Where:

- (P(C\mid X)) = posterior probability.
    
- (P(X\mid C)) = likelihood.
    
- (P(C)) = prior probability.
    
- (P(X)) = evidence.
    

### Naive Bayes Assumption

Features are assumed to be conditionally independent given the class.

For a spam message containing `free`, `prize`, and `click`:

[  
\begin{aligned}  
&P(free,prize,click\mid SPAM)\  
&\approx P(free\mid SPAM)\  
&\quad\times P(prize\mid SPAM)\  
&\quad\times P(click\mid SPAM)  
\end{aligned}  
]

This simplifies the calculation, although the words are not necessarily independent in real messages.

## 12. Markov vs. Naive Bayes Assumption

|Markov Assumption|Naive Bayes Assumption|
|---|---|
|Limits preceding context|Assumes conditional independence of features given the class|
|Used in N-gram language models|Used in classification|
|Predicts the next word|Predicts the class|

---

# Must-Memorize Formulas

**1. Chain Rule**

[  
P($w_1,\ldots,w_n)$  
$=P(w_1)\prod_{i=2}^{n}P(w_i\mid w_1,\ldots,w_{i-1})$  
]

**2. Bigram MLE**

[  
P(w_i\mid w_{i-1})  
=\frac{\operatorname{Count}(w_{i-1},w_i)}  
{\operatorname{Count}(w_{i-1})}  
]

**3. Laplace Smoothing**

[  
P_{\text{Laplace}}(w_i\mid w_{i-1})  
=\frac{\operatorname{Count}(w_{i-1},w_i)+1}  
{\operatorname{Count}(w_{i-1})+|V|}  
]

**4. Bayes' Theorem**

[  
P(C\mid X)=\frac{P(X\mid C)P(C)}{P(X)}  
]

# Final Rapid Recall

1. **Unigram:** 0 previous words.
    
2. **Bigram:** 1 previous word.
    
3. **Trigram:** 2 previous words.
    
4. **MLE:** Learn probabilities from counts.
    
5. **Data sparsity:** Many possible N-grams are unseen.
    
6. **OOV:** Out-of-Vocabulary word.
    
7. **Smoothing:** Gives unseen events nonzero probability.
    
8. **Laplace smoothing:** Add one to each N-gram count.
    
9. **Perplexity:** Lower generally means better predictive performance.
    
10. **Extrinsic evaluation:** Evaluate inside an application.
    
11. **Naive Bayes:** Uses Bayes' Theorem and conditional independence.
    
12. **Language model:** Estimates $(P(\text{sentence})).$
    
13. **Classifier:** Estimates $(P(\text{class}\mid\text{sentence})).$
    

**Revision priority:** Practise the bigram MLE calculation and Laplace smoothing first, then revise the N-gram definitions, Markov Assumption, perplexity, and Naive Bayes.