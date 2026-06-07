# Open Research Problems: Experimentally-Verifiable Questions

This document distills the open research gaps identified in the survey into concrete, experimentally-verifiable problems. Each problem is mapped to the survey section where it appears, the hypothesis to test, and the experimental infrastructure required (primarily vllm-hust and related systems).

The goal: use vllm-hust benchmark runs to provide empirical evidence that strengthens the survey's claims about state-management gaps.

---

## 1. KV Cache Lifecycle Governance Gap

**Survey reference:** Section 4.2 (KV-cache lifecycle governance), Figure 7

**Core claim:** No single system governs all five KV lifecycle stages (admit, place, mutate, transfer, reclaim) against the same TTFT/TPOT/SLO boundary. Current systems optimize one or two stages while externalizing debt to others.

### Experimental questions

- **Q1.1:** Under mixed prompt-length workloads, does an admission controller that is unaware of downstream transfer cost cause worse p99 TPOT than one that jointly reasons about admission + placement?
- **Q1.2:** How much hidden "transfer debt" does prefill/decode disaggregation create? Measure KV transfer latency as a fraction of end-to-end TTFT under varying sequence lengths.
- **Q1.3:** At what occupancy threshold does reactive eviction (PagedAttention-style) begin to hurt tail latency compared to anticipatory admission throttling?

### Required infrastructure
- vllm-hust with instrumented KV allocator (admission/eviction/transfer event logging)
- Mixed-length prompt traces (ShareGPT, synthetic burst generators)
- p99 TTFT/TPOT/goodput measurement under sustained load

---

## 2. Multi-Tenant Serving Under Burst Arrival

**Survey reference:** Section 7.3.1 (Multi-Tenant LLM Serving Under Burst Arrival)

**Core claim:** Burst robustness depends on coherent lifecycle governance over short-lived serving state rather than on any single optimization knob. The literature still lacks a control contract that can rank admission, offload, restoration, and tenant-isolation actions against the same service boundary.

### Experimental questions

- **Q2.1:** Under bursty multi-tenant traffic (mixed LoRA adapters), how much does adapter residency churn degrade throughput compared to a warmth-aware eviction policy?
- **Q2.2:** Does priority-aware admission (rejecting low-priority requests early) yield better SLO attainment than best-effort batching under burst?
- **Q2.3:** What is the interference cost when two tenants share KV memory pools vs. when they are isolated? Quantify in terms of p99 latency inflation.

### Required infrastructure
- vllm-hust with multi-LoRA serving support
- Burst traffic generators with configurable arrival patterns (Poisson bursts, flash crowds)
- Per-tenant latency tracking and SLO violation counters

---

## 3. Prefill/Decode Phase Disaggregation Cost

**Survey reference:** Section 4.2 (Predictive serving, structural-reuse, temporal-lifecycle families)

**Core claim:** Phase disaggregation (DistServe, Splitwise, PrFaaS-style) moves the bottleneck from compute asymmetry to transfer and restoration. The remaining gap is uncertainty composition: practical runtimes still lack a portable rule for reconciling wrong or conflicting predictions about load, memory, and placement.

### Experimental questions

- **Q3.1:** What is the cross-over point where disaggregation overhead (KV serialization + network transfer) exceeds the latency benefit of phase specialization? Parameterize by sequence length, batch size, and network bandwidth.
- **Q3.2:** When prefill-length predictions are wrong (±30% error), how much does that degrade goodput compared to a reactive baseline?
- **Q3.3:** Under phase-imbalance spike (sudden prefill-heavy burst followed by decode-heavy tail), does anticipatory phase balancing recover faster than reactive load shedding?

### Required infrastructure
- vllm-hust with disaggregated prefill/decode mode (or simulated via profiling)
- Controllable network latency injection between prefill and decode workers
- Workload traces with non-stationary phase mix

---

## 4. Disturbance-Oriented Evaluation Protocol

**Survey reference:** Section 8.1 (Evaluation Dimensions), Figure 12 (Disturbance-oriented evaluation protocol)

**Core claim:** One-shot benchmarking of non-stationary mechanisms is a recurring anti-pattern. Evaluation should cover warmup → burst → reconfiguration → drift → long-horizon maintenance as one connected experiment.

### Experimental questions

- **Q4.1:** Take a well-known result (e.g., prefix caching improves TTFT by X%). Does that gain survive a 5-phase disturbance protocol (warmup, burst, cache flush, drift to new distribution, re-stabilization)?
- **Q4.2:** How quickly does the system re-stabilize after a cache-invalidation event (simulating reconfiguration)? Measure time-to-recovery of steady-state throughput.
- **Q4.3:** Under sustained workload drift (gradual shift from short prompts to long prompts over 30 minutes), how much does amortized goodput degrade compared to the one-shot optimum?

### Required infrastructure
- vllm-hust benchmark harness extended with multi-phase workload scripts
- Workload generators with controllable distribution drift
- Time-series telemetry (per-second TTFT/TPOT/throughput/memory)

---

## 5. Policy Layering Conflict Demonstration

**Survey reference:** Section 7.2.2 (Policy Layering Without Conflict Semantics)

**Core claim:** Adding contention mitigation + migration heuristics + quality guards without explicit precedence causes oscillation. The stack of policies may fight each other under skew or failure.

### Experimental questions

- **Q5.1:** Enable batching optimization + prefix caching + continuous batching admission control simultaneously. Under what workload conditions do they conflict (e.g., prefix caching wants to keep old KV, admission control wants to evict to make room)?
- **Q5.2:** Can we demonstrate measurable oscillation (latency variance increase) when two independent policies (e.g., preemption + dynamic batching) operate without coordination?
- **Q5.3:** Does adding a simple priority ordering between policies (hard constraint → soft objective → tie-breaker) reduce tail latency variance under the same workload?

### Required infrastructure
- vllm-hust with independently toggleable policy modules
- Latency variance and throughput jitter metrics
- Adversarial workload traces designed to trigger policy conflicts

---

## 6. State-Centric Scheduling on Heterogeneous Hardware

**Survey reference:** Section 8.2.2 (State-Centric Scheduling on Heterogeneous Hardware)

**Core claim:** Scheduling should be formulated over state-object lifecycles rather than isolated requests. The unresolved requirement is a scheduler that can jointly reason about who touches state, where it should reside, how expensive it is to move, and whether mutation is occurring concurrently.

### Experimental questions

- **Q6.1:** On a heterogeneous NPU/GPU setup (Ascend + NVIDIA, or multi-tier memory), does state-aware placement (KV on fast memory, adapter weights on slower tier) outperform uniform placement under memory pressure?
- **Q6.2:** How much does cross-device KV migration cost compared to recomputation? At what sequence length does migration become cheaper?
- **Q6.3:** Under mixed workloads (some requests need long KV context, others are short), does state-locality-aware routing improve p99 latency compared to round-robin?

### Required infrastructure
- vllm-ascend-hust with multi-device topology awareness
- Memory tier profiling (HBM vs DDR vs NVMe offload)
- Request routing instrumentation

---

## 7. Write Amplification in Paged KV Management

**Survey reference:** Section 7.2.4 (Ignoring Write Amplification in "Read-Optimized" Designs)

**Core claim:** Paging, disaggregation, transfer compression, and restoration scheduling can improve TTFT or goodput, but create write-path or movement debt (KV transfer, restoration pressure, reclamation complexity). A mechanism is not efficient if it externalizes cost into deferred compaction.

### Experimental questions

- **Q7.1:** Under sustained serving load with prefix caching, measure the ratio of useful KV computation vs. total KV data movement (writes to/from swap, transfers between workers). How does this "write amplification" scale with sequence length?
- **Q7.2:** Does KV compression (quantized KV cache) reduce write amplification proportionally, or does decompression overhead shift the bottleneck?
- **Q7.3:** Under what conditions does "speculative" KV retention (keeping evicted KV in slower storage for potential reuse) pay off vs. recomputation?

### Required infrastructure
- vllm-hust with KV data movement accounting (bytes read/written/transferred per request)
- Swap/offload instrumentation
- Workload traces with varying reuse probability

---

## 8. Closed-Loop vs. Open-Loop Admission Control

**Survey reference:** Section 7.1.4 (Closed-Loop Rather Than Open-Loop Policies)

**Core claim:** Open-loop policies should be read as local approximations. A sampling rule, compression level, or eviction heuristic may work well inside one disturbance regime, yet fail once another controller changes the workload shape.

### Experimental questions

- **Q8.1:** Compare static admission thresholds vs. feedback-driven admission (adjusting based on observed queue depth + memory pressure). Under what burst intensity does the feedback loop become necessary?
- **Q8.2:** How much latency overshoot occurs when a static policy encounters a regime change (e.g., sudden shift from short to long prompts) before manual retuning?
- **Q8.3:** Can simple closed-loop heuristics (e.g., "reduce admission rate when p99 exceeds 2x target for >5s") match more complex learned controllers in practice?

### Required infrastructure
- vllm-hust with configurable admission policies
- Workload regime-shift scenarios
- Real-time telemetry feedback to admission controller

---

## Priority and Connection to vllm-hust Roadmap

| Problem | Difficulty | Data Impact on Survey | vllm-hust Feature Required |
|---------|-----------|----------------------|---------------------------|
| Q1 (KV lifecycle) | Medium | High — validates central Figure 7 | KV allocator instrumentation |
| Q2 (Multi-tenant burst) | Medium | High — validates case study §7.3.1 | Multi-LoRA + burst traffic |
| Q3 (Disaggregation cost) | High | High — validates §4.2 predictive family | Disaggregated mode |
| Q4 (Disturbance eval) | Low | Very High — validates §8.1 methodology | Multi-phase benchmark scripts |
| Q5 (Policy conflict) | Medium | Medium — validates §7.2.2 anti-pattern | Toggleable policy modules |
| Q6 (Heterogeneous sched) | High | Medium — validates §8.2.2 agenda | Multi-device support |
| Q7 (Write amplification) | Low | Medium — validates §7.2.4 anti-pattern | Data movement accounting |
| Q8 (Closed-loop admission) | Medium | Medium — validates §7.1.4 principle | Configurable admission |

**Recommended execution order:** Q4 → Q1 → Q2 → Q7 → Q8 → Q3 → Q5 → Q6

Q4 (disturbance evaluation protocol) is the highest-leverage first step because it defines the benchmarking methodology that all subsequent experiments should follow.

---

## How to Use These Results in the Survey

Each experimental result should be integrated as:
1. A **concrete evidence paragraph** in the corresponding survey section
2. An entry in a **new empirical validation table** (to be added)
3. Possibly a **figure** showing the multi-phase behavior or cross-over points

The goal is not to turn the survey into a systems paper, but to provide empirical grounding for claims that are currently synthesized only from existing literature.
