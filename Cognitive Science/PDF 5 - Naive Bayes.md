# Naive Bayes — Last-Minute Revision 🧠

## 1. Classification

**Classifier:** A system that assigns an observation to a class based on its features.

- Input: Email or document
    
- Features: Words in the input
    
- Classes: Spam / Not Spam, Positive / Negative
    
- Output: Predicted class
    

**Decision rule:** Choose the class with the highest posterior probability.

## 2. Bayes' Theorem

$$  
\boxed{P(C|X)=\frac{P(X|C)P(C)}{P(X)}}  
$$

Where:

- **Prior:** $P(C)$ — Probability of a class before observing the evidence.
    
- **Likelihood:** $P(X|C)$ — Probability of the evidence given the class.
    
- **Posterior:** $P(C|X)$ — Probability of the class given the evidence.
    
- **Evidence:** $P(X)$ — Probability of observing the evidence.
    

**Memory trick:** Prior = Before, Likelihood = Evidence under a class, Posterior = Updated belief.

### Numerical example

Given:

$$  
P(A)=0.20,\quad P(B|A)=0.85,\quad P(B)=0.25  
$$

Find $P(A|B)$:

$$  
P(A|B)=\frac{P(B|A)P(A)}{P(B)}  
$$

$$  
=\frac{0.85\times0.20}{0.25}  
=\boxed{0.68}  
$$

## 3. Naive Bayes

**Definition:** A probabilistic classification algorithm based on Bayes' Theorem that assumes features are conditionally independent given the class.

For features $X_1,X_2,\ldots,X_m$:

$$  
\boxed{P(C|X_1,\ldots,X_m)\propto P(C)\prod_{j=1}^{m}P(X_j|C)}  
$$

**Class score:**

$$  
\boxed{\text{Score}(C)=P(C)\prod_j P(X_j|C)}  
$$

### Why is it called "Naive"?

It assumes that features are conditionally independent given the class.

For example:

$$  
P(\text{free, prize, winner}|\text{Spam})  
$$

is approximated by:

$$  
P(\text{free}|\text{Spam})  
\times P(\text{prize}|\text{Spam})  
\times P(\text{winner}|\text{Spam})  
$$

This simplifies calculations, but words in real language are not necessarily independent.

## 4. Prior Probability

The prior is calculated from the number of documents in each class.

$$  
\boxed{P(C)=\frac{\text{Documents in class }C}{\text{Total documents}}}  
$$

Example: 4 Positive and 4 Negative reviews out of 8 documents.

$$  
P(\text{Positive})=\frac48=0.5  
$$

$$  
P(\text{Negative})=\frac48=0.5  
$$

## 5. Movie Review Example

### Training corpus

|Review|Class|
|---|---|
|good movie|Positive|
|good acting|Positive|
|excellent movie|Positive|
|good story|Positive|
|bad movie|Negative|
|bad acting|Negative|
|poor movie|Negative|
|bad story|Negative|

New review: **"good movie"**

### Step 1: Calculate priors

$$  
P(\text{Positive})=P(\text{Negative})=\frac48=0.5  
$$

### Step 2: Count word occurrences

|Word|Positive count|Negative count|
|---|---|---|
|good|3|0|
|movie|2|2|

Total word occurrences in each class = 8.

Vocabulary:

$$  
V={\text{good, movie, acting, excellent, story, bad, poor}}  
$$

$$  
|V|=7  
$$

### Step 3: Calculate likelihoods without smoothing

$$  
P(\text{good}|\text{Positive})=\frac38  
$$

$$  
P(\text{movie}|\text{Positive})=\frac28  
$$

$$  
P(\text{good}|\text{Negative})=\frac08=0  
$$

$$  
P(\text{movie}|\text{Negative})=\frac28  
$$

### Step 4: Calculate class scores without smoothing

**Positive:**

$$  
0.5\times\frac38\times\frac28  
=\boxed{0.046875}  
$$

**Negative:**

$$  
0.5\times0\times\frac28=\boxed{0}  
$$

The Positive score is higher, so the predicted class is **Positive**.

However, the zero score illustrates the zero-frequency problem.

## 6. Zero-Frequency Problem

**Problem:** If any feature likelihood is zero, the entire Naive Bayes class score becomes zero.

Example:

$$  
P(\text{excellent}|\text{Negative})=0  
$$

Therefore:

$$  
\text{Score}(\text{Negative})  
=P(\text{Negative})\times0\times P(\text{story}|\text{Negative})  
=0  
$$

**Solution:** Laplace (Add-One) smoothing.

## 7. Laplace Smoothing

**Definition:** A technique that prevents unseen words from receiving zero probability by adding one to each word count.

### Formula

$$  
\boxed{  
P(w|C)=\frac{\text{Count}(w,C)+1}  
{\text{TotalWords}(C)+|V|}  
}  
$$

Where:

- $\text{Count}(w,C)$ = Count of word $w$ in class $C$.
    
- $\text{TotalWords}(C)$ = Total word occurrences in class $C$.
    
- $|V|$ = Vocabulary size.
    

For our dataset:

$$  
\text{TotalWords}(C)=8,\quad |V|=7  
$$

Denominator:

$$  
8+7=15  
$$

### Calculate smoothed likelihoods

**Positive class:**

$$  
P(\text{good}|\text{Positive})  
=\frac{3+1}{8+7}  
=\frac4{15}\approx0.2667  
$$

$$  
P(\text{movie}|\text{Positive})  
=\frac{2+1}{8+7}  
=\frac3{15}=0.2  
$$

**Negative class:**

$$  
P(\text{good}|\text{Negative})  
=\frac{0+1}{8+7}  
=\frac1{15}\approx0.0667  
$$

$$  
P(\text{movie}|\text{Negative})  
=\frac{2+1}{8+7}  
=\frac3{15}=0.2  
$$

**Important:** Even an unseen word gets a nonzero probability after smoothing.

## 8. Classify "good movie" Using Smoothing

### Positive score

$$  
\begin{aligned}  
\text{Score}(\text{Positive})  
&=P(\text{Positive})\  
&\quad\times P(\text{good}|\text{Positive})\  
&\quad\times P(\text{movie}|\text{Positive})  
\end{aligned}  
$$

$$  
=0.5\times\frac4{15}\times\frac3{15}  
$$

$$  
\boxed{\text{Score}(\text{Positive})\approx0.02667}  
$$

### Negative score

$$  
\begin{aligned}  
\text{Score}(\text{Negative})  
&=0.5\times\frac1{15}\times\frac3{15}  
\end{aligned}  
$$

$$  
\boxed{\text{Score}(\text{Negative})\approx0.00667}  
$$

Since:

$$  
0.02667>0.00667  
$$

**Prediction: Positive.**

## 9. Unnormalized Score vs. Posterior Probability

Scores can be compared directly to select the most likely class, but they do not necessarily sum to 1.

To obtain the actual posterior probabilities, normalize each score.

$$  
\boxed{  
P(C_i|X)=\frac{\text{Score}(C_i)}  
{\sum_j\text{Score}(C_j)}  
}  
$$

Using the approximate scores:

$$  
\text{Total}=0.02667+0.00667=0.03334  
$$

**Positive posterior:**

$$  
P(\text{Positive}|X)  
=\frac{0.02667}{0.03334}\approx\boxed{0.80}  
$$

**Negative posterior:**

$$  
P(\text{Negative}|X)  
=\frac{0.00667}{0.03334}\approx\boxed{0.20}  
$$

Check:

$$  
0.80+0.20=1  
$$

Therefore, the estimated posterior probabilities are approximately **80% Positive and 20% Negative**.

## 10. Why Did "Good" Matter More Than "Movie"?

$$  
P(\text{good}|\text{Positive})\approx0.2667  
$$

$$  
P(\text{good}|\text{Negative})\approx0.0667  
$$

The word `good` is four times as likely under the Positive class.

But:

$$  
P(\text{movie}|\text{Positive})  
=P(\text{movie}|\text{Negative})=0.2  
$$

**Conclusion:** A feature is useful for classification when its likelihood differs across classes. In this example, `good` provides evidence favouring Positive, while `movie` does not distinguish the classes.

## 11. MAP Decision Rule

**MAP = Maximum A Posteriori.**

Choose the class with the highest posterior probability.

$$  
\boxed{  
\hat C=\arg\max_{C_i}  
\left[P(C_i)\prod_jP(X_j|C_i)\right]  
}  
$$

In simple words:

1. Calculate each class's prior.
    
2. Calculate feature likelihoods.
    
3. Multiply the prior by the likelihoods.
    
4. Compare class scores.
    
5. Choose the highest-scoring class.
    

Normalize the scores if actual posterior probabilities are required.

## 12. Limitation of Naive Bayes

Consider:

**"not good"**

The word `good` normally suggests positive sentiment, but `not` reverses the meaning.

Because Naive Bayes assumes conditional independence, it may fail to capture this relationship adequately.

**Main limitation:** The conditional-independence assumption can ignore important relationships between features.

---

## Final Rapid Revision

|Term|Key point|
|---|---|
|Classifier|Assigns an observation to a class|
|Prior|Probability before observing evidence|
|Likelihood|Probability of evidence given a class|
|Posterior|Probability of a class given evidence|
|Bayes' Theorem|Updates beliefs using evidence|
|Naive Bayes|Uses Bayes' Theorem and conditional independence|
|Zero-frequency problem|One zero likelihood makes the class score zero|
|Laplace smoothing|Adds one to counts to prevent zero probabilities|
|Class score|Prior × product of likelihoods|
|Normalization|Divides each score by the sum of scores|
|MAP|Selects the highest-scoring class|
|Main limitation|May miss relationships such as "not good"|

## Formulas to Memorize

**Bayes' Theorem**

$$  
P(C|X)=\frac{P(X|C)P(C)}{P(X)}  
$$

**Prior**

$$  
P(C)=\frac{\text{Documents in class }C}{\text{Total documents}}  
$$

**Naive Bayes score**

$$  
\text{Score}(C)=P(C)\prod_jP(X_j|C)  
$$

**Laplace smoothing**

$$  
P(w|C)=\frac{\text{Count}(w,C)+1}{\text{TotalWords}(C)+|V|}  
$$

**Posterior normalization**

$$  
P(C_i|X)=\frac{\text{Score}(C_i)}{\sum_j\text{Score}(C_j)}  
$$

### Five things to remember before the quiz

1. **Prior, likelihood, posterior:** Before evidence, evidence given a class, and class given evidence.
    
2. **Naive Bayes:** Assumes conditional independence given the class.
    
3. **Laplace smoothing:** Adds one to word counts to prevent zero likelihoods.
    
4. **MAP:** Choose the class with the highest score.
    
5. **"Good movie" example:** Positive score ≈ 0.02667, Negative score ≈ 0.00667, giving approximately 80% Positive and 20% Negative after normalization.