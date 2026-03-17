Define an object that encapsulates how a set of objects interact. Components talk to the mediator instead of each other, reducing coupling.

## One-line intuition
One hub coordinates many spokes.

• Best for: Complex interaction graphs (chat rooms, UI dialogs, orchestration between modules).
• Watch-outs: Mediator can become a “god object”; keep it focused and split by domain/use-case.
