---
tags: [cognitive-science, pos, parsing, pyq]
unit: 5
updated: 2026-11-10
---

# POS & Parsing — Exam Practice

> [!abstract] Revise in this order
> **Tag table → both Q8 sentences → Q10 tree → Q9 ambiguity → Q7 context change.**
> **POS = word category; parsing = phrase/sentence structure.**
> Traps: **bought/VBD; was/VBD purchased/VBN; very/RB; their/PRP$; three/CD.**
> Penn tags, full parsing and acquisition stages are PYQ supplements in the source chat.

## 1. Penn tags — compact lookup

| Group | Tags → meaning |
| --- | --- |
| Nouns | **NN** singular/common; **NNS** plural; **NNP** proper singular; **NNPS** proper plural |
| Pronouns | **PRP** he/it/they; **PRP$** his/their/my |
| Modifiers | **JJ** adjective; **JJR** comparative; **JJS** superlative; **RB** adverb |
| Function words | **DT** the/a; **IN** in/with/near; **CC** and/or; **CD** number; **TO** to |

| Verb tag | Cue | Example |
| --- | --- | --- |
| VB | Base / after “to” | to **eat** |
| VBP | Present, non-third-singular | I **eat**, they **are** |
| VBZ | Present, third-singular | she **eats** |
| VBD | Past tense | she **ate**, it **was** |
| VBG | Gerund / present participle | **eating** |
| VBN | Past participle | was **eaten** |

## 2. 2024 Q8 — practise both sentences
**(a)**
```text
Aniket/NNP and/CC Ankita/NNP bought/VBD a/DT
fridge/NN with/IN three/CD doors/NNS ./.
```
**(b)**
```text
It/PRP was/VBD purchased/VBN from/IN a/DT very/RB
small/JJ store/NN near/IN their/PRP$ house/NN
located/VBN at/IN Pala/NNP ./.
```
**Why?** “Was purchased” is passive → purchased/VBN. “Very” modifies small → RB. “Located” is a participle in a reduced relative clause → VBN. Tag **by context**, not spelling alone.

> [!question]- Tag “purchased” in “He purchased a fridge” versus “It was purchased”.
> First **VBD** (past tense); second **VBN** (past participle).

## 3. 2024 Q7 — “His likes include swimming”
- Original **likes = plural noun/NNS**, meaning preferences.
- **“She likes swimming.”** → likes becomes **verb/VBZ**.
- **“The children are swimming.”** → swimming now belongs to a progressive verb phrase, instead of naming an activity nominally.

**Nuance:** Penn Treebank can label both gerund and progressive uses **VBG**; the second example changes syntactic function, not necessarily its Penn tag. Explain the distinction if using it.

## 4. 2024 Q9 — “Spring leaves spring”

| Plausible reading | Tags | Interpretation |
| --- | --- | --- |
| Springtime leaves spring upward | Spring/**NN** leaves/**NNS** spring/**VBP** | Noun phrase + verb |
| A character called Spring leaves “spring” | Spring/**NNP** leaves/**VBZ** spring/**NN** | Subject + verb + object; needs context |

**Justification:** spring can be noun/verb/proper name; leaves can be noun/verb. Hence lexical/POS ambiguity, with different structures and meanings. **Not every arbitrary tag combination forms a valid sentence.**

## 5. 2024 Q10 — full parse tree
Sentence: **The big yellow dog sat under the house.**

**Use the supplied rules:**
```text
S   → NP VP
NP  → DET NOM
NOM → ADJ NOM | NOUN
VP  → VP PP | VERB NP | VERB
PP  → PREP NP
```
**Build:** subject NP = The big yellow dog; VP = sat + PP; PP = under + the house.

```text
S
├── NP
│   ├── DET → The
│   └── NOM
│       ├── ADJ → big
│       └── NOM
│           ├── ADJ → yellow
│           └── NOM
│               └── NOUN → dog
└── VP
    ├── VP
    │   └── VERB → sat
    └── PP
        ├── PREP → under
        └── NP
            ├── DET → the
            └── NOM
                └── NOUN → house
```

> [!tip] Tree checks that save marks
> Two adjectives → **two recursive NOM expansions**.
> “Under the house” → **PP**, not direct-object NP.
> Use **VP → VP PP**, then inner **VP → VERB**.
> Read leaves left→right: they must reproduce the sentence exactly. Every expansion must match an allowed rule.

## 6. 2024 Q1 — five quick answers

| Cue | Answer |
| --- | --- |
| Word meanings combined through grammatical structure | **Compositional semantics** (semantics is the broader field) |
| “The chicken is ready to eat” | **Structural/semantic ambiguity:** chicken eats / is eaten |
| Remove and/is/a/an/the | **Stopword removal** |
| Sound patterns and rules | **Phonology** |
| 250 verb tokens among 10,000 words | **250/10,000 = 0.025 = 2.5%** |

For Q4’s language-acquisition stages, see [[11-12 - Linguistics and NLP#7. Language acquisition — 2024 Q4, 8 marks]].

## Recall drill
- [ ] Tag both Q8 sentences without the answers.
- [ ] Draw Q10’s tree from the grammar alone.
- [ ] Give two readings of “Spring leaves spring”.
- [ ] Explain bought/VBD versus purchased/VBN.
- [ ] Distinguish **grammatical category**, **syntactic function** and **phrase structure**.

---
Source: condensed from the latest ANN and Linguistics/NLP explanations in [Organize PDF Topics](https://chatgpt.com/c/6aef17a8-9c54-83ec-8e63-e1a2ab7ed46f). Checked 10 November 2026.
