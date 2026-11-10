---
tags: [cognitive-science, problem-solving, gps]
unit: 4
lecture_pdf: 10
updated: 2026-11-10
---
	
# Problem Solving — Short Notes

> [!abstract] At a glance
> **Represent:** initial state → legal operators → goal; all possibilities form the problem space.
> **GPS = framework; means–ends = strategy** using differences and subgoals.
> **Hanoi:** top 2 A→B; largest A→C; top 2 B→C. Minimum $2^n-1$ → **7 moves for 3 disks**.
> **Well-defined:** clear states/rules/goal test. **Ill-defined:** ambiguous goals/constraints.
> **Nine dots:** extend beyond the grid; change the representation.
> **Trap:** a necessary subgoal can temporarily move away from the final goal.


## 1. Core definitions
- **Cognition:** mental processes for acquiring, processing, storing and using information. **Example:** reading a question, recalling a formula and calculating an answer.
- **Problem solving:** using actions and strategies to overcome obstacles and reach a goal. **Example:** transform $2x+5=17$ into $x=6$.
- **Reasoning:** drawing conclusions from premises/evidence; it can support problem solving.

| Term | Meaning | Tower of Hanoi |
| --- | --- | --- |
| Initial state | Starting condition | All disks on A |
| Goal state | Desired condition | All disks on C |
| Operators | Legal actions | Move a top disk |
| Problem space | Possible states and transitions | Legal arrangements and moves |

**Cognitive cycle:** Identify → Represent → Choose strategy → Apply → Evaluate → Revise.

## 2. Well-defined vs. ill-defined
**Well-defined problem:** clear starting conditions, goal, rules and a way to check the answer. **Ill-defined problem:** one or more of these are unclear or open-ended.


| Aspect | Well-defined | Ill-defined |
| --- | --- | --- |
| Start and goal | Clear, specific | May be unclear/broad |
| Rules/operators | Explicit | Flexible/incomplete |
| Evaluation | Clear goal test | Often subjective/contextual |
| Solutions | Clearly testable | Several acceptable approaches |
| Examples | Equation, Sudoku, Hanoi | Write a novel; improve college life |

Faculty classification: equation, Sudoku and average marks = well-defined; stress app, AI novel, plastic-waste reduction and better college = ill-defined. Shortest route is well-defined **when network and costs are specified**.

## 3. Concepts, prototypes and expertise
- **Concept:** mental category, e.g. bird. Speeds processing, communication and reuse of knowledge.
- **Prototype:** typical representative, e.g. sparrow. Enables quick recognition but can cause bias, stereotypes and miscommunication. A penguin is still a bird.
- **Concept shifting:** revise a category after new information—birds include non-flying penguins; botanical fruit includes tomatoes.
- Keep the lecture’s **prototype-biased remembering** (recalling an unusual dog as more typical) distinct from revising a category.
- **Novice:** beginner with limited domain knowledge; often focuses on surface details. **Expert:** has organized knowledge and recognizes underlying structure. **Example:** an expert recognizes a recurrence method instead of trying random algebra.

## 4. Memory, algorithms and heuristics
**Working memory** temporarily holds and manipulates information; **long-term memory** stores learned knowledge and methods. **Example:** WM holds $3x=2$ while LTM supplies “divide both sides by 3”.

Flow: encode problem in WM → retrieve from LTM → apply method → compare with goal → repeat if needed.

- **Algorithm:** defined steps that solve the specified problem under stated conditions. **Example:** binary search on sorted data. It provides a guarantee, but algorithms are not always fast.
- **Heuristic:** useful shortcut without a guarantee, e.g. move toward a maze’s apparent exit.
- **Anti-looping:** avoid revisiting states or undoing actions without useful progress.
- **Subgoal:** intermediate target, e.g. shoes → 5 km → 10 km → marathon.
- Real-world problems need flexible representations, creativity, planning and decisions under uncertainty.

## 5. Means–ends analysis and GPS
**Means–ends analysis:** a strategy that compares the current state with the goal, identifies the difference, and chooses actions/subgoals to overcome it.
**Steps:** compare → identify difference → choose operator → create subgoals → act → evaluate.

Example: research paper → choose topic → gather sources → outline → draft → revise.
A necessary step can temporarily move away from the final goal, as in Hanoi.

**General Problem Solver (GPS; Newell and Simon):** a computational model representing problem solving as search through a problem space using operators. **GPS uses means–ends analysis:** GPS is the overall model; means–ends is a strategy inside it.

Faculty route example: Home → Main Road → Junction → College Road → College. Forward search starts at home; backward search works from the goal toward prerequisites.

## 6. Tower of Hanoi — GPS application
**Rules:** one disk per move; only top disks move; never place a larger disk on a smaller one. Disk 1 = smallest; disk 3 = largest.

Initial: all on A. Goal: all on C. Legal top-disk moves are operators.

**Subgoals:** top two A→B; largest A→C; top two B→C.

| Move | Disk | From → To |
| --- | --- | --- |
| 1 | 1 | A → C |
| 2 | 2 | A → B |
| 3 | 1 | C → B |
| 4 | 3 | A → C |
| 5 | 1 | B → A |
| 6 | 2 | B → C |
| 7 | 1 | A → C |

$$
M(n)=2M(n-1)+1=2^n-1
$$
For 3 disks: **7 moves**; 4 disks: 15; 5 disks: 31.

**Advantages of GPS:** structured representation, subgoals, less random search, planning and decomposition.
**Limitations:** growing search space; depends on representation/heuristics; less suited to ambiguous problems; incomplete account of creativity, emotions and individual differences.

## 7. Nine-dot puzzle
Connect a 3×3 grid using **four continuous straight segments**, without lifting the pen. Lines may extend **outside the grid**.

Start bottom-left: up through left column and beyond → diagonal down-right through top-middle and middle-right to beyond bottom-right → left through bottom row → diagonal up-right through center and top-right.

**Lesson:** an invented boundary makes the problem seem impossible; restructuring the mental representation enables the solution.

## 8. PYQ answer outlines from the chat
- **GPS + Hanoi, 10 marks (2023/2025 mid-sem Q3):** define GPS → states/operators/constraints → means–ends subgoals → seven moves → advantages/limitations. Draw initial and goal arrangements.
- **Algorithms save time/energy, 10 marks (2024 end-sem Q5):** systematic procedure, reduced cognitive load/errors, reuse and fewer unnecessary steps; explain recursive Hanoi and its 7-move solution.
- **Well-/ill-defined, 10 marks (2024 Q6):** compare at least five features with examples; equation $2x+5=17\Rightarrow x=6$ versus improving college life.
- **Reasoning, 7 marks (2024 Q3; PDF 15 topic):** use the three definitions and examples below.

| Type | Definition | Example |
| --- | --- | --- |
| Deduction | Draw a conclusion guaranteed by valid inference if the premises are true | All birds have feathers; sparrow is a bird → sparrow has feathers |
| Induction | Generalize from observations; conclusion is probable, not guaranteed | Several observed crows are black → crows are probably black |
| Abduction | Infer a plausible explanation for evidence | Wet ground → perhaps it rained; other causes remain possible |

**Recall:** represent → search → subgoals → legal operators → goal test.

## Test yourself — answer before expanding

> [!question]- What must a 10-mark GPS/Hanoi answer include?
> GPS definition; initial/goal states, operators and constraints; subgoals; seven moves; advantages and limitations.

> [!question]- What is the difference between an algorithm and a heuristic?
> An algorithm has specified steps and guarantees under its assumptions; a heuristic is a shortcut without that guarantee.

> [!question]- How is a prototype different from a concept?
> A concept is the category; a prototype is a typical representative.


---
Source: condensed from [Organize PDF Topics](https://chatgpt.com/c/6aef17a8-9c54-83ec-8e63-e1a2ab7ed46f). Updated 10 November 2026.
