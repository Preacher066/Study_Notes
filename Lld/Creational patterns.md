Factory Method

Defines an interface for creating an object but lets subclasses decide which class to instantiate. It handles "which" object to create based on input or logic, centralizing the creation process.  

• Best for: When the exact types of objects to be created are unknown until runtime.  

Builder Pattern

Constructs complex objects step-by-step. Unlike the Factory, which returns a product in one shot, the Builder allows you to specify various configurations before final assembly.  

• Best for: Objects with many optional parameters or complex internal structures.

Abstract Factory

Provides an interface for creating families of related/dependent objects (a “kit”) without specifying their concrete classes. You select a factory (family), then create consistent products from that family.

• Best for: When you need to enforce compatible combinations (e.g., `Button` + `Checkbox` for Windows vs Mac), or swap entire “ecosystems” via config/environment.

Prototype

Creates new objects by cloning an existing instance (the prototype) rather than constructing from scratch. Useful when object creation is expensive or involves lots of configuration.

• Best for: When you need many similar objects with small variations, or when constructor setup is heavy (deep graphs, parsing, expensive I/O avoided via pre-built templates).

Singleton

Ensures only one instance exists and provides a global access point. In interviews, emphasize controlling lifecycle and thread-safety, and when NOT to use it.

• Best for: Stateless shared services (careful), configuration registry, process-wide caches/metrics/loggers (often better via DI than a hard global).
• Watch-outs: Global state, hidden dependencies, testability, concurrency (double-checked locking, static init), and multi-process “singleton” is not guaranteed.

Object Pool

Manages a set of reusable, pre-initialized objects (checkout/return) instead of creating/destroying each time.

• Best for: Expensive-to-create resources with bounded capacity (DB connections, thread pools). Avoid pooling cheap objects (adds complexity and contention).

Quick interview cheat sheet (when asked “which pattern would you use?”)

• Factory Method: Choose a concrete product type at runtime.
• Abstract Factory: Swap an entire family of related products together.
• Builder: Assemble one complex object with many optional parts/steps.
• Prototype: Clone a configured template to make near-copies fast.