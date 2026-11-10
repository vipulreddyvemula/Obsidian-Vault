---
tags: [cognitive-science, linguistics, nlp, revision]
unit: 5
lecture_pdfs: [11, 12]
updated: 2026-11-10
---

# Linguistics & NLP — Revision Notes

> [!abstract] At a glance
> **Phonology = sounds; morphology = words; syntax = sentence structure; semantics = meaning; pragmatics = context.**
> **Phoneme distinguishes meaning; morpheme carries meaning/function.**
> NLP pipeline: **Clean → Tokenize → Remove selected stopwords → Normalize → Vectorize → Classify.**
> **BoW counts; TF-IDF weights; embeddings encode learned semantic relationships.**
> For the exam exercises, open [[11-12 - POS and Parsing Practice]].

## 1. Language and thought
- **Linguistics:** scientific study of language—structure, meaning, acquisition, processing and use. Connects neuroscience, psychology, philosophy, computation and AI.
- Language is **communicative, arbitrary, structured, generative and dynamic**. Language can be spoken, written or signed; language ≠ speech.
- **Sapir–Whorf:** strong determinism = language determines thought; weaker relativity = language influences thought. **No word does not mean no thought.**

## 2. Definitions with one example each

| Term | Meaning | Example |
| --- | --- | --- |
| Phoneme | Smallest contrastive sound unit | /b/→/p/: bat→pat |
| Morpheme | Smallest meaningful/grammatical unit | books = book + s |
| Phonology | Sound patterns/rules | Plural sounds in cats/dogs |
| Morphology | Word structure | unhappy = un + happy |
| Syntax | Phrase/sentence arrangement | Subject–verb–object |
| Semantics | Linguistic meaning | Who chased whom? |
| Pragmatics | Meaning from context/intention | “Can you open the window?” = request |

Free morpheme = can stand alone (`book`); bound = cannot (`-s`). `teachers = teach + er + s`; `redo = re + do`.

**Compositional semantics:** word meanings + grammatical structure → phrase/sentence meaning. Linguistic hierarchy: sounds → morphemes → words → phrases → sentences.

## 3. Ambiguity — recognize and explain both readings

| Type / issue | Example | Two readings |
| --- | --- | --- |
| Lexical | “I saw a bat” | Animal / sports equipment |
| Lexical | bank; crane | Finance/river edge; machine/bird |
| Syntactic | “I saw the man with the telescope” | I used it / man had it |
| Lexical + POS | “I saw her duck” | Her bird / her lowering her head |
| Structural/semantic | “The chicken is ready to eat” | Chicken eats / is eaten |

**World knowledge:** trophy does not fit suitcase because “it” is too **big** → trophy; too **small** → suitcase. Grammar alone does not settle the reference.

## 4. NLP tasks and the pipeline
**NLP:** computers process, interpret and generate human language.
Tasks: classification, **NER**, translation, question answering, summarization, intent recognition and generation.

**NER identifies entities** (Apple = organization, Paris = location). **POS identifies grammatical categories** (Apple/NNP, opened/VBD).

**Faculty pipeline example:**

| Step | Result / purpose |
| --- | --- |
| Raw text | The Movie was ABSOLUTELY Fantastic!!! |
| Clean | the movie was absolutely fantastic |
| Tokenize | the · movie · was · absolutely · fantastic |
| Selected stopword removal | movie · absolutely · fantastic |
| Stem OR lemmatize | Normalize word forms |
| Vectorize | Convert text to numeric features |
| Classify | Positive sentiment |

> [!warning] Preserve meaning
> Removing **not** can reverse sentiment. Removing numbers/punctuation or lowercasing is task-dependent. This is the lecture’s traditional pipeline, not a compulsory recipe for every NLP model.

**Stemming chops:** `studies → studi`, possibly a nonword. **Lemmatization finds a dictionary base:** `studies → study`, `better → good`; may use POS/context.

## 5. Text representation and models

| Method | What it captures | Limitation |
| --- | --- | --- |
| Bag of Words | Counts in fixed vocabulary order | Loses word order |
| TF-IDF | Local frequency × corpus rarity | Generally loses order/deeper meaning |
| Static embeddings | Dense learned semantic vectors | Same word vector across contexts |
| Contextual embeddings | Representation depends on sentence | Requires a contextual model |

**BoW faculty example:** vocabulary `[I,love,NLP,AI]`; “I love NLP” → **[1,1,1,0]**; “I love AI” → **[1,1,0,1]**. Dog-chased-cat and cat-chased-dog have identical counts but different meanings.

**TF-IDF supplementary practice from the chat:**
$$
TFIDF(t,d)=TF(t,d)\log\frac{N}{df(t)}
$$
With raw-count TF=3, N=10, df=2: **3 ln(5) ≈ 4.828**. Under this unsmoothed formula, a term in every document gets IDF=0. Follow the question’s TF/log convention.

**Model progression:** handwritten rules → statistical models (N-gram, Naive Bayes, HMM) → RNN sequences → attention-based Transformers. Static embedding examples: Word2Vec/GloVe; lecture Transformer examples: BERT/GPT/T5. Tools named: spaCy, NLTK, Hugging Face.

## 6. Evaluation, challenges and future directions

| Metric | Remember |
| --- | --- |
| Accuracy | $(TP+TN)/(TP+TN+FP+FN)$ |
| Precision | $TP/(TP+FP)$: correct among predicted positives |
| Recall | $TP/(TP+FN)$: found among actual positives |
| F1 | $2PR/(P+R)$ |
| BLEU / ROUGE | Translation / summarization reference overlap |
| Perplexity | Language prediction; lower under comparable evaluation |

Practice: 8 correct among 10 predicted spam; 16 actual spam → **precision 0.8, recall 0.5, F1 ≈ 0.6154**.

Challenges: ambiguity, sarcasm, idioms/culture, biased data, scarce language resources. Directions mentioned: multimodal, few-shot, cross-lingual and explainable NLP.

## 7. Language acquisition — 2024 Q4, 8 marks
**Acquisition:** developing language comprehension and use through maturation, exposure and interaction. This stage-by-stage material supplements the PDFs in the source explanation.

| Approximate stage | Feature | Cue |
| --- | --- | --- |
| Birth–12 months | Prelinguistic: crying/cooing/babbling | ba-ba |
| 12–18 months | One-word / holophrastic | “Milk!” = I want milk |
| 18–24 months | Two-word combinations | more milk |
| 2–3 years | Telegraphic: mainly content words | Daddy go office |
| 3+ years | Increasing vocabulary and grammar | Longer sentences/questions |

Ages are approximate. **“Goed”** shows overregularization: applying a learned past-tense rule to an irregular verb.

## Test yourself — answer before expanding

> [!question]- Phoneme vs morpheme?
> Contrastive sound vs smallest meaningful/grammatical unit.

> [!question]- Why can BoW not distinguish who chased whom?
> It counts words and discards order.

> [!question]- Precision vs recall?
> Precision checks the predicted positives; recall checks the actual positives.

Related: [[11-12 - POS and Parsing Practice]] · [[13 - Statistical Language Models]] · [[14 - Naive Bayes]] · [[16 - Hidden Markov Models]]

---
Source: condensed from the latest ANN and Linguistics/NLP explanations in [Organize PDF Topics](https://chatgpt.com/c/6aef17a8-9c54-83ec-8e63-e1a2ab7ed46f). Checked 10 November 2026.
