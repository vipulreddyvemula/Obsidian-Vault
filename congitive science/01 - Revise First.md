---
tags: [cognitive-science, revision]
updated: 2026-11-10
---

# Revise First — Recall Sheet

> [!tip] How to use
> Use this as a recall sheet after reading the subject notes. Those contain short definitions and examples; this page brings back the key cues and formulas. Explain each cue without looking, then do the drill.

## Language — five words to remember
**Sounds → Words → Sentences → Meaning → Context**

| Cue | Answer |
| --- | --- |
| Lexical ambiguity | One word, multiple meanings: bat = animal / sports equipment |
| Syntactic / structural ambiguity | Different grammatical groupings: telescope used by me / carried by the man |
| Semantic interpretation | Different sentence meanings: chicken eats / is eaten; can overlap structural ambiguity |
| Lexical / compositional semantics | Word meaning / meanings combined through grammar |
| Phonology / morphology | Sound patterns / word structure |
| Syntax / semantics / pragmatics | Sentence structure / meaning / meaning in context |
| Phoneme / morpheme | Contrastive sound / meaningful unit |
| Stemming / lemmatization | Chop to root, possibly nonword / dictionary base |
| BoW / TF-IDF / embeddings | Counts / importance / semantic vectors |
| POS / parsing / NER | Word categories / phrase structure / real-world entities |

**NLP pipeline:** Clean → Tokenize → selected Stopwords → Normalize → Vectorize → Classify. Keep negation when it affects meaning.

**Acquisition:** babbling → one word → two words → telegraphic → complex language. **Sapir–Whorf:** influence, not total control.

→ [[11-12 - Linguistics and NLP]]

## POS & parsing — exam cues
**VBD = past; VBN = participle; VBG = -ing; VBZ = she eats; VBP = they eat.**

Bought/**VBD**; was/**VBD** purchased/**VBN**; very/**RB**; their/**PRP$**; three/**CD**.

**Tree:** S→NP VP; NP→DET NOM; NOM→ADJ NOM or NOUN; VP→VP PP or VERB; PP→PREP NP.

Two adjectives = two NOM expansions. Read leaves in sentence order.

→ [[11-12 - POS and Parsing Practice]]

## ANN — compute in this order
**Weighted sum → bias → activation → loss → gradients → update.**

$$
z=\sum_iw_ix_i+b,\quad\sigma(z)=\frac1{1+e^{-z}},\quad ReLU(z)=\max(0,z)
$$
$$
L=\tfrac12(y-\hat y)^2,\quad\delta_o=(\hat y-y)\hat y(1-\hat y),\quad w'=w-\eta(\delta\times input)
$$
**Backpropagation calculates loss gradients; gradient descent uses them to update parameters.** A gradient measures how loss changes with a parameter. Use old weights in all gradients. **OR is linearly separable; XOR is not.** CNNs reuse local filters across images.

→ [[06-08 - Artificial Neural Networks]]

## Probability — keep these three models separate

| Topic | Essential cue | Trap |
| --- | --- | --- |
| N-grams | N−1 previous words; MLE = pair/context | Chain rule exact; Markov approximation |
| Naive Bayes | Prior × likelihoods → score → normalize | Documents vs tokens vs unique words |
| HMM | Infer hidden states from observations over time | Forward sums for observation likelihood; Viterbi finds the best path |

**Add-one:** numerator count+1; denominator context/class-token count+vocabulary size.

**Perplexity:** $P(W)^{-1/N}$; lower under comparable evaluation.

**Anchor answers:**
- Naive Bayes “good movie” → **Positive posterior 0.8**.
- HMM weather U,U,no umbrella → **RRS**; joint **0.06804**; observation likelihood **0.120445**.
- HMM “he raises purses” → **NNN** under given unsmoothed corpus; joint **0.000512**. Include END.

→ [[13 - Statistical Language Models]] · [[14 - Naive Bayes]] · [[16 - Hidden Markov Models]]

## Problem solving — outline before writing
**Initial state** = start; **goal** = desired result; **operators** = legal actions; **problem space** = possible states and moves. **GPS** models search through this space; **means–ends analysis** compares current/goal states and creates subgoals to resolve differences.

**Hanoi:** top 2 A→B → largest A→C → top 2 B→C; minimum $2^n-1$.

**3-disk moves:** 1:A→C; 2:A→B; 1:C→B; 3:A→C; 1:B→A; 2:B→C; 1:A→C.

**Nine dots:** extend outside the grid. **Well-defined:** explicit goal/rules; **ill-defined:** ambiguity and flexible constraints. **Algorithm:** specified guarantee; **heuristic:** shortcut without guarantee.

→ [[10 - Problem Solving]]

## Final closed-note drill
- [ ] Draw “The big yellow dog sat under the house” using the supplied grammar.
- [ ] Tag both Q8 sentences and explain VBD vs VBN.
- [ ] Solve the perceptron $w=(0.5,-0.7),b=0.1,x=(1,2)$.
- [ ] Reproduce one output-weight and one hidden-weight backprop update.
- [ ] Calculate and normalize the movie-review Naive Bayes scores.
- [ ] Reproduce both HMM examples, with backtracking and END where specified.
- [ ] Write a GPS/Hanoi answer: representation → subgoals → moves → strengths/limits.
