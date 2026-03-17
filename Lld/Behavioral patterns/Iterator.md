Provide a way to access elements of a collection sequentially without exposing its underlying representation.

## One-line intuition
Traverse without knowing the data structure.

• Best for: Multiple traversal strategies (DFS/BFS), hiding internal structure, uniform access across different collections.
• Watch-outs: Iterators over mutating collections (concurrency/modification issues).
