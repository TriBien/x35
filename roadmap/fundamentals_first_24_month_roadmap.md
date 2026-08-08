# Fundamentals-First Software Engineering Roadmap — 24 Months / 104 Weeks

> **Goal:** Build a durable software-engineering foundation that remains useful across languages, runtimes, frameworks, hardware generations, and architectural trends.
>
> **Primary principle:** Fundamentals are the foundation; technology stacks are laboratories for observing those fundamentals.
>
> **Languages:** Assembly → C → Java → JavaScript → Python → Go → Rust  
> **Technical stack:** Linux, Git, React, Node.js, Spring Boot, PostgreSQL, HTTP/TCP, Docker, testing, observability, distributed systems.
>
> **Core ratio:** ~60% fundamentals / ~25% technical stack / ~15% experiments, measurement, documentation.
>
> **Weekly rule:** Every week must produce evidence:
> 1. **Implement it**
> 2. **Measure it**
> 3. **Break it**
> 4. **Explain it**
> 5. **Map it to production**

---

## How to use this roadmap

### The 7 rules

1. **Never learn an abstraction without learning what it hides.**
2. **Never benchmark without a hypothesis.**
3. **Never trust a benchmark without understanding the workload.**
4. **Never claim understanding until you can break the system.**
5. **Implement the primitive before using the framework at least once.**
6. **Compare at least two implementations of every major fundamental.**
7. **Always connect the fundamental back to production.**

### Weekly study loop

- **Day 1:** Read / derive the fundamental.
- **Day 2:** Implement a primitive.
- **Day 3:** Experiment and benchmark.
- **Day 4:** Study the production technology that implements the idea.
- **Day 5:** Apply it to the running project.
- **Day 6:** Break, debug, optimize, and explain.
- **Day 7:** Review, write conclusions, and score yourself.

### Weekly score

| Dimension | Points |
|---|---:|
| Conceptual understanding | 20 |
| Implementation | 20 |
| Experiment | 15 |
| Measurement | 15 |
| Production mapping | 10 |
| Debugging | 10 |
| Explanation | 10 |
| **Total** | **100** |

**Pass:** ≥75  
**Strong:** ≥85  
**Mastery:** ≥90

A week does not count as complete without a working experiment and written evidence.

### Experiment evidence template

```text
Question:
Hypothesis:
Setup:
Implementation:
Measurement:
Result:
Why?
Trade-offs:
Failure mode:
Real-world mapping:
What surprised me?
What would break this design?
```

---

# 24-Month Architecture

| Phase | Months | Theme |
|---|---|---|
| I | 1–3 | Machine, computation, memory, compilation |
| II | 4–6 | OS, runtime, concurrency, networking |
| III | 7–9 | Data structures, algorithms, language design |
| IV | 10–12 | Databases, distributed systems, messaging |
| V | 13–15 | Architecture, APIs, reliability, security |
| VI | 16–18 | Performance, observability, scalability |
| VII | 19–21 | Advanced distributed systems and internals |
| VIII | 22–24 | Capstone, research, architecture mastery |

---

# MONTH 1 — Representation, Bits, CPU

## Week 1 — Bits, Bytes, Number Representation

**Fundamental:** Representation

**Target**
- Understand binary, hexadecimal, signed/unsigned integers, two's complement.
- Understand why data representation is a design decision.

**Experiments / exercises**
- Build decimal ↔ binary ↔ hexadecimal converter.
- Implement signed 8-bit arithmetic and overflow.
- Inspect integer representations in C.
- Build a CLI "binary inspector."

**Production mapping**
- Serialization, network protocols, database numeric types, bit flags.

**Acceptance criteria**
- Explain two's complement without notes.
- Demonstrate overflow with tests.
- Explain why `0.1 + 0.2` is not exactly `0.3` in binary floating point.
- ≥80% experiment score.

**Deliverable:** `binary-inspector/` + `representation.md`

---

## Week 2 — Assembly and CPU Execution

**Fundamental:** Computation

**Target**
- Understand registers, instructions, load/store, branch, call/return, stack frames.

**Experiments**
- Write simple x86-64/ARM64 assembly programs.
- Compile C functions to assembly.
- Trace function calls and loops.
- Compare optimized vs unoptimized assembly.

**Production mapping**
- Compiler optimization, debugging, performance analysis.

**Acceptance**
- Given a small assembly function, identify inputs, outputs, branches, memory accesses.
- Explain a stack frame.
- Explain what a CPU actually executes.

**Deliverable:** annotated assembly notebook.

---

## Week 3 — C Memory Model

**Fundamental:** Memory / resource management

**Target**
- Understand pointers, arrays, structs, stack, heap, allocation.

**Experiments**
- Pointer/address inspector.
- Struct layout with `sizeof` and offsets.
- `malloc/free`.
- Array vs pointer experiments.

**Practical**
- Implement a dynamic vector: `push/pop/get/set/resize/free`.

**Production mapping**
- Java object allocation, Rust ownership, cache locality.

**Acceptance**
- Explain pointer vs value vs address.
- Detect at least three memory errors with tooling.
- Benchmark vector growth.

**Deliverable:** `mini-vector/` + memory report.

---

## Week 4 — Compilation Pipeline

**Fundamental:** Compilation / abstraction

**Target**
- Understand source → compiler → assembly/object → executable.
- Compare native compilation with JVM bytecode.

**Experiments**
- Inspect C object files.
- Inspect Java bytecode with `javap`.
- Compare C executable and Java `.class`.

**Practical**
- Build a tiny arithmetic expression evaluator.

**Production mapping**
- GCC/Clang, javac/JVM, Babel/TypeScript/V8.

**Acceptance**
- Draw both C and Java execution pipelines.
- Explain static compilation vs runtime compilation.

**Deliverable:** compiler-pipeline diagram + evaluator.

---

# MONTH 2 — Memory, OS, Processes

## Week 5 — Virtual Memory and Locality

**Fundamental:** Memory hierarchy

**Target**
- Understand virtual address space, pages, locality, cache.

**Experiments**
- Sequential vs random memory access.
- Array vs linked-list traversal.
- Large allocation experiments.
- Observe page behavior with Linux tooling.

**Practical**
- Build a memory allocator simulator with free blocks and coalescing.

**Acceptance**
- Explain why more RAM does not automatically improve latency.
- Measure locality effects.

**Deliverable:** allocator simulator + benchmark.

---

## Week 6 — Processes and System Calls

**Fundamental:** OS abstraction

**Target**
- Understand process, PID, fork/exec/wait, system calls, file descriptors.

**Experiments**
- `fork()`, `exec()`, `wait()`.
- Parent/child communication with pipes.

**Practical**
- Build a mini Unix shell supporting commands and `|`.

**Production mapping**
- Containers, process supervisors, server workers.

**Acceptance**
- Trace shell → fork → exec → syscall → process.
- Explain process isolation.

**Deliverable:** `mini-shell/`

---

## Week 7 — Files, Buffers, I/O

**Fundamental:** Resource management / I/O

**Target**
- Understand file descriptors, buffering, blocking I/O.

**Experiments**
- Raw vs buffered file reads.
- Large-file throughput.
- Different buffer sizes.

**Practical**
- Build a streaming log analyzer.

**Acceptance**
- Process a large synthetic log without loading the entire file.
- Report throughput, memory, CPU.
- Identify bottleneck.

**Deliverable:** `log-analyzer/` + performance report.

---

## Week 8 — Java Memory and Garbage Collection

**Fundamental:** Automatic resource management

**Target**
- Understand object allocation, reachability, heap, GC, references.

**Experiments**
- Allocation storm.
- Object vs primitive memory.
- Cache-induced retention.
- GC tuning experiments.

**Production mapping**
- Spring request allocation and latency.

**Acceptance**
- Explain why GC improves productivity and can hurt latency.
- Identify a memory-retention bug.

**Deliverable:** JVM memory laboratory.

---

# MONTH 3 — Languages, Types, Runtimes

## Week 9 — Java Type Systems and Abstraction

**Fundamental:** Types / abstraction

**Target**
- Understand interface, inheritance, composition, generics, immutability.

**Experiments**
- Same domain model using inheritance vs composition.
- Generic collection.
- Immutable value object.

**Practical**
- Design extensible payment methods.

**Acceptance**
- Explain when abstraction reduces complexity and when it creates complexity.
- Demonstrate one over-abstraction failure.

**Deliverable:** design comparison.

---

## Week 10 — Spring IoC / Dependency Injection

**Fundamental:** Dependency inversion / composition

**Target**
- Understand dependency graphs and inversion of control.

**Experiments**
- Build a simplified DI container.
- Constructor vs field injection.
- Lifecycle experiment.

**Production mapping**
- Spring `ApplicationContext`, bean lifecycle, proxies.

**Acceptance**
- Explain DI without mentioning Spring first.
- Explain what Spring hides.

**Deliverable:** `mini-di-container/`

---

## Week 11 — JavaScript Language Runtime

**Fundamental:** Dynamic languages / closures / objects

**Target**
- Understand values, references, closures, prototypes, promises.

**Experiments**
- Prototype chain inspector.
- Closure examples.
- Simplified Promise.
- Equality experiments.

**Practical**
- Build a small async task abstraction.

**Acceptance**
- Explain closure and prototype chain from first principles.
- Predict Promise behavior.

**Deliverable:** JS runtime notebook.

---

## Week 12 — Node.js and React Runtime

**Fundamental:** Event-driven computation / state invalidation

**Target**
- Understand Node event loop and React rendering/reconciliation at a conceptual level.

**Experiments**
- Event-loop ordering.
- CPU-bound blocking.
- React unnecessary renders.

**Practical**
- Build product search/filter/pagination/cart UI.
- Build minimal Node HTTP API.

**Acceptance**
- Explain why Node handles I/O concurrency well but CPU-heavy work blocks the event loop.
- Identify and fix unnecessary React renders.

**Deliverable:** first fullstack vertical slice.

---

# MONTH 4 — Concurrency

## Week 13 — Threads and Race Conditions in C

**Fundamental:** Concurrency / synchronization

**Target**
- Understand thread, shared state, race, mutex.

**Experiments**
- Concurrent counter.
- Reproduce race condition.
- Mutex fix.

**Practical**
- Concurrent counter server.

**Acceptance**
- Reproduce race on demand.
- Explain why `counter++` is not necessarily atomic.

**Deliverable:** concurrency lab.

---

## Week 14 — Java Concurrency

**Fundamental:** Thread pools / coordination

**Target**
- Threads, executors, futures, atomics, locks.

**Experiments**
- Fixed thread pool.
- Producer-consumer.
- Atomic vs lock.
- Queue saturation.

**Practical**
- Concurrent job processor.

**Acceptance**
- Measure throughput, latency, CPU, queue depth.
- Explain when more threads hurt.

**Deliverable:** Java worker-pool benchmark.

---

## Week 15 — Go Concurrency

**Fundamental:** Concurrency model

**Target**
- Understand goroutines, channels, select, scheduler conceptually.

**Experiments**
- Goroutines.
- Worker pool.
- Channel pipeline.
- Cancellation.

**Practical**
- Concurrent URL checker.

**Acceptance**
- Compare C threads, Java executors, Go goroutines.
- Explain what abstraction each model provides.

**Deliverable:** Go concurrency comparison.

---

## Week 16 — Node and Spring Concurrency

**Fundamental:** Concurrency under I/O and load

**Target**
- Understand event-loop concurrency vs thread-pool concurrency.

**Experiments**
- CPU-bound Node endpoint.
- Blocking Spring endpoint.
- Pool saturation.

**Practical**
- Load-test both.

**Acceptance**
- Explain p50/p95/p99.
- Identify bottleneck from measurements rather than intuition.

**Deliverable:** concurrency benchmark report.

---

# MONTH 5 — Networking

## Week 17 — TCP and Sockets

**Fundamental:** Communication

**Target**
- Understand IP, port, socket, TCP connection, buffering.

**Experiments**
- C TCP server/client.
- Multiple clients.
- Connection lifecycle.

**Practical**
- Raw TCP chat server.

**Acceptance**
- Trace connection establishment and data flow.
- Explain blocking behavior.

**Deliverable:** TCP lab.

---

## Week 18 — HTTP

**Fundamental:** Protocol abstraction

**Target**
- Understand HTTP request/response, headers, status, body, keep-alive.

**Experiments**
- Minimal HTTP server in Go.
- HTTP client.
- Persistent connection.

**Practical**
- Support GET/POST/JSON.

**Acceptance**
- Explain browser → TCP → HTTP → server.
- Implement HTTP without a web framework once.

**Deliverable:** `mini-http-server/`

---

## Week 19 — API Design

**Fundamental:** Interface / contract

**Target**
- Resources, idempotency, pagination, versioning, auth/authz.

**Practical**
- Design Users/Products/Orders API in Spring.
- Implement Node client.

**Experiments**
- Duplicate POST.
- Idempotency key.
- Pagination strategies.

**Acceptance**
- Design API independent of framework.
- Explain why an API is a contract rather than merely endpoints.

**Deliverable:** API specification + implementation.

---

## Week 20 — Distributed Failure

**Fundamental:** Partial failure

**Target**
- Timeouts, retries, duplicates, backpressure, circuit breakers.

**Experiments**
- Kill service.
- Add latency.
- Retry storm.
- Duplicate requests.

**Practical**
- Node → Spring → PostgreSQL failure lab.

**Acceptance**
- Demonstrate how retries can amplify failure.
- Design bounded retries and idempotency.

**Deliverable:** failure-injection report.

---

# MONTH 6 — Databases and Persistent State

## Week 21 — Data Structures Behind Databases

**Fundamental:** Data organization

**Target**
- Hash tables, trees, heaps, caches.

**Experiments**
- Implement hash table.
- Implement B-tree-like structure or simplified ordered index.
- LRU cache.

**Production mapping**
- Java HashMap, JS Map, PostgreSQL indexes.

**Acceptance**
- Explain why indexes trade write/storage cost for read efficiency.

**Deliverable:** data-structure lab.

---

## Week 22 — PostgreSQL Query Planning

**Fundamental:** Algorithms + cost models

**Target**
- Sequential scan, index scan, joins, query planner.

**Experiments**
- `EXPLAIN ANALYZE`.
- Index/no index.
- Composite index.
- Join alternatives.

**Practical**
- Optimize intentionally slow queries.

**Acceptance**
- Show before/after plan and measurement.
- Never claim an index helps without evidence.

**Deliverable:** query optimization report.

---

## Week 23 — Transactions, MVCC, Isolation

**Fundamental:** Consistency

**Target**
- ACID, isolation levels, locks, MVCC, deadlocks.

**Experiments**
- Lost update.
- Concurrent transfer.
- Deadlock.
- Isolation comparison.

**Practical**
- Bank transfer simulator.

**Acceptance**
- Reproduce and fix at least two consistency failures.
- Explain MVCC conceptually.

**Deliverable:** transaction lab.

---

## Week 24 — Fullstack Vertical System

**Fundamental:** End-to-end system behavior

**Target**
- Connect React, Node, Spring, PostgreSQL.

**Practical**
- Users, products, inventory, cart, orders, authentication.

**Experiments**
- Trace request end-to-end.
- Connection pool.
- Error propagation.

**Acceptance**
- Trace a request from browser to disk and back.
- Identify at least five possible bottlenecks.

**Deliverable:** working commerce core.

---

## Week 25 — Performance and Reliability

**Fundamental:** Resource constraints

**Experiments**
- React render bottleneck.
- Node event-loop blocking.
- JVM GC pressure.
- PostgreSQL slow query.
- Connection-pool saturation.
- Network latency injection.

**Metrics**
- RPS
- p50/p95/p99
- CPU
- memory
- GC
- DB CPU
- active connections
- errors

**Acceptance**
- Every optimization must have baseline → hypothesis → change → measurement → conclusion.

**Deliverable:** performance engineering report.

---

## Week 26 — Month 6 Capstone

**Target**
- Demonstrate machine → OS → runtime → network → database → application understanding.

**Project**
- Production-style commerce core.

**Required**
- React
- Node.js
- Spring Boot
- PostgreSQL
- authentication
- inventory
- orders
- tests
- observability
- load testing
- failure injection

**Acceptance**
- ≥85/100 weekly score.
- Explain all major architectural choices.
- Demonstrate three failure modes and recovery.
- Demonstrate three bottlenecks and evidence-based fixes.

**Deliverable:** architecture document + performance report + demo.

---


# MONTH 7 — Data Structures I

## Week 27 — Complexity, Cost Models, and Benchmarking

### Fundamental
**Abstraction → algorithm → cost model**

The important idea is not memorizing Big-O. It is learning to predict how a workload consumes resources.

### Targets

By the end of the week, you should be able to:

- Explain time complexity and space complexity.
- Distinguish worst-case, average-case, and amortized complexity.
- Understand constant factors.
- Explain why `O(n)` can beat `O(log n)` for small or cache-friendly workloads.
- Build repeatable benchmarks.
- Understand why benchmarks can lie.

### Study

- Big-O notation.
- Amortized analysis.
- CPU cache effects.
- Allocation cost.
- Benchmark warm-up.
- Throughput vs latency.
- p50/p95/p99.

### Experiments

1. Linear search vs binary search.
2. Array scan vs hash lookup.
3. Small array vs large array.
4. Cold vs warm JVM.
5. Java vs Go vs Rust implementation.
6. Node.js benchmark with and without warm-up.

### Practical project

Build `benchmark-lab`:

```text
benchmark/
  search/
  map/
  sort/
  allocation/
  serialization/
```

Each benchmark must report:

```text
workload
iterations
warm-up
mean
p50
p95
p99
throughput
memory
CPU
```

### Production mapping

Apply the model to:

- React list rendering.
- Node request handling.
- Spring collection processing.
- PostgreSQL query execution.

### Failure experiment

Create a benchmark where:

- an apparently faster algorithm loses because of allocation;
- a JIT warm-up effect changes the result;
- an average hides p99 latency.

### Acceptance criteria

You pass only if you can explain:

> "Why is algorithmic complexity necessary but insufficient for performance prediction?"

### Deliverable

`benchmark-lab/` + `week-27-performance-model.md`

---

## Week 28 — Arrays, Strings, Linked Structures

### Fundamental
**Data layout affects computation.**

### Targets

Understand:

- contiguous memory;
- pointer chasing;
- dynamic arrays;
- linked structures;
- string representation;
- mutation vs immutability.

### Implement

From scratch:

- dynamic array;
- singly linked list;
- doubly linked list;
- string builder.

Implement in:

- C;
- Java;
- Rust.

### Experiments

Compare:

```text
Array traversal
vs
Linked-list traversal
```

Measure:

- CPU time;
- memory;
- allocations;
- cache behavior.

### Production mapping

React:

- arrays of component state.

Node:

- Buffers and streams.

Java:

- `ArrayList` vs `LinkedList`.

PostgreSQL:

- page-oriented storage.

### Practical project

Build a **large log-processing pipeline**:

```text
10M log records
→ parse
→ filter
→ aggregate
→ sort
→ report
```

Run multiple data structures.

### Acceptance criteria

You can explain why `LinkedList` is theoretically attractive for insertion but often practically inferior to arrays.

### Deliverable

Benchmark report with a decision matrix:

| Workload | Best structure | Why |
|---|---|---|

---

## Week 29 — Hash Tables

### Fundamental
**Fast lookup is achieved by trading space and computation for organization.**

### Targets

Understand:

- hash functions;
- buckets;
- collisions;
- load factor;
- resizing;
- open addressing;
- chaining.

### Implement

A `HashMap` from scratch in:

- C;
- Java;
- Rust.

Operations:

```text
put
get
remove
contains
resize
```

### Experiments

Test:

- good hash function;
- deliberately bad hash function;
- low load factor;
- high load factor;
- different table sizes.

### Production mapping

Compare:

- Java `HashMap`;
- JavaScript `Map`;
- Python `dict`;
- Go `map`;
- Rust `HashMap`.

### Practical project

Build an **in-memory session store**:

```text
sessionId → session
```

Add TTL and cleanup.

### Failure experiments

- hash collision storm;
- memory growth;
- expired-session accumulation.

### Acceptance

Explain:

> Why does a hash table provide average O(1) lookup but not guaranteed O(1)?

### Deliverable

`hashmap-lab/` + collision benchmark.

---

## Week 30 — Stacks, Queues, Deques, and Backpressure

### Fundamental
**Queues transform concurrency into controlled work.**

### Targets

Understand:

- FIFO;
- LIFO;
- bounded queues;
- producer-consumer;
- backpressure;
- queue growth.

### Implement

- stack;
- queue;
- circular queue;
- deque;
- bounded blocking queue.

### Practical projects

1. Expression parser.
2. Job queue.
3. HTTP request queue.
4. Background email processor.

### Experiments

Producer rate:

```text
100/s
500/s
1,000/s
10,000/s
```

Consumer rate:

```text
100/s
```

Observe:

- queue depth;
- latency;
- memory;
- failure behavior.

### Production mapping

- Node worker queues.
- Spring `ThreadPoolExecutor`.
- Kafka consumer lag.
- PostgreSQL connection pool.

### Acceptance

Demonstrate why:

> Unlimited queues are usually not a reliability strategy.

### Deliverable

Bounded job queue with metrics.

---

# MONTH 8 — Data Structures II

## Week 31 — Trees

### Fundamental
**Hierarchical relationships require recursive structure.**

### Targets

Understand:

- tree terminology;
- recursion;
- DFS;
- BFS;
- binary tree;
- BST.

### Implement

- binary tree;
- BST;
- preorder;
- inorder;
- postorder;
- level-order traversal.

### Practical project

Build a **filesystem indexer**:

```text
directory
├── source
├── tests
└── docs
```

Generate:

- tree;
- file count;
- directory size;
- search results.

### Production mapping

- DOM tree;
- React component tree;
- filesystem;
- database indexes.

### Acceptance

Explain why tree structure appears repeatedly in software.

### Deliverable

Filesystem indexer + traversal visualizer.

---

## Week 32 — Heaps and Priority Queues

### Fundamental
**When the next item matters more than insertion order, priority becomes the organizing principle.**

### Targets

Understand:

- heap invariant;
- min heap;
- max heap;
- heapify;
- priority queue.

### Implement

Binary heap from scratch.

### Practical project

Build a **production-like job scheduler**:

```text
priority
deadline
retryCount
createdAt
```

### Experiments

Compare:

- sorted array;
- heap;
- unsorted array.

Measure:

- insertion;
- extraction;
- memory.

### Production mapping

- schedulers;
- OS scheduling;
- database query priorities;
- task queues.

### Acceptance

Given a workload, justify whether a heap is appropriate.

### Deliverable

Priority scheduler + benchmark.

---

## Week 33 — Balanced Trees and B-Trees

### Fundamental
**Keeping a structure balanced preserves predictable cost.**

### Targets

Understand:

- tree height;
- AVL;
- Red-Black tree;
- B-tree;
- B+ tree;
- page-oriented storage.

### Implement

At least a simplified AVL tree.

### Reverse engineering

Compare:

```text
Java TreeMap
PostgreSQL B-tree index
Rust BTreeMap
```

### Practical experiment

Create:

```text
1M ordered keys
```

Compare:

- unbalanced BST;
- AVL;
- hash table;
- sorted array.

### Acceptance

Explain why databases do not normally use a simple binary search tree for disk indexes.

### Deliverable

Tree comparison report.

---

## Week 34 — Graphs

### Fundamental
**Graphs model relationships rather than hierarchy.**

### Targets

Understand:

- vertices;
- edges;
- directed/undirected graphs;
- weighted graphs;
- adjacency matrix;
- adjacency list.

### Implement

- BFS;
- DFS;
- connected components;
- cycle detection.

### Practical project

Build a **service dependency analyzer**:

```text
checkout
 ├── inventory
 ├── payment
 └── notification
```

Detect:

- dependency cycles;
- unreachable services;
- dependency depth.

### Production mapping

- microservices;
- package dependencies;
- build systems;
- network topology.

### Acceptance

Model a real system as a graph and justify the representation.

### Deliverable

Dependency analyzer.

---

# MONTH 9 — Algorithms

## Week 35 — Searching and Sorting

### Fundamental
**Algorithms are strategies for transforming a workload under resource constraints.**

### Implement

- linear search;
- binary search;
- insertion sort;
- merge sort;
- quicksort;
- heap sort.

### Experiments

Use:

- random;
- sorted;
- reverse-sorted;
- nearly sorted;
- duplicate-heavy datasets.

### Practical project

Build a **large CSV sorting utility**.

Requirements:

- streaming input;
- memory limit;
- configurable sort key.

### Production mapping

- PostgreSQL sort;
- Java streams;
- JavaScript array sorting.

### Acceptance

Explain why benchmark results change with input distribution.

### Deliverable

External-sort-inspired CLI + benchmark report.

---

## Week 36 — Greedy Algorithms

### Fundamental
**Local optimization can produce global optimization only when the problem has the right structure.**

### Study

- interval scheduling;
- activity selection;
- fractional knapsack;
- scheduling;
- caching heuristics.

### Practical project

Build a **meeting-room allocator**.

Input:

```text
meeting(start, end, priority)
```

Output:

- room assignment;
- conflicts;
- utilization.

### Experiment

Compare greedy strategies.

### Acceptance

For every greedy algorithm, identify the property that makes it valid.

### Deliverable

Scheduler + correctness explanation.

---

## Week 37 — Dynamic Programming

### Fundamental
**Dynamic programming turns repeated subproblems into stored state.**

### Study

- overlapping subproblems;
- optimal substructure;
- memoization;
- tabulation;
- state definition.

### Practical applications

Choose at least two:

- pricing;
- inventory allocation;
- resource planning;
- recommendation ranking.

### Exercise

Solve first recursively.

Then:

```text
recursive
→ memoized
→ iterative
```

Measure improvement.

### Acceptance

You must define:

```text
state
transition
base case
answer
```

before coding.

### Deliverable

DP notebook with derivations.

---

## Week 38 — Graph Algorithms

### Study

- Dijkstra;
- topological sorting;
- union-find;
- minimum spanning tree concepts.

### Practical project

Build a **build/dependency planner**.

Example:

```text
A → B
A → C
B → D
C → D
```

Generate valid execution order.

### Production mapping

- Maven/Gradle dependencies;
- npm dependency graph;
- CI pipelines;
- distributed workflows.

### Acceptance

Given a graph, select the correct algorithm and explain why.

### Deliverable

Dependency planner.

---

## Week 39 — Algorithmic Engineering

### Fundamental

**Asymptotic complexity describes growth; engineering performance depends on the entire machine.**

### Experiments

Take one algorithm and optimize:

1. algorithm;
2. memory layout;
3. allocation;
4. I/O;
5. concurrency.

### Compare

- C;
- Java;
- Go;
- Rust;
- Node.

### Acceptance

Produce:

```text
baseline
hypothesis
change
measurement
regression risk
final conclusion
```

### Deliverable

Cross-language performance study.

---

# MONTH 10 — Database Internals

## Week 40 — Storage Engine

### Fundamental
**Persistence converts volatile computation into durable state.**

### Learn

- pages;
- records;
- page headers;
- free space;
- serialization;
- sequential storage.

### Implement

Toy storage engine:

```text
write(record)
read(id)
delete(id)
scan()
```

Store data in fixed-size pages.

### Practical

Use it as a tiny database behind a Java repository.

### Acceptance

Explain:

```text
object
→ record
→ page
→ file
→ disk
```

### Deliverable

Toy storage engine.

---

## Week 41 — Index Internals

### Learn

- B-tree;
- B+tree;
- selectivity;
- cardinality;
- composite indexes;
- covering indexes.

### PostgreSQL experiments

Run:

```sql
EXPLAIN ANALYZE
```

for:

- no index;
- single-column index;
- composite index;
- partial index.

### Practical

Optimize a product-search workload.

### Acceptance

Predict index usefulness before testing, then validate experimentally.

### Deliverable

PostgreSQL index playbook.

---

## Week 42 — WAL, Durability, and Crash Recovery

### Fundamental

**Durability requires recording enough information to reconstruct state after failure.**

### Learn

- write-ahead logging;
- redo;
- checkpoints;
- crash recovery.

### Implement

Toy WAL:

```text
BEGIN
UPDATE
UPDATE
COMMIT
```

Simulate crash.

### Production mapping

PostgreSQL WAL.

### Acceptance

Explain why the database cannot simply write arbitrary pages whenever it wants and still guarantee durability efficiently.

### Deliverable

Toy WAL + recovery demonstration.

---

## Week 43 — Query Execution

### Fundamental

**SQL is a declarative language; the database must transform it into an execution strategy.**

### Learn

- parser;
- logical plan;
- physical plan;
- scan;
- filter;
- join;
- aggregation.

### Implement

Toy query engine over CSV:

```sql
SELECT ...
FROM ...
WHERE ...
```

Support:

- filter;
- projection;
- simple join;
- aggregation.

### Acceptance

Explain why two equivalent SQL queries may have very different execution costs.

### Deliverable

Toy query engine + PostgreSQL comparison.

---

# MONTH 11 — Messaging

## Week 44 — Queues and Durable Work

### Fundamental

**Asynchronous systems decouple producer speed from consumer speed.**

### Build

A job queue with:

- producer;
- consumer;
- retry;
- visibility timeout;
- dead-letter queue.

### Practical

Use it for:

```text
Order → email
Order → invoice
Order → notification
```

### Acceptance

Demonstrate consumer crash without losing the job.

### Deliverable

Job queue service.

---

## Week 45 — Pub/Sub

### Fundamental

**Events decouple producers from multiple consumers.**

### Build

Event bus:

```text
OrderCreated
 ├── Inventory
 ├── Email
 ├── Analytics
 └── Notification
```

### Compare

- direct HTTP;
- queue;
- pub/sub.

### Acceptance

Explain when each communication style is appropriate.

### Deliverable

Event-driven commerce slice.

---

## Week 46 — Delivery Semantics

### Learn

- at-most-once;
- at-least-once;
- effectively-once;
- idempotency.

### Experiment

Kill consumers at different points:

```text
before processing
during processing
after DB commit
before ACK
```

### Practical

Build idempotent order consumer.

### Acceptance

Repeated delivery must not duplicate the business effect.

### Deliverable

Failure matrix + implementation.

---

## Week 47 — Ordering and Partitioning

### Learn

- partition keys;
- ordering scope;
- consumer groups;
- hotspots.

### Practical

Partition events by:

```text
userId
orderId
productId
```

Compare ordering and load distribution.

### Acceptance

Explain:

> Global ordering, throughput, and horizontal scalability are often competing goals.

### Deliverable

Partitioning simulator.

---

# MONTH 12 — Distributed Systems I

## Week 48 — Time and Clocks

### Fundamental

**Distributed computers do not share one perfect clock.**

### Study

- clock drift;
- skew;
- NTP concept;
- logical clocks;
- Lamport timestamps.

### Experiment

Simulate three nodes with different clocks.

### Practical

Build an event-ordering simulator.

### Acceptance

Explain why timestamps alone cannot always determine causal order.

### Deliverable

Logical-clock lab.

---

## Week 49 — Consistency

### Learn

- strong consistency;
- eventual consistency;
- read-your-writes;
- monotonic reads;
- conflict.

### Practical

Build replicated key-value store simulator.

Scenarios:

```text
write A
read B
```

with replication delay.

### Acceptance

Choose consistency requirements for:

- inventory;
- product views;
- analytics;
- user preferences.

### Deliverable

Consistency decision matrix.

---

## Week 50 — Replication

### Learn

- primary/replica;
- synchronous replication;
- asynchronous replication;
- replication lag;
- failover.

### Experiment

Inject:

```text
100ms lag
1s lag
10s lag
```

Observe stale reads.

### Practical

Simulate primary failure.

### Acceptance

Explain why replication is not the same as backup.

### Deliverable

Replication/failover lab.

---

## Week 51 — Consensus Concepts

### Learn

- leader;
- quorum;
- split brain;
- Raft concepts;
- election.

### Build

Simplified leader-election simulator.

### Experiment

Partition network:

```text
A B | C D
```

Observe behavior.

### Acceptance

Explain why quorum matters and why a minority partition should not blindly become leader.

### Deliverable

Consensus notebook.

---

# MONTH 13 — Architecture

## Week 52 — Complexity, Coupling, Cohesion

### Fundamental

**Software complexity is largely the cost of change.**

### Analyze

Existing commerce code.

Measure:

- dependency count;
- module fan-out;
- cyclic dependencies;
- change impact.

### Practical

Refactor a tangled module.

### Acceptance

Show measurable architectural improvement.

### Deliverable

Before/after dependency graph.

---

## Week 53 — Modular Monolith

### Target

Build:

```text
catalog
inventory
order
payment
user
```

as modules in one deployment.

### Rules

Modules cannot directly access another module's internals.

### Experiment

Change inventory implementation without changing order.

### Acceptance

Demonstrate independent change.

### Deliverable

Modular Spring Boot monolith.

---

## Week 54 — Clean Architecture

### Learn

- dependency rule;
- entities;
- use cases;
- adapters;
- infrastructure.

### Apply

Only to business-critical core.

### Critical experiment

Compare:

```text
simple layered architecture
vs
clean architecture
```

Measure:

- code size;
- testability;
- complexity;
- change cost.

### Acceptance

Explain when Clean Architecture is useful and when it is overengineering.

### Deliverable

Architecture decision record.

---

## Week 55 — Hexagonal Architecture

### Build

Ports:

```text
OrderRepository
PaymentGateway
NotificationGateway
```

Adapters:

```text
PostgresOrderRepository
MockPaymentGateway
HttpNotificationGateway
```

### Experiment

Run business logic without infrastructure.

### Acceptance

Core business tests require no database.

### Deliverable

Hexagonal order module.

---

# MONTH 14 — Domain and API Design

## Week 56 — Domain Modeling

### Learn

- entity;
- value object;
- aggregate;
- invariant;
- domain service.

### Practical

Model:

```text
Order
OrderItem
Money
InventoryReservation
```

### Acceptance

Identify which invariants must be enforced transactionally.

### Deliverable

Domain model + invariant catalog.

---

## Week 57 — API Evolution

### Experiments

Version an API from:

```text
v1
```

to:

```text
v2
```

without breaking old clients.

### Study

- backward compatibility;
- additive changes;
- field removal;
- enum evolution;
- pagination evolution.

### Acceptance

Existing automated client tests continue passing.

### Deliverable

API evolution guide.

---

## Week 58 — Error Semantics

### Design

Separate:

```text
validation error
business error
authentication error
authorization error
dependency error
system error
```

### Practical

Standardize error response across React/Node/Spring.

### Acceptance

Frontend can distinguish retryable vs non-retryable errors.

### Deliverable

Error taxonomy.

---

## Week 59 — Authentication and Authorization

### Learn

- authentication vs authorization;
- sessions;
- tokens;
- RBAC;
- least privilege.

### Practical

Implement:

```text
user
admin
seller
```

roles.

### Attack/failure tests

- expired credentials;
- privilege escalation attempt;
- unauthorized resource access.

### Acceptance

Every protected operation has explicit authorization.

### Deliverable

Security model + tests.

---

# MONTH 15 — Testing

## Week 60 — Unit Testing

### Fundamental

**Tests are executable specifications and feedback mechanisms.**

### Build

Domain tests for:

- pricing;
- inventory;
- order state transitions.

### Mutation exercise

Intentionally introduce bugs.

### Acceptance

Tests catch injected defects.

### Deliverable

High-value unit-test suite.

---

## Week 61 — Integration Testing

### Test

- Spring;
- PostgreSQL;
- HTTP;
- transactions.

### Compare

Mock-heavy test vs real integration test.

### Acceptance

Know exactly which boundary each test validates.

### Deliverable

Integration test strategy.

---

## Week 62 — Contract Testing

### Build

Node consumer + Spring provider.

Test:

```text
request schema
response schema
error schema
```

### Break the provider intentionally.

### Acceptance

CI catches incompatible changes.

### Deliverable

Consumer/provider contract suite.

---

## Week 63 — Property and Fuzz Testing

### Targets

Test:

- parser;
- serializer;
- money calculations;
- data structures.

### Properties

Examples:

```text
serialize(deserialize(x)) ≈ x
sort(sort(x)) = sort(x)
```

### Acceptance

Find at least one bug not covered by ordinary examples.

### Deliverable

Property/fuzz test lab.

---

# MONTH 16 — Observability

## Week 64 — Structured Logging

### Implement

Correlation ID:

```text
requestId
traceId
userId
orderId
```

### Practical

Trace one order across services.

### Acceptance

A production incident can be reconstructed from logs.

### Deliverable

Logging standard.

---

## Week 65 — Metrics

### Instrument

- request count;
- error count;
- latency histogram;
- queue depth;
- DB pool;
- JVM GC.

### Experiment

Compare average latency vs p95/p99.

### Acceptance

Explain why averages are dangerous for tail-sensitive systems.

### Deliverable

Metrics dashboard.

---

## Week 66 — Distributed Tracing

### Trace

```text
React
→ Node
→ Spring
→ PostgreSQL
```

### Inject

- DB latency;
- network latency;
- service latency.

### Acceptance

Identify the dominant latency contributor from trace evidence.

### Deliverable

End-to-end trace.

---

## Week 67 — SLOs and Error Budgets

### Define

For example:

```text
availability ≥ 99.9%
p95 checkout latency < 500ms
```

### Study

- SLI;
- SLO;
- SLA;
- error budget.

### Practical

Connect SLO violation to engineering action.

### Acceptance

Explain why "100% availability" is usually economically irrational.

### Deliverable

SLO document.

---

# MONTH 17 — Performance

## Week 68 — CPU Profiling

### Tools

Use appropriate tools for each runtime:

- Linux `perf`;
- Java profiler/JFR;
- Node profiling;
- Go pprof;
- Rust profiling.

### Practical

Find one CPU hotspot.

### Acceptance

Optimization is supported by profiler evidence.

### Deliverable

Flame graph + optimization report.

---

## Week 69 — Memory Profiling

### Investigate

- allocation rate;
- heap;
- retention;
- leaks;
- GC.

### Compare

Java vs Node vs Go vs Rust.

### Practical

Create and diagnose a memory-retention bug.

### Acceptance

Explain:

```text
allocation
→ reachability
→ retention
→ collection
```

### Deliverable

Memory investigation report.

---

## Week 70 — Database Performance

### Investigate

- query plan;
- indexes;
- locks;
- connection pool;
- buffer/cache behavior.

### Practical

Optimize five intentionally slow queries.

### Acceptance

Each optimization has baseline and post-change evidence.

### Deliverable

Database performance playbook.

---

## Week 71 — Load Testing

### Learn

- open workload;
- closed workload;
- saturation;
- concurrency;
- throughput;
- latency.

### Practical

Load test commerce API.

### Required graph

```text
concurrency → throughput
concurrency → p95
concurrency → errors
```

### Acceptance

Identify saturation point.

### Deliverable

Load-test report.

---

# MONTH 18 — Scalability

## Week 72 — Caching

### Learn

- cache-aside;
- write-through;
- TTL;
- invalidation;
- locality.

### Practical

Cache product catalog.

### Experiments

Compare:

```text
0% hit
50% hit
90% hit
99% hit
```

### Acceptance

Quantify cache benefit and stale-data risk.

### Deliverable

Caching decision record.

---

## Week 73 — Connection Pools

### Fundamental

**A pool is a concurrency control mechanism, not merely a performance optimization.**

### Experiment

Test pool sizes:

```text
5
10
20
50
100
```

Measure:

- throughput;
- latency;
- DB CPU;
- queueing.

### Acceptance

Explain why a larger pool can make a system slower.

### Deliverable

Pool-sizing report.

---

## Week 74 — Horizontal Scaling

### Build

Run:

```text
Node x 3
Spring x 3
PostgreSQL
Load balancer
```

### Investigate

- statelessness;
- sessions;
- shared cache;
- database bottleneck.

### Acceptance

Demonstrate scaling until the next bottleneck appears.

### Deliverable

Scaling experiment.

---

## Week 75 — Backpressure and Graceful Degradation

### Build

Bounded queues and admission control.

### Failure

Increase load beyond capacity.

### Compare

Without backpressure vs with backpressure.

### Acceptance

System fails predictably rather than exhausting memory.

### Deliverable

Overload-control report.

---

# MONTH 19 — Reliability

## Week 76 — Failure Models

### Classify

- crash;
- timeout;
- partial failure;
- overload;
- corruption;
- dependency failure.

### Build

Failure-injection middleware.

### Acceptance

Every major dependency has a documented failure model.

### Deliverable

Failure matrix.

---

## Week 77 — Retry and Circuit Breaking

### Implement

- exponential backoff;
- jitter;
- maximum attempts;
- circuit breaker.

### Experiment

Create downstream outage.

### Compare

Naive retry vs bounded retry.

### Acceptance

Show how retry storms can amplify outages.

### Deliverable

Retry/circuit-breaker lab.

---

## Week 78 — Idempotency

### Apply to

- payment;
- order creation;
- inventory reservation.

### Experiment

Send same request:

```text
1x
2x
10x
100x
```

### Acceptance

Business effect remains correct.

### Deliverable

Idempotency design.

---

## Week 79 — Disaster Recovery

### Implement

- PostgreSQL backup;
- restore;
- verification;
- recovery procedure.

### Measure

- RPO;
- RTO.

### Acceptance

Actually restore the system rather than merely documenting backup commands.

### Deliverable

Recovery runbook.

---

# MONTH 20 — Security

## Week 80 — Threat Modeling

### Learn

- assets;
- trust boundaries;
- attack surface;
- threats;
- mitigations.

### Practical

Threat-model:

```text
React
→ Node
→ Spring
→ PostgreSQL
```

### Acceptance

Prioritize threats by impact and likelihood.

### Deliverable

Threat model.

---

## Week 81 — Web Security

### Study and safely reproduce locally

- XSS;
- CSRF;
- SQL injection;
- SSRF;
- insecure direct object reference.

### Fix

Each vulnerability.

### Acceptance

Explain root cause rather than memorizing mitigation.

### Deliverable

Security lab.

---

## Week 82 — Authentication Security

### Study

- password hashing;
- salts;
- sessions;
- tokens;
- expiration;
- rotation.

### Practical

Implement secure password lifecycle.

### Acceptance

Explain why passwords should be hashed rather than encrypted.

### Deliverable

Authentication security review.

---

## Week 83 — Supply Chain and Secrets

### Implement

- dependency scanning;
- secret detection;
- environment separation;
- SBOM concepts.

### Practical

Remove all hardcoded secrets.

### Acceptance

CI rejects accidental secret commits.

### Deliverable

Secure CI baseline.

---

# MONTH 21 — Runtime Internals

## Week 84 — JVM Internals

### Study

```text
.java
→ javac
→ bytecode
→ class loading
→ interpreter/JIT
→ machine code
```

### Experiments

- warm-up;
- allocation;
- GC;
- JIT compilation;
- escape-analysis concepts.

### Practical

Profile a Spring endpoint.

### Acceptance

Explain why JVM applications may behave differently during startup and steady state.

### Deliverable

JVM runtime report.

---

## Week 85 — V8 and Node Runtime

### Study

- parsing;
- bytecode/interpreter concepts;
- JIT;
- hidden classes/concepts;
- event loop;
- libuv.

### Experiments

Compare:

```text
CPU-bound endpoint
I/O-bound endpoint
```

### Acceptance

Explain why Node is excellent for many I/O workloads but not automatically ideal for CPU-heavy workloads.

### Deliverable

Node runtime report.

---

## Week 86 — Rust Ownership and Memory Safety

### Fundamental

**Memory safety can be enforced through language semantics and compile-time reasoning.**

### Study

- ownership;
- borrowing;
- lifetimes;
- `Option`;
- `Result`;
- traits.

### Rewrite

One C memory-management experiment in Rust.

### Break

Try to reproduce:

- use-after-free;
- double-free;
- data race.

Observe compiler rejection.

### Acceptance

Explain the safety property, not merely the syntax.

### Deliverable

C vs Rust memory-safety comparison.

---

## Week 87 — Go Runtime and Concurrency

### Study

- goroutines;
- scheduler;
- channels;
- GC;
- interfaces.

### Practical

Build high-concurrency HTTP service.

### Compare

Go vs Java vs Node.

Measure:

- throughput;
- p99;
- memory;
- CPU;
- startup.

### Acceptance

Explain trade-offs rather than declaring one language "faster."

### Deliverable

Runtime comparison.

---

# MONTH 22 — Advanced Distributed Systems

## Week 88 — Sharding

### Learn

- partition key;
- range sharding;
- hash sharding;
- hotspot;
- rebalancing.

### Practical

Build sharded key-value store simulator.

### Experiment

Compare keys:

```text
userId
region
timestamp
hash(userId)
```

### Acceptance

Identify hotspot scenarios.

### Deliverable

Sharding decision matrix.

---

## Week 89 — Distributed Transactions

### Study

- two-phase commit;
- saga;
- compensation;
- eventual consistency.

### Practical

Model:

```text
Order
→ Payment
→ Inventory
→ Shipping
```

### Failure injection

Fail each stage.

### Acceptance

Recover without creating impossible business state.

### Deliverable

Saga implementation/design.

---

## Week 90 — Event-Driven Architecture

### Build

Convert part of commerce flow:

```text
OrderCreated
→ InventoryReserved
→ PaymentAuthorized
→ OrderConfirmed
```

### Study

- event schema;
- replay;
- consumer versioning;
- event ownership.

### Acceptance

Rebuild derived state by replaying events.

### Deliverable

Event-driven workflow.

---

## Week 91 — Multi-Region Systems

### Study

- latency;
- replication;
- regional failure;
- routing;
- consistency.

### Practical

Simulate two regions.

### Failure

Kill Region A.

### Acceptance

Define explicitly:

```text
what remains available?
what becomes stale?
what becomes unavailable?
```

### Deliverable

Multi-region architecture + failure analysis.

---

# MONTH 23 — Architecture at Scale

## Week 92 — Capacity Planning

### Fundamental

**Architecture is resource allocation under workload constraints.**

### Learn

- Little's Law;
- throughput;
- concurrency;
- arrival rate;
- service time.

### Practical

Estimate:

```text
requests/sec
CPU
memory
DB connections
storage
network
```

### Acceptance

Produce a capacity model with explicit assumptions.

### Deliverable

Capacity spreadsheet/model.

---

## Week 93 — Hot Paths

### Identify

The most valuable end-to-end business path:

```text
Browse
→ Cart
→ Checkout
→ Order
```

### Profile

Find:

- CPU bottleneck;
- DB bottleneck;
- network bottleneck;
- serialization;
- lock contention.

### Optimize

Only the dominant bottleneck.

### Acceptance

Demonstrate measurable end-to-end improvement.

### Deliverable

Hot-path optimization report.

---

## Week 94 — Cost Engineering

### Compare architectures

Example:

```text
monolith
modular monolith
microservices
serverless
```

### Calculate

- compute;
- DB;
- network;
- storage;
- operational complexity.

### Acceptance

Defend a design using both technical and economic reasoning.

### Deliverable

Cost/performance model.

---

## Week 95 — Architecture Review

### Perform adversarial review

Ask:

- What happens if PostgreSQL is slow?
- What if Redis disappears?
- What if a service receives 10x traffic?
- What if messages duplicate?
- What if a region disappears?
- What if schema changes?
- What if credentials leak?
- What if p99 becomes 10x worse?

### Deliverable

At least 10 ADRs.

Each ADR:

```text
Context
Decision
Alternatives
Trade-offs
Consequences
Evidence
```

### Acceptance

Defend the architecture without relying on framework names.

---

# MONTH 24 — Master Capstone

## Week 96 — Requirements and Workload Model

### Target

Start from the problem rather than technology.

Define:

- users;
- business invariants;
- traffic;
- workload distribution;
- latency requirements;
- availability;
- consistency;
- security;
- cost constraints.

### Deliverable

Requirements + workload specification.

### Acceptance

Every architecture decision can trace back to a requirement.

---

## Week 97 — Domain and Data Model

### Design

- domain boundaries;
- entities;
- value objects;
- aggregates;
- PostgreSQL schema;
- indexes;
- transactions.

### Acceptance

Explain:

```text
Why this aggregate?
Why this transaction boundary?
Why this index?
Why this consistency model?
```

### Deliverable

Domain model + ERD + invariant catalog.

---

## Week 98 — Core Services

### Implement

```text
React
Node.js
Spring Boot
PostgreSQL
```

### Features

- authentication;
- catalog;
- cart;
- inventory;
- order.

### Engineering requirements

- unit tests;
- integration tests;
- API contract;
- structured errors.

### Acceptance

Vertical slice works end-to-end.

---

## Week 99 — Concurrency and Transactions

### Focus

Inventory/order race conditions.

### Tests

Concurrent:

```text
100 buyers
10 inventory units
```

### Verify

- no negative inventory;
- no duplicate order;
- correct transaction semantics.

### Acceptance

System remains correct under concurrent load.

### Deliverable

Concurrency test suite + transaction analysis.

---

## Week 100 — Messaging

### Introduce

Asynchronous events:

```text
OrderCreated
InventoryReserved
PaymentAuthorized
NotificationRequested
```

### Requirements

- idempotent consumers;
- retries;
- DLQ;
- observability.

### Acceptance

Kill consumers during processing and recover correctly.

### Deliverable

Event-driven subsystem.

---

## Week 101 — Scalability

### Deploy

At least:

```text
React
Node x N
Spring x N
PostgreSQL
cache
queue
load generator
```

### Experiments

Scale:

```text
1 instance
→ 2
→ 4
→ 8
```

### Measure

- throughput;
- p50;
- p95;
- p99;
- CPU;
- memory;
- DB load;
- queue lag.

### Acceptance

Identify the first bottleneck at each scale.

### Deliverable

Scaling report.

---

## Week 102 — Reliability and Security

### Failure tests

- DB unavailable;
- DB slow;
- cache unavailable;
- queue unavailable;
- downstream timeout;
- service crash;
- duplicate event;
- invalid credentials;
- unauthorized access.

### Security

Complete:

- threat model;
- dependency scan;
- secret scan;
- authentication review;
- authorization review.

### Acceptance

Every major failure has:

```text
detection
containment
recovery
verification
```

### Deliverable

Reliability + security report.

---

## Week 103 — Performance Engineering

### Method

Do not optimize by intuition.

Use:

```text
baseline
→ profile
→ hypothesis
→ change
→ benchmark
→ regression test
```

### Profile

- React;
- Node;
- Spring/JVM;
- PostgreSQL;
- network.

### Optimize

At least:

- one CPU bottleneck;
- one memory bottleneck;
- one database bottleneck;
- one network/serialization bottleneck.

### Acceptance

Show numerical improvement.

### Deliverable

Final performance engineering report.

---

## Week 104 — Final Defense

### Final system

Produce a complete engineering package:

```text
architecture/
  architecture.md
  adr/
  domain-model.md
  data-model.md
  threat-model.md
  failure-model.md
  capacity-model.md
  slo.md

performance/
  benchmarks/
  profiles/
  reports/

testing/
  unit/
  integration/
  contract/
  property/
  load/

operations/
  deployment.md
  backup-restore.md
  incident-runbook.md
```

### Final oral defense

Answer these without looking at notes:

1. What problem does the system solve?
2. What are its invariants?
3. Where are its boundaries?
4. Where is state stored?
5. How does a request travel through the system?
6. What happens at the CPU level?
7. What happens in memory?
8. What does the runtime do?
9. What happens in the OS?
10. What happens over the network?
11. What happens inside PostgreSQL?
12. What happens when two requests race?
13. What happens when a dependency fails?
14. What happens when traffic increases 10x?
15. What is the dominant bottleneck?
16. What is the most expensive resource?
17. What is the weakest reliability assumption?
18. What security boundary matters most?
19. Which abstraction provides the most value?
20. Which abstraction adds unnecessary complexity?
21. What would you remove if forced to simplify the system by 50%?
22. What would you keep if only the fundamental behavior mattered?

### Final mastery test

For each major concept, prove all five levels:

```text
LEVEL 1 — Explain
        ↓
LEVEL 2 — Implement
        ↓
LEVEL 3 — Break
        ↓
LEVEL 4 — Measure
        ↓
LEVEL 5 — Transfer
```

The final objective is not:

> "I know React, Node, Java, Spring, PostgreSQL, Go, Rust and Python."

It is:

> "I can recognize the same underlying computational idea regardless of the technology implementing it."

---

# Weekly Deliverable Standard

Every week from Week 27 onward must leave behind four artifacts:

### 1. Code

A minimal implementation from first principles.

### 2. Experiment

A reproducible experiment with a hypothesis.

### 3. Production mapping

At least one connection to:

- React;
- Node;
- Java;
- Spring;
- PostgreSQL;
- Linux;
- distributed systems.

### 4. Explanation

One short document answering:

```text
What is it?
Why does it exist?
What problem does it solve?
What does it cost?
When does it fail?
How do I measure it?
Where have I seen it in production?
What alternative exists?
```

---

# Monthly Gate Criteria

## Month 7
Can reason about data structures from workload.

## Month 8
Can select and implement appropriate structures.

## Month 9
Can select algorithms based on constraints.

## Month 10
Can reason about database internals rather than treating SQL as magic.

## Month 11
Can design asynchronous communication and handle duplicates.

## Month 12
Can reason about distributed consistency and failure.

## Month 13
Can control architectural complexity.

## Month 14
Can design stable domains and APIs.

## Month 15
Can use tests as engineering feedback rather than merely coverage.

## Month 16
Can diagnose production behavior using telemetry.

## Month 17
Can optimize using evidence.

## Month 18
Can scale without blindly adding machines.

## Month 19
Can design for failure.

## Month 20
Can reason about security from first principles.

## Month 21
Can explain what the major runtimes are actually doing.

## Month 22
Can reason about distributed workflows and multi-region trade-offs.

## Month 23
Can connect architecture to capacity and cost.

## Month 24
Can independently design, implement, measure, debug, and defend a production-grade system.

---

# The Reverse-Engineering Habit

Whenever learning a new technology, apply this sequence:

```text
Framework
   ↓
Library
   ↓
Runtime
   ↓
OS
   ↓
CPU / Memory / Network
   ↓
Fundamental
```

Examples:

```text
React rendering
→ reconciliation
→ tree algorithms
→ data structures

Spring DI
→ dependency graph
→ graph traversal
→ abstraction + inversion of control

PostgreSQL index
→ B-tree
→ balanced tree
→ algorithm + storage locality

Node async I/O
→ event loop
→ OS I/O
→ concurrency

Java GC
→ reachability
→ object graph
→ memory management

Rust ownership
→ borrow checking
→ aliasing rules
→ memory safety

Go goroutines
→ scheduler
→ concurrency
→ resource management
```

---

# Cross-Language Map

| Fundamental | Assembly | C | Java | JavaScript | Python | Go | Rust |
|---|---|---|---|---|---|---|---|
| Memory | Registers | Pointers | GC | GC | GC | GC | Ownership |
| Resource management | Explicit | Manual | GC/try-with-resources | GC | GC/context | defer | RAII/ownership |
| Compilation | Native ISA | Native | Bytecode/JIT | JIT/runtime | Interpreter/VM | Native | Native/LLVM |
| Types | ISA-level | Static | Static | Dynamic | Dynamic | Static | Static/strong |
| Concurrency | CPU primitives | pthread | Threads/executors | Event loop/workers | threads/processes/async | Goroutines | threads/async |
| Networking | syscalls | sockets | NIO/blocking | Node/libuv | sockets/asyncio | net | std/tokio ecosystem |
| Abstraction | instructions | functions/structs | classes/interfaces | objects/functions | objects/functions | interfaces | traits/types |
| Safety | none | programmer | runtime/compiler | runtime | runtime | runtime | compiler |

---

# Technical Stack Mapping

## React

Fundamentals:
- state
- invalidation
- rendering
- trees
- memoization
- scheduling
- network latency

Key questions:
- What causes rendering?
- Where should state live?
- What work is repeated?
- What does memoization cost?

## Node.js

Fundamentals:
- event loop
- async I/O
- concurrency
- memory
- streams
- networking

Key questions:
- What blocks the event loop?
- Where does concurrency come from?
- What happens under CPU saturation?

## Java / Spring

Fundamentals:
- types
- abstraction
- dependency inversion
- runtime
- memory
- GC
- concurrency
- transactions

Key questions:
- What does Spring hide?
- What does the JVM optimize?
- What happens during a request?

## PostgreSQL

Fundamentals:
- data structures
- persistence
- indexing
- transactions
- concurrency
- durability
- query optimization

Key questions:
- Why this index?
- Why this plan?
- What happens during concurrent updates?
- What survives a crash?

---

# The Timeless-Idea Matrix

| Idea | Primary weeks |
|---|---|
| Representation | 1, 40–43 |
| Abstraction | 4, 9–10, 52–55 |
| Computation | 2, 4 |
| Algorithms | 27–39, 42–43 |
| Data structures | 3, 28–34, 40–41 |
| Memory | 3, 5, 8, 69, 84–87 |
| Resource management | 3, 7, 8, 86 |
| Compilation | 2, 4, 84–87 |
| Runtime | 8, 11–12, 84–87 |
| Type systems | 9, 11, 86–87 |
| Concurrency | 13–16, 23, 71, 74 |
| Synchronization | 13–16, 23, 89 |
| OS | 5–7 |
| Networking | 17–20, 48, 50 |
| Persistence | 40–43 |
| Transactions | 23, 42, 57, 89 |
| Distribution | 44–51, 76–79, 88–91 |
| Fault tolerance | 20, 76–79, 101–102 |
| Performance | 17, 25, 35, 68–75, 93–94, 103 |
| Evolution | 52–63, 95, 104 |

---

# The Fundamental Learning Loop

For every new technology:

```text
                 NEW TECHNOLOGY
                       |
                       v
             What problem does it solve?
                       |
                       v
             What primitive enables it?
                       |
                       v
              What abstraction hides it?
                       |
                       v
               What does it cost?
                       |
                       v
               How can it fail?
                       |
                       v
                 How do I measure?
                       |
                       v
                Where is it useful?
                       |
                       v
              What alternative exists?
                       |
                       v
             What is the trade-off?
```

The objective of the 24 months is not to memorize more APIs.

It is to make this loop automatic.

---

# Final Competency Model

At the end of 24 months, evaluate yourself across five levels:

### Level 1 — Explain
Can explain the concept.

### Level 2 — Implement
Can build a simplified version.

### Level 3 — Debug
Can intentionally break it and diagnose the failure.

### Level 4 — Measure
Can benchmark/profile it and distinguish evidence from intuition.

### Level 5 — Transfer
Can recognize the same fundamental idea inside a different language, runtime, database, framework, or architecture.

**Target:** Level 5 for the 20 timeless ideas.

The ultimate goal is:

```text
CPU
 ↓
Machine
 ↓
Assembly
 ↓
C
 ↓
OS
 ↓
Runtime
 ↓
Java / JS / Go / Rust / Python
 ↓
React / Node / Spring
 ↓
PostgreSQL
 ↓
Distributed Systems
 ↓
Production Architecture
```

while being able to reason in the reverse direction:

```text
Production symptom
       ↓
Architecture
       ↓
Runtime
       ↓
OS
       ↓
Hardware/resource
       ↓
Fundamental principle
```

That reverse path is the core skill this roadmap is designed to build.
