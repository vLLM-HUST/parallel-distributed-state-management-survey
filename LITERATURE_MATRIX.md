# Literature Matrix

This file is the staging area before writing into [main.tex](main.tex). Each row should map one paper to the survey scaffold.

## How To Use

1. Add one row per paper.
2. Fill all columns before editing prose.
3. Group rows by target section/subsection.
4. Mark `Status` as `ready` only when the row can be converted into synthesis text.

## Status Values

- `todo`: paper selected but not read
- `reading`: paper being read
- `note-ready`: scaffold fields filled
- `ready`: can be integrated into manuscript prose
- `integrated`: already integrated into manuscript

## Matrix

| Bib key | Area | State object | Control surface | Coupling path | Evaluation boundary | Remaining gap | Target subsection in main.tex | Owner | Status |
|---|---|---|---|---|---|---|---|---|---|
| kwon2023pagedattention | LLM serving | per-request KV pages | paging/allocation/sharing | fragmentation and batch-size coupling | throughput at latency target | cross-node lifecycle control | State-Aware Execution Optimization / KV-Cache Management | TBD | integrated |
| agrawal2024sarathi | LLM serving | prefill/decode working set | phase-aware scheduling | phase asymmetry and queueing | throughput-latency tradeoff | portability across workloads | State-Aware Execution Optimization / KV-Cache Management | TBD | integrated |
| zheng2023sglang | LLM serving | reusable prefix KV and decoding state | radix reuse and structured decoding control | program structure and reuse boundary | throughput under complex programs | generality under mixed workloads | State-Aware Execution Optimization / KV-Cache Management | TBD | integrated |
| fernandez2013osm | stream elasticity | operator state shards | unified scale-out/fault-tolerance transfer | migration and recovery interaction | elasticity + fault handling cost | stronger online observability | State Access and Scheduling / Runtime Control | TBD | integrated |
| karpukhin2020dpr | retrieval memory | dense passage vector index | retriever encoding and ANN lookup | retrieval quality vs index maintenance | top-k retrieval quality and E2E QA | update cadence under drift | State Evolution and Reuse / Structured Memory | TBD | integrated |
| khattab2020colbert | retrieval memory | token-level late-interaction index | offline encoding + online late interaction | quality-cost tradeoff in retrieval path | effectiveness with lower FLOPs | memory footprint and update overhead | State Evolution and Reuse / Structured Memory | TBD | integrated |
| wang2024hipporag | retrieval memory | KG + graph memory substrate | graph-based retrieval orchestration | long-term memory structure and drift | quality-cost-latency | dynamic maintenance policies | State Evolution and Reuse / Structured Memory | TBD | integrated |

## Backlog Rows To Fill Next

| Bib key | Area | State object | Control surface | Coupling path | Evaluation boundary | Remaining gap | Target subsection in main.tex | Owner | Status |
|---|---|---|---|---|---|---|---|---|---|
| zhong2024distserve | serving disaggregation | separated prefill/decode state paths | phase disaggregation scheduling | cross-stage queueing and transfer cost | goodput/tail latency | cluster-level admission control | State-Aware Execution Optimization / KV-Cache Management | TBD | note-ready |
| patel2024splitwise | serving disaggregation | split prefill/decode state lifecycle | phase splitting and placement | phase imbalance and resource contention | throughput-latency | generalized policy tuning | State-Aware Execution Optimization / KV-Cache Management | TBD | note-ready |
| nasir2019megaphone | stream migration | keyed operator state | fine-grained state migration | migration latency and locality | latency under reconfiguration | broader fault coupling | State Access and Scheduling / Runtime Control | TBD | note-ready |

