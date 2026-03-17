Separate an algorithm from the object structure it operates on. Add new operations without changing the existing element classes (at the cost of harder new element types).

## One-line intuition
Add new “behaviors” to a fixed object graph.

• Best for: ASTs, compilers, document/object models where element types are stable but operations grow (pretty print, validate, evaluate).
• Watch-outs: Adding a new element type requires updating all visitors (trade-off flips).
