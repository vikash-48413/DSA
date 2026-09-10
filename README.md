# FAANG & AI Engineering Data Structures & Algorithms (DSA) Roadmap

Welcome to your daily **FAANG & AI-Engineer DSA Practice Repository**. This repository is structured into interactive **Jupyter Notebooks (`.ipynb`)** across 7 distinct phases to help you practice Data Structures & Algorithms from fundamentals to advanced AI systems coding, tailored for FAANG software engineering and AI/ML engineering interviews.

---

## 🎯 The Golden Daily Practice Loop

For every topic notebook:
1. **Learn & Trigger**: Read the FAANG pattern triggers & AI Engineering mapping markdown cells.
2. **Implement From Scratch**: Code the pure Python data structure/algorithm without external libraries.
3. **Verify with Tests**: Run the pre-written unit test assertions.
4. **Benchmark & Pythonic Alternative**: Compare with standard library (`heapq`, `collections`, `dict`), `numpy`, or `torch`.
5. **Solve FAANG Problems**: Attempt the curated LeetCode problem stubs.
6. **Commit & Push**: Commit daily using convention `day-NN-topic-description` to build your GitHub activity green grid.

---

## 📂 Repository Directory & Notebook Index

### ⚙️ [00-setup](./00-setup/)
- [01_environment_setup.ipynb](./00-setup/01_environment_setup.ipynb) — Virtualenv, Jupyter kernel, Git workflow.
- [02_daily_log_template.ipynb](./00-setup/02_daily_log_template.ipynb) — Progress, time complexity, & mistake tracking log.

### 🐍 [01-python-foundations](./01-python-foundations/)
- [01_variables_and_types.ipynb](./01-python-foundations/01_variables_and_types.ipynb) — Primitives, casting, f-strings, type hints.
- [02_operators_and_expressions.ipynb](./01-python-foundations/02_operators_and_expressions.ipynb) — Logical, membership (`in`), identity (`is`), bitwise operators (`&`, `|`, `^`).
- [03_control_flow_and_conditionals.ipynb](./01-python-foundations/03_control_flow_and_conditionals.ipynb) — `if/elif/else`, pattern matching (`match/case`), error handling.
- [04_loops_and_comprehensions.ipynb](./01-python-foundations/04_loops_and_comprehensions.ipynb) — List, dict, set comprehensions & generator expressions.
- [05_functions_args_kwargs.ipynb](./01-python-foundations/05_functions_args_kwargs.ipynb) — `*args`, `**kwargs`, closures, default param pitfalls, lambdas.
- [06_string_manipulation.ipynb](./01-python-foundations/06_string_manipulation.ipynb) — String slicing, immutability, `join`, `split`, regex basics.
- [07_lists_and_tuples.ipynb](./01-python-foundations/07_lists_and_tuples.ipynb) — List operations, tuple immutability, unpacking, memory layouts.
- [08_dicts_and_sets.ipynb](./01-python-foundations/08_dicts_and_sets.ipynb) — Hash tables, O(1) lookups, set operations, frequency mapping.
- [09_iterators_and_generators.ipynb](./01-python-foundations/09_iterators_and_generators.ipynb) — `yield`, memory-efficient data streaming (100GB datasets).
- [10_oop_dunder_methods.ipynb](./01-python-foundations/10_oop_dunder_methods.ipynb) — Classes, `__len__`, `__getitem__`, inheritance (PyTorch Dataset pattern).

### 🏗️ [02-data-structures](./02-data-structures/)
- [01_dynamic_array.ipynb](./02-data-structures/01_dynamic_array.ipynb) — Resizable dynamic array from scratch (amortized O(1) append).
- [02_singly_doubly_linked_list.ipynb](./02-data-structures/02_singly_doubly_linked_list.ipynb) — Node manipulation, linked list reversal, pointer management.
- [03_hash_map_from_scratch.ipynb](./02-data-structures/03_hash_map_from_scratch.ipynb) — Hash collision chaining, load factor, dynamic resizing.
- [04_hash_set_from_scratch.ipynb](./02-data-structures/04_hash_set_from_scratch.ipynb) — Set implementation for O(1) deduplication and membership checks.
- [05_stack.ipynb](./02-data-structures/05_stack.ipynb) — LIFO Stack (push, pop, peek), array-backed stack.
- [06_queue_and_deque.ipynb](./02-data-structures/06_queue_and_deque.ipynb) — FIFO Queue, circular buffer, double-ended queue (`collections.deque`).
- [07_binary_heap_min_max.ipynb](./02-data-structures/07_binary_heap_min_max.ipynb) — Min-Heap & Max-Heap from scratch (sift-up, sift-down, `heapq`).
- [08_binary_tree_and_bst.ipynb](./02-data-structures/08_binary_tree_and_bst.ipynb) — Binary Search Tree insertion, deletion, lookup.
- [09_trie_prefix_tree.ipynb](./02-data-structures/09_trie_prefix_tree.ipynb) — Prefix tree insert, search, `starts_with` for tokenizers.
- [10_graph_adjacency_list_matrix.ipynb](./02-data-structures/10_graph_adjacency_list_matrix.ipynb) — Adjacency list & matrix graph representations.
- [11_matrix_2d_array.ipynb](./02-data-structures/11_matrix_2d_array.ipynb) — 2D array manipulation, matrix transpose, manual matrix multiply.

### ⚡ [03-dsa-patterns](./03-dsa-patterns/)
- [01_two_pointers.ipynb](./03-dsa-patterns/01_two_pointers.ipynb) — Opposite and same-direction pointers on sorted data.
- [02_sliding_window.ipynb](./03-dsa-patterns/02_sliding_window.ipynb) — Fixed & dynamic window size (LLM context window management).
- [03_hashing.ipynb](./03-dsa-patterns/03_hashing.ipynb) — Frequency maps, complement search, tokenizer vocab lookups.
- [04_prefix_sum.ipynb](./03-dsa-patterns/04_prefix_sum.ipynb) — Range sum queries, running accumulators, normalization stats.
- [05_monotonic_stack.ipynb](./03-dsa-patterns/05_monotonic_stack.ipynb) — Next greater/smaller element queries, expression parsing.
- [06_queue_bfs.ipynb](./03-dsa-patterns/06_queue_bfs.ipynb) — Level-order BFS traversal, shortest unweighted path.
- [07_heap_topk.ipynb](./03-dsa-patterns/07_heap_topk.ipynb) — Streaming top-K retrieval, vector DB search, beam search.
- [08_binary_search.ipynb](./03-dsa-patterns/08_binary_search.ipynb) — O(log N) search on sorted arrays & monotonic search spaces.
- [09_fast_slow_pointers.ipynb](./03-dsa-patterns/09_fast_slow_pointers.ipynb) — Floyd's cycle detection (agentic loop detection).
- [10_intervals_greedy.ipynb](./03-dsa-patterns/10_intervals_greedy.ipynb) — Merging overlapping intervals, greedy request scheduling.
- [11_backtracking.ipynb](./03-dsa-patterns/11_backtracking.ipynb) — State-space tree search (permutations, combinations, N-Queens).
- [12_dynamic_programming.ipynb](./03-dsa-patterns/12_dynamic_programming.ipynb) — Memoization & Tabulation (Edit Distance, KV-Cache memoization).

### 🌲 [04-advanced-dsa](./04-advanced-dsa/)
- [01_tree_traversals_lca.ipynb](./04-advanced-dsa/01_tree_traversals_lca.ipynb) — Pre/in/post/level order, Lowest Common Ancestor.
- [02_trie_autocomplete.ipynb](./04-advanced-dsa/02_trie_autocomplete.ipynb) — DFS prefix suggestion autocomplete, subword tokenizer decoding.
- [03_graph_topological_sort_dsu.ipynb](./04-advanced-dsa/03_graph_topological_sort_dsu.ipynb) — Kahn's BFS topo sort, Disjoint Set Union (Union-Find).
- [04_segment_trees.ipynb](./04-advanced-dsa/04_segment_trees.ipynb) — O(log N) range queries & point updates.

### 🤖 [05-ai-engineering](./05-ai-engineering/)
- [01_systems_matrix_ops.ipynb](./05-ai-engineering/01_systems_matrix_ops.ipynb) — Pure Python vs vectorized NumPy MatMul ($Y = XW + b$).
- [02_systems_data_loader_generators.ipynb](./05-ai-engineering/02_systems_data_loader_generators.ipynb) — Out-of-core streaming dataset loader with shuffling buffer.
- [03_systems_streaming_topk.ipynb](./05-ai-engineering/03_systems_streaming_topk.ipynb) — Streaming top-K token logit tracker using Min-Heap.
- [04_systems_lru_cache.ipynb](./05-ai-engineering/04_systems_lru_cache.ipynb) — LRU Cache (Hash Map + Doubly Linked List) for KV-cache eviction.
- [05_systems_rate_limiter.ipynb](./05-ai-engineering/05_systems_rate_limiter.ipynb) — Token Bucket & Sliding Window Counter rate limiters.
- [06_ml_linear_logistic_regression.ipynb](./05-ai-engineering/06_ml_linear_logistic_regression.ipynb) — Gradient Descent from scratch, MSE & Cross-Entropy loss.
- [07_ml_knn_kmeans.ipynb](./05-ai-engineering/07_ml_knn_kmeans.ipynb) — KNN (distance + heap top-K) and K-Means centroid updates.
- [08_ml_decision_trees_naive_bayes.ipynb](./05-ai-engineering/08_ml_decision_trees_naive_bayes.ipynb) — Decision Trees (Gini impurity splits) & Naive Bayes probability.
- [09_pytorch_tensors_autograd.ipynb](./05-ai-engineering/09_pytorch_tensors_autograd.ipynb) — PyTorch tensors, autograd computation graph, 2-layer MLP.

### 💻 [06-leetcode](./06-leetcode/)
- [01_easy_patterns.ipynb](./06-leetcode/01_easy_patterns.ipynb) — Curated Easy FAANG questions.
- [02_medium_patterns.ipynb](./06-leetcode/02_medium_patterns.ipynb) — Curated Medium FAANG questions.
- [03_hard_patterns.ipynb](./06-leetcode/03_hard_patterns.ipynb) — Curated Hard FAANG questions.

### 📌 [cheat-sheets](./cheat-sheets/)
- [01_master_pattern_to_ai_mapping.ipynb](./cheat-sheets/01_master_pattern_to_ai_mapping.ipynb) — Master table connecting every DSA pattern to production AI tasks.
- [02_time_space_complexity_cheatsheet.ipynb](./cheat-sheets/02_time_space_complexity_cheatsheet.ipynb) — Big-O time & space complexity cheat-sheet.

---

## 🧠 Master Pattern-to-AI Mapping Quick Reference

| DSA Pattern / Structure | Trigger Signal | Direct AI Engineering Production Use Case |
|---|---|---|
| **Hash Map / Set** | Fast O(1) lookup | Tokenizer vocab map (`token -> id`), embedding cache, dataset deduplication |
| **Sliding Window** | Contiguous subarray + condition | LLM context window management, overlapping document chunking for RAG |
| **Heap / Priority Queue** | Top-K, streaming extremum | Vector search top-K nearest neighbors, Beam Search decoding in LLMs |
| **Prefix Sum** | Range sum queries | Cumulative token statistics, rolling mean/variance metrics |
| **Graphs / DAG** | Dependencies, topological sort | Agent tool-call execution DAGs, Graph Neural Networks (GNNs) |
| **Dynamic Programming** | Overlapping subproblems | Edit Distance for text eval metrics, KV-Cache memoization |
| **Generators (`yield`)** | Out-of-core streaming | Reading 100GB+ JSONL training corpus without RAM allocation |

---

## 🛠️ Environment Setup

1. **Activate Virtual Environment**:
   ```bash
   python -m venv .venv
   # Windows PowerShell:
   .\.venv\Scripts\Activate.ps1
   ```
2. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```
3. **Register Jupyter Kernel**:
   ```bash
   python -m ipykernel install --user --name=ai-dsa-env --display-name "Python 3.11 (AI DSA)"
   ```
4. **Open in VS Code**:
   Open any `.ipynb` file in VS Code and select the `ai-dsa-env` Jupyter kernel.

---

## 🚀 Daily Commit Convention

Maintain a consistent daily practice log on GitHub:
```bash
git add .
git commit -m "day-14-heap-topk-streaming: completed streaming topk tracker and test cases"
git push origin main
```
