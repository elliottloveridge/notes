# GPT Roadmap: Senior Backend Developer Study Path

## Phase 1: Python Language Mastery
### Python execution model
- How Python executes code
- Bytecode and the interpreter
- Stack frames
- Scope resolution
- LEGB rule
- Why closures work
### Data model and object internals
- Everything is an object
- __init__ vs __new__
- __repr__ vs __str__
- Equality vs identity
- Hashing rules
- Mutability implications
### Types and typing
- Why types matter in Python
- typing module fundamentals
- Optional Union Literal
- Protocols vs inheritance
- Structural typing
- When not to type
- Using mypy as a design tool
### Functions as first class citizens
- Higher order functions
- Closures
- Decorators
- Partial application
- Function purity
- Side effects
### Iteration and generators
- Iterators vs iterables
- Generator functions
- Generator expressions
- Lazy evaluation
- Back-pressure concepts
## Phase 2: Writing Professional Python Code
### Code structure
- Modules vs packages
- Public vs private APIs
- src layout
- Dependency direction
- Avoiding circular imports
### Domain modelling
- Modelling real world concepts
- Anemic vs rich models
- Value objects vs entities
- Immutability by default
- Validation boundaries
### Refactoring
- Recognising code smells
- Extract function
- Extract class
- Inline when appropriate
- Making change safer
### Error handling
- Exceptions as control flow vs signals
- Custom exceptions
- Error boundaries
- When to fail fast
- When to recover
## Phase 3: Testing
### Unit testing
- What a unit really is
- Testing behaviour not structure
- Good vs bad mocks
- Deterministic tests
- Test readability
### Integration testing
- What to integrate
- Where unit tests stop
- Testing boundaries
- Avoiding slow suites
### Property based testing
- Invariants
- Hypothesis basics
- Designing with properties
### Test architecture
- Test data builders
- Fixtures vs factories
- Test isolation
## Phase 4: Concurrency and Async
### Python concurrency model
- GIL reality
- CPU bound vs IO bound
- Threads vs processes
- Multiprocessing pitfalls
### Async Python
- Event loop
- async and await
- Cooperative multitasking
- Cancellation
- Timeouts
### Safety and correctness
- Race conditions
- Deadlocks
- Shared state
- Idempotency
## Phase 5: Backend Fundamentals
### Application architecture
- Layered architecture
- Hexagonal architecture
- Clean architecture
- Dependency inversion
### APIs
- REST principles
- API contracts
- Versioning
- Idempotency
- Pagination
- Error semantics
### Persistence concepts
- Transactions
- Consistency
- Isolation
- Migrations
- Schema evolution
### Observability
- Logging vs metrics vs tracing
- Structured logs
- Correlation IDs
- Debugging production issues
## Phase 6: Systems and Distributed Thinking
### System design fundamentals
- Latency vs throughput
- Caching strategies
- Stateless services
- Horizontal vs vertical scaling
### Reliability
- Failure modes
- Retries and backoff
- Circuit breakers
- Graceful degradation
### Security basics
- Authentication vs authorization
- Secrets management
- Principle of least privilege
- Input validation
## Phase 7: Python in Production
### Performance
- Profiling tools
- Identifying bottlenecks
- Memory vs CPU tradeoffs
- When Python is enough
- When it is not
### Packaging and deployment
- Virtual environments
- Dependency resolution
- Reproducible builds
- Semantic versioning
### Tooling
- Linters
- Formatters
- Static analysis
- CI concepts
## Phase 8: Rust Foundations
### Why Rust
- Memory safety without GC
- Explicit ownership
- Predictable performance
### Rust fundamentals
- Ownership model
- Borrowing rules
- Lifetimes mental model
- Explicit mutability
### Types and enums
- Algebraic data types
- Pattern matching
- Result vs Option
- Error handling philosophy
### Concurrency in Rust
- Fearless concurrency
- Data races prevented at compile time
- Message passing vs shared state
## Phase 9: Systems Thinking via Rust
### Memory layout
- Stack vs heap
- Value vs reference semantics
- Cache friendliness
### Performance intuition
- Zero cost abstractions
- When abstractions leak
- Tradeoffs vs Python
### Cross language perspective
- Why Python hides complexity
- Why Rust forces decisions
- Bringing Rust discipline back to Python
## Phase 10: Senior Engineer Mindset
### Design judgement
- When not to abstract
- When to accept duplication
- When to rewrite vs refactor
### Communication
- Explaining tradeoffs
- Writing technical decisions
- Reviewing code constructively
### Career readiness
- Reading unfamiliar codebases
- Asking the right questions
- Estimating work realistically