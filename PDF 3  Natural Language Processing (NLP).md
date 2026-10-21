# 🧠 Cognitive Science — Last-Minute Revision Notes

## PDF 3: Natural Language Processing (NLP)

These notes cover the key definitions, differences, examples, and formulas from your PDF. Focus on the **bold terms, comparison tables, and examples** for your quiz.

## 1. What is NLP?

**Natural Language Processing (NLP):** A field of AI and computer science that enables computers to process, analyze, interpret, and generate human language.

**Examples:** ChatGPT, Google Translate, spam detection, voice assistants, and text summarization.

### Core NLP tasks

|Task|Meaning|Example|
|---|---|---|
|Text classification|Assigns a category to text|Spam vs. non-spam|
|Named Entity Recognition (NER)|Identifies named entities|Apple → Organization; Paris → Location|
|Machine translation|Converts one language into another|English → Spanish|
|Question answering|Answers questions using information|Who wrote _Hamlet_? → Shakespeare|
|Summarization|Produces a shorter version of text|Long article → Short summary|

NLP can also identify **intent** (what the user wants) and **entities** (specific information in a request). For example, "Book a flight to Delhi tomorrow morning" contains the intent to book a flight, the destination Delhi, and the time tomorrow morning. NLP_Notes_Sep24

## 2. NLP Pipeline

**General pipeline:**

**Raw text → Preprocessing → Numerical representation → Machine learning model → Prediction**

### Main preprocessing steps

|Step|Definition|Example|
|---|---|---|
|Text collection|Gather text data|Reviews, emails, tweets|
|Text cleaning|Normalize text|`Fantastic!!!` → `fantastic`|
|Tokenization|Split text into tokens|`I love NLP` → `[I, love, NLP]`|
|Stopword removal|Remove selected common words|Remove `the`, `is`, `was`|
|Stemming|Remove word endings using simple rules|`studies` → `studi`|
|Lemmatization|Convert words to their base forms using linguistic information|`better` → `good`|
|Feature extraction|Convert text into numerical representations|Text → Vector|

**Important:** Stopword removal can change the meaning if words such as _not_ are removed. For example, "I do not like this movie" could become "like movie," reversing the sentiment. NLP_Notes_Sep24 NLP_Notes_Sep24

### Stemming vs. Lemmatization

|Stemming|Lemmatization|
|---|---|
|Uses simple rules to chop word endings|Uses vocabulary and grammatical information|
|May produce invalid words|Aims to produce valid base forms|
|`studies` → `studi`|`better` → `good`|

**Memory trick:** Stemming chops; lemmatization finds the lemma.

## 3. Numerical Representations of Text

Computers use numerical representations, such as vectors, to process text.

### A. Bag of Words (BoW)

**BoW represents text using word counts, ignoring word order.**

Vocabulary: `[I, love, NLP, AI]`

- Text 1: "I love NLP" → `[1, 1, 1, 0]`
- Text 2: "I love AI" → `[1, 1, 0, 1]`

**Limitation:** It loses word order.

"The dog chased the cat" and "The cat chased the dog" have the same basic Bag of Words representation, even though their meanings differ.

### B. TF-IDF

**TF-IDF = Term Frequency–Inverse Document Frequency**

- **TF:** How often a word occurs in a particular document.
- **IDF:** How rare a word is across a collection of documents.

TF-IDF gives greater weight to words that occur frequently in a document but are relatively rare across the collection.

Example: In movie reviews, _fantastic_ may be more informative than _movie_ because _movie_ occurs in many reviews.

### C. Word embeddings

**Word embeddings represent words as dense numerical vectors that capture learned semantic relationships.**

Example:

\[ \text{king}-\text{man}+\text{woman}\approx\text{queen} \]

Examples of embedding methods: **Word2Vec and GloVe**.

### Comparison

|BoW|TF-IDF|Word embeddings|
|---|---|---|
|Counts word occurrences|Weights words by frequency and rarity|Represents learned semantic relationships|
|Ignores word order|Does not inherently capture word order or meaning|Can capture relationships between words|

**Remember:** BoW counts words; TF-IDF weights informative words; embeddings represent learned relationships. NLP_Notes_Sep24

## 4. Traditional vs. Modern NLP

### Traditional approaches

**Rule-based NLP**

- Uses manually written rules.
- Example: If a sentence contains "excellent," classify it as positive.
- Limitation: Can fail with sarcasm and context.

**Statistical NLP**

- Uses probabilities to predict words or labels.
- Example: "I want to drink ..." → Predict "water."

**N-grams:** Sequences of consecutive tokens.

- Unigram: One token.
- Bigram: Two consecutive tokens.
- Trigram: Three consecutive tokens.

### Modern approaches

|Approach|Main idea|Limitation or feature|
|---|---|---|
|Word embeddings|Represent words as dense numerical vectors|Capture learned semantic relationships|
|RNN|Processes sequences recurrently|Basic RNNs can struggle with long-range dependencies|
|Transformer|Uses attention to model relationships between tokens|Can capture contextual relationships across a sequence|

**Transformer examples:** BERT, GPT, and T5.

For the quiz, remember: **RNN = recurrent sequence processing; Transformer = attention-based processing.** NLP_Notes_Sep24

## 5. Pretrained NLP Models and Tools

|Model/tool|Use highlighted in the slides|
|---|---|
|BERT|Understanding text, sentiment analysis, question answering|
|GPT|Text generation, chatbots, writing assistance|
|T5|Translation and summarization|
|spaCy / NLTK|Tokenization, part-of-speech tagging, classical NLP|
|Hugging Face|Tools for accessing and using pretrained models|

**Pretrained model:** A model that has already been trained on data and can be used as a starting point for a task. NLP_Notes_Sep24

## 6. Evaluation Metrics

|Metric|Meaning / use|
|---|---|
|Accuracy|Proportion of all predictions that are correct|
|Precision|Proportion of predicted positives that are actually positive|
|Recall|Proportion of actual positives correctly identified|
|F1 score|Combines precision and recall using their harmonic mean|
|BLEU|Commonly used to evaluate machine translation|
|ROUGE|Commonly used to evaluate summarization|
|Perplexity|Measures language-model prediction performance; lower generally indicates better prediction of the evaluated sequence|

### Important formulas

**Accuracy**

$[ \text{Accuracy}=\frac{TP+TN}{TP+TN+FP+FN} ]$

**Precision**

$[ \text{Precision}=\frac{TP}{TP+FP} ]$

**Recall**

$[ \text{Recall}=\frac{TP}{TP+FN} ]$

**F1 score**

$[ F1=2\times\frac{\text{Precision}\times\text{Recall}} {\text{Precision}+\text{Recall}} ]$

Where:

- **TP:** True positives.
	- **TN:** True negatives.
- **FP:** False positives.
- **FN:** False negatives.

**Memory trick:**

- Precision = How many predicted positives were correct?
- Recall = How many actual positives did we find?

BLEU, ROUGE, and perplexity are associated with translation, summarization, and language modeling, respectively. NLP_Notes_Sep24

## 7. Challenges in NLP

|Challenge|Example|
|---|---|
|Ambiguity|"I saw her duck."|
|Sarcasm|"Oh great, another rainy day."|
|Cultural context|"Break a leg!" means good luck|
|Data bias|Stereotypical associations between occupations and gender|
|Low-resource languages|Limited datasets for languages such as Yoruba or Lao|

**Key idea:** NLP must account for context, intended meaning, culture, biases in data, and the availability of training resources. NLP_Notes_Sep24

## 8. Future of NLP

| Area              | Meaning                                          |
| ----------------- | ------------------------------------------------ |
| Multimodal NLP    | Combines text with images, audio, or other data  |
| Few-shot learning | Learns or adapts from a small number of examples |
| Cross-lingual NLP | Supports multiple languages                      |
| Explainable NLP   | Helps explain why a model made a prediction      |

NLP_Notes_Sep24

---

## ⭐ Final 2-Minute Revision

Memorize these 12 points:

1. **NLP:** Enables computers to process and generate human language.
2. **Tokenization:** Splits text into tokens.
3. **Stopword removal:** Removes selected common words, but removing _not_ can reverse meaning.
4. **Stemming:** Chops word endings using simple rules.
5. **Lemmatization:** Finds linguistically appropriate base forms.
6. **BoW:** Counts words but ignores word order.
7. **TF-IDF:** Gives greater weight to locally frequent, globally rare words.
8. **Word embeddings:** Dense vectors that capture learned semantic relationships.
9. **RNN vs. Transformer:** Recurrent processing vs. attention-based processing.
10. **Precision vs. recall:** Correctness of predicted positives vs. coverage of actual positives.
11. **BLEU / ROUGE / Perplexity:** Translation / summarization / language modeling.
12. **NLP challenges:** Ambiguity, sarcasm, cultural context, data bias, and low-resource languages.

### What to revise first

**Prioritize the preprocessing pipeline, BoW vs. TF-IDF vs. embeddings, stemming vs. lemmatization, RNN vs. Transformer, and evaluation metrics.** Make sure you can identify each concept from an example, not just repeat its definition.