Define a one-to-many dependency so when one object changes state, all dependents are notified (push) or can pull the latest state.

## One-line intuition
Publish events; subscribers react independently.

• Best for: Event-driven updates (UI listeners, domain events, cache invalidation, notifications).
• Watch-outs: Memory leaks (unsubscribe), ordering/duplication, “event storms”, and debugging implicit flows.
