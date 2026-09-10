# AI Engineer Coding & Data Structures Roadmap
### From Fundamentals to Advanced Systems — Patterns Mapped to Real AI Engineering Work

> Author's note: this roadmap assumes a working VS Code + Jupyter + GitHub setup. Every algorithmic pattern is paired with the AI/ML engineering context it actually shows up in — tokenization, data pipelines, embeddings, real-time inference, model internals — so you're not learning DSA in a vacuum.

---

## Table of Contents

1. [How to Use This Roadmap](#1-how-to-use-this-roadmap)
2. [Phase 0 — Environment & Repository Setup](#phase-0--environment--repository-setup)
3. [Phase 1 — Programming Foundations](#phase-1--programming-foundations)
4. [Phase 2 — Core Data Structures](#phase-2--core-data-structures)
5. [Phase 3 — Core Algorithmic Patterns](#phase-3--core-algorithmic-patterns)
6. [Phase 4 — Advanced Data Structures & Graph/Tree Systems](#phase-4--advanced-data-structures--graphtree-systems)
7. [Phase 5 — AI-Systems Coding (Pipelines, Tensors, Memory, Streaming)](#phase-5--ai-systems-coding-pipelines-tensors-memory-streaming)
8. [Phase 6 — Applied ML Algorithms as Code](#phase-6--applied-ml-algorithms-as-code)
9. [Master Pattern-to-AI-Task Reference Table](#9-master-pattern-to-ai-task-reference-table)
10. [Practice Strategy & Platforms](#10-practice-strategy--platforms)
11. [GitHub Repository Structure](#11-github-repository-structure)
12. [Jupyter Notebook Structure](#12-jupyter-notebook-structure)
13. [12-Month Timeline](#13-12-month-timeline)
14. [Weekly Schedule](#14-weekly-schedule)
15. [Self-Assessment Checkpoints](#15-self-assessment-checkpoints)

---

## 1. How to Use This Roadmap

Every phase below follows the same four-column shape:

- **Concept** — the CS fundamental.
- **Practice** — the exact problems/patterns to drill (LeetCode-style).
- **AI Engineering Mapping** — where this literally appears in ML/LLM systems code.
- **Deliverable** — what goes into your GitHub repo / notebook.

**Golden loop for every topic:**

```
Learn concept → Implement from scratch (no library) → Solve 8–12 problems
→ Re-implement using the "AI-relevant" version (e.g. NumPy, streaming) → Commit → Note pattern in cheat-sheet
```

Do not skip the "from scratch" step — writing a hash map, a min-heap, or matrix multiply by hand is what makes the library version (dict, heapq, NumPy) stop feeling like magic.

---

## Phase 0 — Environment & Repository Setup

**Duration:** Day 0–1

| Task | Detail |
|---|---|
| VS Code | Install Python, Pylance, Jupyter, GitLens, Black/Ruff formatter extensions |
| Python env | `python -m venv .venv`, pin Python 3.11+, add `requirements.txt` |
| Jupyter | Install `ipykernel`, register kernel per project (`python -m ipykernel install --user --name=ai-eng`) |
| Git | Configure `git config user.name/email`, set up SSH key for GitHub |
| Repo | Create `ai-engineer-journey` (structure in [Section 11](#11-github-repository-structure)) |
| Testing | Install `pytest` — every "from scratch" implementation gets a test file, not just print statements |
| Linting | Add `ruff` + `black` + a pre-commit hook so committed code is always clean |

**Deliverable:** initialized repo with README, `.gitignore` (Python + Jupyter checkpoints), `requirements.txt`, and a `CONTRIBUTING-to-myself.md` describing your daily loop.

---

## Phase 1 — Programming Foundations

**Duration:** Weeks 1–4 · **Goal:** Write Python fluently without a tutorial open.

### 1.1 Core Language

- Variables, types (`int`, `float`, `str`, `bool`, `None`), casting, f-strings
- Operators: arithmetic, comparison, logical, membership (`in`), identity (`is`)
- Control flow: `if/elif/else`, `for`, `while`, `break`, `continue`, `match`
- Comprehensions: list/set/dict comprehensions, generator expressions
- Functions: `*args`, `**kwargs`, default/keyword args, closures, `lambda`
- Type hints (`list[int]`, `dict[str, float]`, `Optional`, `Union`) — used everywhere in production ML code (Pydantic, FastAPI)
- Error handling: `try/except/else/finally`, custom exceptions
- Iterators & **generators** (`yield`) — critical, see AI mapping below
- OOP: classes, `__init__`, inheritance, `@staticmethod`/`@classmethod`, dunder methods (`__len__`, `__getitem__`, `__iter__`)
- Modules, packaging, virtual environments

### 1.2 AI Engineering Mapping

| Python Concept | Where it shows up in AI engineering |
|---|---|
| **Generators (`yield`)** | Out-of-core / streaming dataset loading — reading a 100GB JSONL corpus without loading it into RAM; PyTorch `Dataset`/`IterableDataset` internals; batch generators for training loops |
| **Dict/set comprehensions** | Building vocabulary maps, token-to-id lookups, de-duplicating training examples |
| **`__getitem__`/`__len__`** | Implementing custom PyTorch `Dataset` classes |
| **Context managers (`with`)** | Resource-safe file/model checkpoint loading, timing/profiling blocks, `torch.no_grad()` |
| **Decorators** | Caching (`functools.lru_cache`) for repeated embedding lookups, timing/logging wrappers around inference calls, retry logic around API/model calls |
| **Type hints + Pydantic** | Structured LLM outputs, FastAPI request/response schemas, tool-calling argument validation |
| **`*args`/`**kwargs`** | Wrapping arbitrary model/tokenizer configs, building flexible `agent.run(**kwargs)` interfaces |

### 1.3 Practice Set (150–200 problems)

- Basic arithmetic/logic programs (BMI, interest, conversions) — 20 problems
- Condition-based programs (grading, eligibility, tax slabs) — 20 problems
- Loop-based programs (digit sum, factorial, Fibonacci, primes) — 20 problems
- Pattern printing (triangles, numeric/alpha patterns) — 15 problems
- String manipulation (palindrome, anagram, frequency, compression) — 25 problems
- List/array manipulation (rotation, merging, dedup) — 25 problems
- Dict/set-based problems (frequency maps, grouping) — 15 problems
- Function refactors of the above into reusable modules — ongoing

**Deliverable:** `01-python-foundations/` with one folder per module, each script paired with a `test_*.py`.

---

## Phase 2 — Core Data Structures

**Duration:** Weeks 5–7 · **Goal:** Implement each structure from scratch, then know its Python/NumPy equivalent cold.

| Data Structure | Implement From Scratch | Python/Library Equivalent | AI Engineering Mapping |
|---|---|---|---|
| **Array / Dynamic Array** | Resizable array with amortized `append` | `list`, `numpy.ndarray` | Feature vectors, embeddings, batched tensors |
| **Linked List** | Singly + doubly linked list, insert/delete/reverse | rarely used directly | Understanding pointer-chasing cost — motivates why contiguous tensors (arrays) beat linked structures for GPU compute |
| **Hash Map** | Build one with open addressing / chaining, hash function, resize | `dict` | Tokenizer vocab (`token → id`), embedding lookup tables, caching (`prompt_hash → response`), feature-name → column-index maps |
| **Hash Set** | Same underlying idea as hash map | `set` | De-duplicating training data, checking membership in stopword lists, visited-node tracking in graph traversal |
| **Stack** | Array-backed stack | `list` (append/pop) | Backtracking token generation (beam search backtrack), expression parsing for query DSLs, undo/redo in agent action history |
| **Queue / Deque** | Circular buffer, doubly-ended queue | `collections.deque` | Streaming token windows, BFS in graph-based retrieval, sliding context windows, task queues for agent execution |
| **Priority Queue / Heap** | Binary heap (min/max) with sift-up/down | `heapq` | **Top-K retrieval** (top-K nearest embeddings, top-K logits/beam search), streaming top-K, Dijkstra-based routing, scheduling in job queues |
| **Trees (Binary/BST)** | Insert/delete/search/traversals | n/a (build your own) | Decision tree internals, tokenizer merge structures (BPE uses priority structures), hierarchical clustering |
| **Trie (Prefix Tree)** | Insert/search/prefix-search | n/a | Tokenizer prefix matching, autocomplete for prompt suggestions, vocabulary compression |
| **Graph (adjacency list/matrix)** | BFS/DFS from scratch | `networkx` for production | Knowledge graphs, GNN input structures, dependency graphs for agent tool-call planning, attention as a fully-connected graph |
| **Matrix / 2D Array** | Manual matrix multiply, transpose | `numpy.ndarray` | The literal substrate of every neural network layer — linear layers are matrix multiplies |

**Practice per structure:** implement it → write 3–5 unit tests → solve 6–10 problems using only your own implementation, then re-solve with the standard library equivalent and compare.

**Deliverable:** `02-data-structures/<structure_name>/` with `impl.py`, `test_impl.py`, `problems/`.

---

## Phase 3 — Core Algorithmic Patterns

**Duration:** Weeks 8–14 · **Goal:** Instant pattern recognition — see a problem, name the pattern in under 30 seconds.

For each pattern: **trigger phrase → pattern → AI-relevant application.**

### 3.1 Two Pointers
- **Trigger:** sorted array, pair/triplet sum, palindrome check, in-place partition
- **Problems:** Two Sum II, 3Sum, Container With Most Water, Valid Palindrome, Remove Duplicates
- **AI mapping:** merging two sorted score lists (e.g. merging ranked retrieval results from two indexes), deduplication passes over sorted token streams

### 3.2 Sliding Window
- **Trigger:** contiguous subarray/substring + a running condition
- **Problems:** Longest Substring Without Repeating Characters, Minimum Window Substring, Max Sum Subarray of Size K, Longest Repeating Character Replacement
- **AI mapping:** **context-window management** for LLMs (sliding the attention/context window over long documents), computing rolling statistics over streaming metrics (loss, latency), chunking documents for RAG with overlapping windows

### 3.3 Hashing
- **Trigger:** "have I seen this before?" / need O(1) lookup
- **Problems:** Two Sum, Group Anagrams, Top K Frequent Elements, Subarray Sum Equals K
- **AI mapping:** **tokenization** (building/using a `token → id` vocabulary), de-duplicating training examples, caching embeddings/LLM responses by content hash, feature hashing for large categorical spaces

### 3.4 Prefix Sum
- **Trigger:** repeated range-sum queries
- **Problems:** Range Sum Query, Subarray Sum Equals K, Product of Array Except Self
- **AI mapping:** cumulative token counts for dataset statistics, running normalization stats (mean/variance accumulators), efficient batch-level aggregate metrics

### 3.5 Stack / Monotonic Stack
- **Trigger:** matching pairs, "next greater/smaller element", undo history
- **Problems:** Valid Parentheses, Daily Temperatures, Next Greater Element, Largest Rectangle in Histogram
- **AI mapping:** parsing structured LLM outputs (JSON/code with nested brackets), validating generated code/tool-call syntax, agent action-history/undo stacks

### 3.6 Queue / BFS
- **Trigger:** shortest path in an unweighted graph, level-order processing
- **Problems:** BFS traversal, Rotting Oranges, Sliding Window Maximum, Word Ladder
- **AI mapping:** multi-hop retrieval traversal in a knowledge graph, level-wise exploration of an agent's tool-call/plan tree

### 3.7 Heap / Top-K
- **Trigger:** "Kth largest/smallest", streaming top-K, merge K sorted lists
- **Problems:** Kth Largest Element, Top K Frequent Elements, K Closest Points, Merge K Sorted Lists, Find Median from Data Stream
- **AI mapping:** **top-K nearest-neighbor retrieval** in a vector DB, **beam search** decoding (keep top-K sequences at every step), streaming top-K trending queries/tokens, real-time leaderboards for online evaluation metrics

### 3.8 Binary Search
- **Trigger:** sorted data, "search space", monotonic predicate ("find smallest X such that condition holds")
- **Problems:** Binary Search, Search Rotated Array, Koko Eating Bananas, Capacity to Ship Packages, Median of Two Sorted Arrays
- **AI mapping:** **binary search on answer** for hyperparameter/threshold tuning (e.g. finding the smallest batch size that fits in memory), quantile computation over sorted score distributions

### 3.9 Fast/Slow Pointers & Linked Lists
- **Trigger:** cycle detection, middle-of-sequence
- **Problems:** Linked List Cycle, Middle of Linked List, Reverse Linked List
- **AI mapping:** cycle detection in dependency/tool-call graphs (agents calling each other), streaming-sequence midpoint checks

### 3.10 Intervals / Greedy
- **Trigger:** overlapping ranges, scheduling
- **Problems:** Merge Intervals, Non-overlapping Intervals, Meeting Rooms, Minimum Arrows
- **AI mapping:** merging overlapping text spans (NER/entity extraction post-processing), GPU/job scheduling for training runs, request batching windows for inference servers

### 3.11 Backtracking
- **Trigger:** "generate all combinations/permutations/valid configurations"
- **Problems:** Subsets, Permutations, Combination Sum, N-Queens, Word Search
- **AI mapping:** search-based decoding strategies, constraint-satisfying prompt/parameter search, tree-search components of agentic planning (ReAct-style explore/backtrack)

### 3.12 Dynamic Programming
- **Trigger:** overlapping subproblems + optimal substructure
- **Problems:** Climbing Stairs, House Robber, Coin Change, Longest Common Subsequence, Longest Increasing Subsequence, 0/1 Knapsack, Edit Distance
- **AI mapping:** **edit distance is literally used for text similarity/fuzzy matching in eval pipelines**; sequence alignment logic underlies parts of tokenization (BPE) and diff-based data cleaning; DP intuition (memoization) maps directly to caching intermediate activations (KV-cache in transformer inference is a memoization trick)

---

## Phase 4 — Advanced Data Structures & Graph/Tree Systems

**Duration:** Weeks 15–20

### 4.1 Trees

- **Learn:** binary trees, BST, traversals (pre/in/post/level-order), balanced trees (concept-level), tree height/diameter
- **Problems:** Max Depth, Invert Binary Tree, Validate BST, Lowest Common Ancestor, Serialize/Deserialize Binary Tree, Path Sum
- **AI mapping:** **decision tree / random forest internals** (splits = tree nodes, leaves = predictions), hierarchical softmax structures, document/section hierarchies in RAG chunking (tree-structured retrieval)

### 4.2 Tries

- **Learn:** prefix insert/search, autocomplete
- **Problems:** Implement Trie, Word Search II, Longest Word in Dictionary
- **AI mapping:** subword tokenizer prefix structures, autocomplete/prompt-suggestion systems, efficient vocabulary storage

### 4.3 Graphs

- **Learn:** adjacency list/matrix, DFS, BFS, topological sort, cycle detection, Union-Find (DSU), Dijkstra (concept-level)
- **Problems:** Number of Islands, Course Schedule (topo sort), Clone Graph, Number of Connected Components, Word Ladder, Redundant Connection (Union-Find)
- **AI mapping:** **this is the biggest DSA→AI bridge.**
  - **GNNs (Graph Neural Networks):** message passing = BFS/DFS-style neighbor aggregation; adjacency representation is literally the model input
  - **Attention mechanisms** can be viewed as a fully-connected weighted graph between tokens
  - **Agentic tool-call graphs:** which tool calls which tool, detecting cycles/infinite loops in multi-agent systems
  - **Dependency graphs** for build/training pipelines (topological sort decides execution order of DAG-based ML pipelines, e.g. Airflow/Kubeflow DAGs)
  - **Knowledge graphs** for retrieval-augmented generation
  - **Union-Find:** deduplicating/clustering near-identical training examples, connected-components analysis on entity graphs

### 4.4 Segment Trees / Fenwick Trees (Tier 3 — optional but valuable)

- **Learn:** range query + point update in O(log n)
- **AI mapping:** efficient range statistics over large streaming windows (useful for real-time monitoring/observability dashboards over model metrics)

**Deliverable:** `03-dsa/{trees,tries,graphs}/` with implementation + problems + a short `notes.md` per topic explicitly stating the AI-mapping in your own words (writing it yourself cements it far more than reading this table).

---

## Phase 5 — AI-Systems Coding (Pipelines, Tensors, Memory, Streaming)

**Duration:** Weeks 21–26 · This phase is what separates "did LeetCode" from "AI Engineer."

### 5.1 Matrix & Tensor Operations From Scratch

- Implement matrix multiply, transpose, dot product **without NumPy** (pure Python nested loops) — feel the O(n³) cost
- Re-implement with NumPy vectorization — measure the speedup, understand *why* (contiguous memory, SIMD, no Python-level loop overhead)
- Implement a tiny **feedforward layer** (`y = Wx + b`) and a **softmax** function from scratch
- Implement **batched** matrix multiply (3D tensors) — this is what every transformer layer does under the hood

### 5.2 Out-of-Core Data Pipelines

- Build a **generator-based** data loader that reads a large file line-by-line without loading it fully into memory
- Implement your own simplified `Dataset`/`DataLoader` pair (batching, shuffling with a fixed buffer, `__getitem__`) mirroring PyTorch's API
- Chunking strategy for RAG: fixed-size window vs. sliding window (sliding-window pattern from Phase 3) vs. sentence/paragraph-boundary aware chunking

### 5.3 Real-Time / Streaming Inference Patterns

- Implement a **streaming top-K** tracker (min-heap of size K) for live token/embedding scores
- Implement a **rate limiter** (token bucket / sliding window counter — reuses the sliding-window pattern)
- Implement a simple **LRU cache** (hash map + doubly linked list) — used for KV-cache eviction, embedding cache, response cache
- Implement a basic **request batcher** that groups incoming inference requests within a time window (interval/greedy pattern)

### 5.4 Memory Optimization

- Understand time/space trade-offs: recomputation vs. caching (the KV-cache in transformers is exactly this trade-off)
- Practice reducing space complexity of DP solutions (2D → 1D rolling array) — same principle as activation checkpointing in deep learning
- Understand generator vs. list trade-offs for memory-bound pipelines

### 5.5 Concurrency Basics (for inference serving)

- `asyncio` basics: `async def`, `await`, `asyncio.gather`
- Why async matters for I/O-bound LLM API calls (concurrent tool calls, concurrent retrieval requests)

**Deliverable:** `05-ai-engineering/systems/` — `matrix_ops.py`, `data_loader.py`, `streaming_topk.py`, `lru_cache.py`, `rate_limiter.py`, each with tests + a notebook demonstrating it on a toy dataset.

---

## Phase 6 — Applied ML Algorithms as Code

**Duration:** Weeks 27–32 · Implement the classic algorithms from scratch before relying on `scikit-learn`.

| Algorithm | Implement From Scratch | DSA Concepts Reused |
|---|---|---|
| Linear Regression | Gradient descent loop, loss computation | Arrays, vectorized loops |
| Logistic Regression | Sigmoid + gradient descent | Same as above |
| K-Nearest Neighbors | Distance computation + top-K selection | **Heaps (top-K)**, arrays |
| K-Means Clustering | Centroid assignment/update loop | Arrays, distance metrics |
| Decision Tree | Recursive splitting on best feature | **Trees, recursion** |
| Naive Bayes | Frequency counting + probability | **Hash maps** |
| BFS/DFS-based clustering | Connected components on similarity graph | **Graphs, Union-Find** |

Then move to:

- **NumPy / Pandas** — vectorized equivalents of everything above
- **PyTorch basics** — tensors, autograd, a 2-layer neural net trained on toy data
- **Evaluation metrics from scratch**: precision, recall, F1, confusion matrix (pure Python, then compare to `sklearn.metrics`)

**Deliverable:** `05-ai-engineering/ml-from-scratch/` — one notebook per algorithm, each ending with a side-by-side comparison against the library implementation.

---

## 9. Master Pattern-to-AI-Task Reference Table

Keep this as your permanent cheat sheet.

| DSA Pattern / Structure | Problem Signal | Direct AI Engineering Use Case |
|---|---|---|
| Hash Map / Set | Fast lookup, dedup | Tokenizer vocab, embedding cache, dedup training data |
| Two Pointers | Sorted pair/triplet | Merging ranked retrieval results |
| Sliding Window | Contiguous + condition | LLM context windows, RAG chunking, rate limiting |
| Prefix Sum | Repeated range queries | Running training-metric aggregates |
| Stack / Monotonic Stack | Matching/nesting, next-greater | Parsing generated JSON/code, agent undo history |
| Queue / BFS | Shortest unweighted path | Multi-hop knowledge-graph retrieval |
| Heap / Priority Queue | Top-K, streaming Kth | Vector-search top-K, beam search, streaming leaderboards |
| Binary Search | Sorted / monotonic predicate | Threshold & hyperparameter search, quantiles |
| Fast/Slow Pointers | Cycle detection | Cyclic agent tool-call detection |
| Intervals / Greedy | Overlapping ranges, scheduling | Entity-span merging, GPU job scheduling, request batching |
| Backtracking | Generate all valid configs | Search-based decoding, agentic plan search |
| Dynamic Programming | Overlapping subproblems | Edit distance for eval, KV-cache = memoization |
| Trees / BST | Hierarchical data | Decision trees, hierarchical RAG chunking |
| Trie | Prefix matching | Subword tokenizer structures, autocomplete |
| Graphs / Union-Find | Relationships, connectivity | GNNs, knowledge graphs, DAG pipelines, dedup clustering |
| Matrix Ops | Bulk numeric transforms | Every neural network layer |

---

## 10. Practice Strategy & Platforms

- **Python fundamentals drilling:** HackerRank / Codewars (short daily reps)
- **DSA pattern practice:** LeetCode, filtered by pattern/tag, Easy → Medium, "Hard — selected only"
- **AI-specific coding:** Kaggle notebooks (real data), Hugging Face course exercises, building a tiny RAG pipeline end-to-end as a running project
- **Attempt rule:** 20–30 minutes genuine attempt → self-ask the trigger-word checklist from Section 9 → hint → re-attempt → study solution → **close it and re-code from memory the next day**
- **Problem volume target (quality over quantity):**
  - Python foundations: 150–200 problems
  - Core DSA: 100–150 problems
  - Pattern-based LeetCode: 150–200 problems
  - AI-systems mini-projects: 15–20 end-to-end builds (data loader, top-K tracker, cache, tokenizer, tiny RAG, tiny neural net, etc.)

---

## 11. GitHub Repository Structure

```
ai-engineer-journey/
│
├── 00-setup/
│   ├── environment-notes.md
│   └── daily-log.md
│
├── 01-python-foundations/
│   ├── 01_variables/
│   ├── 02_operators/
│   ├── 03_conditions/
│   ├── 04_loops/
│   ├── 05_patterns/
│   ├── 06_strings/
│   ├── 07_lists/
│   ├── 08_dicts_sets/
│   └── 09_functions/
│
├── 02-data-structures/
│   ├── array/
│   ├── linked-list/
│   ├── hash-map/
│   ├── stack/
│   ├── queue-deque/
│   ├── heap/
│   ├── tree/
│   ├── trie/
│   └── graph/
│       (each folder: impl.py, test_impl.py, problems/, notes.md)
│
├── 03-dsa-patterns/
│   ├── two-pointers/
│   ├── sliding-window/
│   ├── hashing/
│   ├── prefix-sum/
│   ├── monotonic-stack/
│   ├── binary-search/
│   ├── backtracking/
│   ├── greedy-intervals/
│   └── dynamic-programming/
│
├── 04-leetcode/
│   ├── easy/
│   ├── medium/
│   └── hard/
│
├── 05-ai-engineering/
│   ├── systems/            # data_loader.py, streaming_topk.py, lru_cache.py, rate_limiter.py, matrix_ops.py
│   ├── ml-from-scratch/    # linear_regression.ipynb, knn.ipynb, decision_tree.ipynb, kmeans.ipynb...
│   ├── numpy-pandas/
│   ├── pytorch-basics/
│   ├── llm-rag-agents/     # tiny end-to-end RAG + agent project
│   └── mcp/
│
├── 06-backend/
│   ├── fastapi/
│   ├── rest-api/
│   └── testing/
│
├── 07-production/
│   ├── docker/
│   ├── ci-cd/
│   └── observability/
│
├── cheat-sheets/
│   ├── pattern-to-ai-mapping.md   # your personal, evolving version of Section 9
│   └── complexity-cheatsheet.md
│
└── README.md
```

**Commit convention:** `day-NN-topic-description` (e.g. `day-14-heap-topk-streaming`). Every commit message should say *what pattern* was practiced, not just "update."

---

## 12. Jupyter Notebook Structure

Use notebooks only for the AI/ML side (Phase 5–6) and exploratory work — keep DSA in plain `.py` files with tests. Standard notebook template:

1. **Markdown cell:** problem/concept statement + which DSA pattern it reuses
2. **Code cell:** from-scratch pure-Python implementation
3. **Code cell:** complexity analysis (time/space) written as a comment
4. **Code cell:** library-based version (NumPy/PyTorch/sklearn)
5. **Code cell:** benchmark comparing both (timing, memory if relevant)
6. **Markdown cell:** "AI relevance" — one paragraph, written in your own words

---

## 13. 12-Month Timeline

| Months | Focus | Target Output |
|---|---|---|
| 1 | Python foundations (Phase 1) | 150+ small problems, clean repo structure |
| 2 | Core data structures (Phase 2) | All structures implemented from scratch + tested |
| 3–4 | Core algorithmic patterns (Phase 3) | 100–150 pattern problems, cheat sheet v1 |
| 5 | Advanced DS: trees, tries, graphs (Phase 4) | Graph/tree problems + notes.md per topic |
| 6–7 | AI-systems coding (Phase 5) | Data loader, streaming top-K, LRU cache, rate limiter, matrix ops from scratch |
| 8–9 | Applied ML algorithms as code (Phase 6) | 7+ ML algorithms from scratch + NumPy/PyTorch versions |
| 10 | LLM/RAG/Agents mini-project | End-to-end tiny RAG + agent, using tries/graphs/heaps built earlier |
| 11 | Pattern-based LeetCode sprint | 150–200 problems, timed practice |
| 12 | Mock interviews + portfolio polish | 3–4 polished AI-systems projects, README case studies |

---

## 14. Weekly Schedule (steady-state, ~10–12 hrs/week)

| Day | Focus | Hours |
|---|---|---|
| Mon | DSA pattern practice | 2h |
| Tue | AI-systems coding (Phase 5/6) | 2h |
| Wed | Python/DSA review + SQL | 1.5h |
| Thu | LeetCode (pattern-tagged) | 2h |
| Fri | ML-from-scratch or RAG/agent project | 2h |
| Sat | Mixed problem set + repo/notebook cleanup | 1.5h |
| Sun | Weekly review, mistake log, cheat-sheet update | 1h |

---

## 15. Self-Assessment Checkpoints

At the end of every phase, you should be able to answer **yes** to all of these before moving on:

- [ ] Can I implement this structure/pattern from scratch, with no reference, in under 15 minutes?
- [ ] Can I state its time and space complexity without checking?
- [ ] Can I name at least one AI engineering system that relies on it?
- [ ] Have I solved at least 8 problems using it, cold (no hints on the last 2)?
- [ ] Is there a tested, committed implementation in my GitHub repo?
- [ ] Have I written the "AI relevance" note in my own words (not copied from this roadmap)?

If any answer is "no," stay in the phase — do not advance on a schedule at the expense of the loop.

---

### Closing Principle

> Don't learn algorithms as interview trivia. Learn them as the vocabulary that AI systems are built from — a heap *is* your vector search top-K, a hash map *is* your tokenizer, a DAG *is* your training pipeline, and dynamic programming *is* the KV-cache. Once you see the mapping, DSA practice stops being a separate track from AI engineering and becomes the same skill.
