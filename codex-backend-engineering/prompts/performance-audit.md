# Prompt — Backend Performance Investigation

Act as a performance engineer investigating [endpoint/service/workload]. Do not optimize by intuition alone. Establish evidence and a baseline first.

## Workload and goals

- Target: [endpoint, job, query, service]
- Expected workload: [RPS, concurrency, payload sizes, data volume]
- Current symptoms: [latency, CPU, memory, DB load, throughput]
- Target: [p50/p95/p99, throughput, resource budget]
- Environment: [local/staging/production-like; never run disruptive tests in production without approval]

## Procedure

### 1. Understand the path
Trace request handling, serialization, database queries, cache calls, external dependencies, queues, and background work. Identify synchronous/blocking operations and resource lifetimes.

### 2. Establish a baseline
Use existing metrics, traces, query plans, logs, or a reproducible benchmark. Record environment, dataset, concurrency, duration, warm-up, and measurement method. If no baseline is available, state that limitation.

### 3. Identify bottlenecks
Evaluate only relevant areas:
- Query count, query plans, missing/ineffective indexes, N+1 patterns.
- Connection pool saturation and lock contention.
- Network round trips and external service latency.
- Serialization, compression, and payload size.
- CPU-heavy work and blocking I/O.
- Memory growth, allocation pressure, and leaks.
- Cache hit rate, invalidation, staleness, and stampedes.
- Queue depth, backpressure, and unbounded concurrency.

### 4. Propose options
For each option, estimate expected impact, complexity, risk, consistency implications, and how to measure success. Prefer the smallest high-confidence change.

### 5. Implement only when requested
Keep optimization focused. Preserve semantics, authorization, and error handling. Avoid adding a cache, worker pool, or concurrency layer without a clear need.

### 6. Verify
Repeat the same workload and compare baseline with after-change results. Include measurement variance and limitations. Run regression tests to confirm behavior.

## Output

- Baseline and measurement method.
- Bottleneck evidence (paths, query plans, traces, or metrics).
- Ranked recommendations.
- Changes made, if authorized.
- Before/after results with units and workload.
- Correctness, consistency, and operational trade-offs.
- Remaining bottlenecks and unverified hypotheses.

Never invent benchmark numbers or claim an improvement without comparable measurements.
