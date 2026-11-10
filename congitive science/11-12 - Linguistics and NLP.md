---
tags: [cognitive-science, linguistics, nlp, revision]
unit: 5
lecture_pdfs: [11, 12]
updated: 2026-11-10
---

# Linguistics & NLP — Short Revision Notes

> [!abstract] At a glance
> **Lexical = words; syntactic = structure; semantic = meaning; pragmatic = context/intention.**
> **Sounds → word parts → words → phrases → sentences.**
> NLP: **Clean → Tokenize → selected Stopwords → Normalize → Vectorize → Classify.**
> For tagged sentences and the full tree: [[11-12 - POS and Parsing Practice]].

## 1. Language and thought
**Linguistics:** scientific study of language—its structure, meaning, acquisition, processing and use. It connects memory, attention and reasoning with neuroscience, developmental psychology, philosophy and computational models.

**Sapir–Whorf hypothesis:** language and thought are related.
- **Determinism (strong):** language determines what can be thought.
- **Relativity (weaker):** language influences habitual attention, categorization or memory.
- **Reflection:** vocabulary reflects culturally important distinctions. **No word ≠ no thought.**

| Property of language | Definition + example |
| --- | --- |
| Communicative | Expresses intentions: asking for help |
| Arbitrary | Word form need not resemble its meaning: tree / arbre |
| Structured | Follows grammatical combinations: subject–verb–object |
| Generative | Finite rules allow new sentences |
| Dynamic | Changes with use: “mouse” gained a computer meaning |

Language can be spoken, written or signed; speech is only one modality.

## 2. Language terms — definition + example

| Term | Definition | Example |
| --- | --- | --- |
| Phoneme | Smallest sound unit distinguishing words | /b/ vs /p/: bat→pat |
| Morpheme | Smallest unit carrying meaning/grammatical function | book + s: `-s` adds plurality |
| Phonology | Study of sound patterns and rules | Plural sounds in cats vs dogs |
| Morphology | Study of word formation/internal structure | un + happy; teach + er + s |
| Syntax | Rules combining words into phrases/sentences | The dog chased the cat: subject→verb→object |
| Semantics | Study of linguistic meaning | Understand what “chased” and the sentence mean |
| Pragmatics | Interpretation using context and intention | “Can you open the window?” as a request |

**Free morpheme:** stands alone (`book`). **Bound:** cannot normally stand alone (`un-`, `-s`).

**Lexical semantics** studies individual word meanings: `bank` = finance / river edge. **Compositional semantics** studies how meanings combine through grammar: dog-chased-cat differs from cat-chased-dog despite identical words.

**Semantics vs pragmatics:** “It is cold here” describes low temperature; in context it may request closing the window.

## 3. Ambiguity — define it and show both readings
**Ambiguity:** an expression permits more than one interpretation.

### Lexical ambiguity — different meanings of a word
**Definition:** one word has multiple possible meanings.
**“I saw a bat”** → flying mammal / sports equipment. The uncertain element is **bat’s meaning**. Similarly, crane = bird/machine; bank = finance/river edge. Context selects a word sense (**disambiguation**).

### Syntactic / structural ambiguity — different grammatical groupings
**Definition:** the same sentence has more than one grammatical structure.
**“I saw the man with the telescope”** → I used the telescope / the man carried it. **“With the telescope” attaches to seeing or to the man**, changing the grouping.

### Semantic ambiguity — different interpretations of meaning
**Definition:** the expression admits multiple interpretations of meaning; this can overlap lexical or structural causes.
**“The chicken is ready to eat”** → chicken eats food / chicken is ready to be eaten. The chicken’s role changes: **eater vs food**. Your source calls this structural ambiguity with a semantic difference; explain both readings when answering.

### POS ambiguity — different word categories
**Definition:** one word form can take different grammatical categories in context.
**“I saw her duck”** → duck/**noun** (her bird) / duck/**verb** (lower her head). This combines lexical and category ambiguity.

### Reference and world knowledge
**“The trophy would not fit in the suitcase because it was too big/small.”** Big → trophy; small → suitcase. Context and knowledge about containment identify what **it** refers to.

**Identification cue:** word sense → lexical; phrase attachment → syntactic; meaning interpretation → semantic; noun/verb choice → POS; unclear pronoun → reference.

## 4. NLP tasks and the pipeline
**Natural Language Processing:** AI methods that process, interpret and generate human language.

| Task | Definition + example |
| --- | --- |
| Classification | Assign a text category: spam/not spam |
| NER | Identify named entities/types: Apple = organization, Paris = location |
| POS tagging | Assign grammatical categories: opened/VBD |
| Translation | Express text in another language |
| Question answering | Answer from information: who wrote Hamlet? |
| Summarization | Shorten text while retaining important information |
| Intent recognition | Identify requested action: “Book a flight to Delhi” → book-flight |

**NER labels entities; POS labels grammar.**

| Pipeline stage   | Definition                               | Example                     |
| ---------------- | ---------------------------------------- | --------------------------- |
| Cleaning         | Standardize unwanted formatting          | Movie!!! → movie            |
| Tokenization     | Split text into units called tokens      | I love NLP → I · love · NLP |
| Stopword removal | Remove selected frequent words           | the, a, was                 |
| Normalization    | Reduce related forms to roots/base forms | studies → studi / study     |
| Vectorization    | Convert text into numeric features       | A count vector              |
| Classification   | Select a predicted category              | Positive sentiment          |

Faculty sentence: **“The Movie was ABSOLUTELY Fantastic!!!”** → clean/tokenize → selected stopwords removed → **movie · absolutely · fantastic** → vectorize → Positive.

**Stemming:** rule-based chopping; `studies→studi` may be a nonword. **Lemmatization:** use linguistic information to find a dictionary base; `studies→study`, `better→good`.
**Trap:** removing **not** can reverse sentiment; cleaning choices depend on the task.

## 5. Representations and model types

| Method | Definition | Example / limitation |
| --- | --- | --- |
| Bag of Words | Vector of counts in fixed vocabulary order | Loses word order; cat/dog role reversal gives the same counts |
| TF-IDF | Weight combining within-document frequency and corpus rarity | Frequent locally, rare globally → larger weight |
| Static embedding | Dense learned word vector encoding associations | Word2Vec/GloVe; one vector per word across contexts |
| Contextual embedding | Word representation changes with its sentence context | Supports context-dependent interpretation |

**BoW:** vocabulary `[I,love,NLP,AI]`: “I love NLP”→**[1,1,1,0]**; “I love AI”→**[1,1,0,1]**.

**TF-IDF practice formula:** $TFIDF(t,d)=TF(t,d)\log(N/df(t))$.
TF = term frequency in document d; N = total documents; df = documents containing t.
Raw TF=3, N=10, df=2 → **3 ln(5)≈4.828**. Under this unsmoothed formula, a term in all documents gets IDF=0.

| Approach | Meaning | Example |
| --- | --- | --- |
| Rule-based | Human-written rules | Keyword sentiment rule; may miss sarcasm |
| Statistical | Probabilities learned from data | N-gram, Naive Bayes, HMM |
| RNN | Recurrent network carries information through sequence steps | Basic RNNs struggle with long dependencies |
| Transformer | Attention models relationships between tokens | BERT/GPT/T5 in the lecture |

Tools mentioned: spaCy, NLTK, Hugging Face.

## 6. Evaluation and challenges

| Metric | Definition / formula |
| --- | --- |
| Accuracy | Fraction correct: $(TP+TN)/(TP+TN+FP+FN)$ |
| Precision | Correct among predicted positives: $TP/(TP+FP)$ |
| Recall | Found among actual positives: $TP/(TP+FN)$ |
| F1 | Harmonic mean: $2PR/(P+R)$ |
| BLEU / ROUGE | Reference overlap for translation / summarization |
| Perplexity | Predictive uncertainty in language modeling; lower on comparable tests |

TP/TN = correctly predicted positive/negative; FP/FN = falsely predicted positive/negative. Example: 8 correct spam predictions out of 10, with 16 actual spam → **P=0.8, R=0.5, F1≈0.6154**.

**Challenges:** ambiguity; sarcasm (“great, another rainy day”); idioms (“break a leg”); training-data bias; low-resource languages. Directions mentioned: multimodal (text/images/audio), few-shot (few examples), cross-lingual (across languages), explainable (interpretable predictions).

## 7. Language acquisition — 2024 Q4, 8 marks
**Definition:** development of language understanding/use through maturation, exposure and social interaction. The stages supplement the PDF in your source.

| Approximate stage | Feature + example |
| --- | --- |
| Birth–12 months: prelinguistic | Crying, cooing, babbling: ba-ba |
| 12–18 months: one-word/holophrastic | One word expresses an intention: “Milk!” |
| 18–24 months: two-word | Combine meaningful words: “more milk” |
| 2–3 years: telegraphic | Mainly content words: “Daddy go office” |
| 3+ years: later development | Longer sentences, questions and grammar |

Ages vary. **Overregularization:** applying a learned rule too broadly, e.g. `goed` for `went`; indicates active rule learning.

## Quick self-check
> [!question]- Lexical semantics vs compositional semantics?
> Individual word meaning vs how meanings combine through grammar into sentence meaning.

> [!question]- Why is the telescope sentence syntactically ambiguous?
> The telescope phrase attaches to different parts: the seeing action or the man.

> [!question]- Phoneme vs morpheme?
> Sound distinguishing words vs a unit carrying meaning/grammatical function.

Related: [[11-12 - POS and Parsing Practice]] · [[13 - Statistical Language Models]] · [[14 - Naive Bayes]] · [[16 - Hidden Markov Models]]

---
Source: your pasted Linguistics/NLP explanation and [Organize PDF Topics](https://chatgpt.com/c/6aef17a8-9c54-83ec-8e63-e1a2ab7ed46f). Definitions retained with brief examples; detailed POS/PYQ practice is in the linked note.
