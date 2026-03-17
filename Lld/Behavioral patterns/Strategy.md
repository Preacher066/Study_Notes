Encapsulate a family of algorithms and make them interchangeable. The client picks a behavior at runtime without `if/else` branching everywhere.

## One-line intuition
Swap “how we do it” without changing “what we do”.

• Best for: Multiple variants of the same operation (pricing, routing, validation, sorting, payment), selected via input/config.
• Watch-outs: Too many tiny strategy classes; prefer simple lambdas/functions when language/framework supports it.
