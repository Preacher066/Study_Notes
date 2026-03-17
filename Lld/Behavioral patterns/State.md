Allow an object to alter its behavior when its internal state changes. Looks like the object “changed class” without big conditional logic.

## One-line intuition
Move `if(state==...)` into state objects.

• Best for: Workflows with well-defined states and transitions (order lifecycle, vending machine, connection state, playback state).
• Watch-outs: Too many states; keep transitions explicit and avoid circular spaghetti.
