Pass a request along a chain of handlers until one handles it (or the chain ends). Each handler decides to handle, transform, or forward.

## One-line intuition
Pipeline of decision-makers.

• Best for: Middleware/interceptors, validation pipelines, authorization filters, logging, retry/fallback chains.
• Watch-outs: Harder to reason about “who handled it”, and can silently do nothing if no handler matches.
