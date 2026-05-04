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
| crankshaw2017clipper | serving orchestration | model/request serving state | ensemble selection and prediction serving control | latency/SLO tradeoff under online serving | latency + accuracy + availability | reusable memory lifecycle still implicit | State-Aware Execution Optimization / KV-Cache Management | TBD | integrated |
| gujarati2020clockwork | predictable serving | schedule and execution-time state | predictability-driven dispatch and isolation | interference and latency uncertainty | tail latency/SLO isolation | memory reuse surfaces underdeveloped | State-Aware Execution Optimization / KV-Cache Management | TBD | integrated |
| yu2022orca | LLM serving | partially materialized decode state | iteration-level scheduling and selective batching | head-of-line blocking and batch inefficiency | throughput + tail latency | memory lifecycle remains implicit | State-Aware Execution Optimization / KV-Cache Management | TBD | integrated |
| crankshaw2020inferline | serving control plane | pipeline queues and provisioning state | provisioning and autoscaling control | workload forecasting and SLO drift | cost/SLO frontier | finer-grained memory-state observability | State-Aware Execution Optimization / KV-Cache Management | TBD | integrated |
| shen2019nexus | cluster serving | GPU occupancy and pipeline queue state | cluster-level scheduling and batching | GPU contention and stage imbalance | throughput/latency in pipelines | generative serving memory lifecycle not explicit | State-Aware Execution Optimization / KV-Cache Management | TBD | integrated |
| romero2021infaas | serving automation | replica and model-placement state | autoscaling and model-less serving control | workload shifts and heterogeneous replica cost | latency/cost under dynamic demand | weaker coupling to reusable memory objects | State-Aware Execution Optimization / KV-Cache Management | TBD | integrated |
| sheng2023flexgen | memory-constrained serving | offloaded model and KV state | tiered offload and placement control | single-GPU memory pressure and transfer overhead | throughput under memory limits | weaker cluster-scale lifecycle control | State-Aware Execution Optimization / KV-Cache Management | TBD | integrated |
| zhong2024distserve | serving disaggregation | separated prefill/decode state paths | phase disaggregation scheduling | cross-stage queueing and transfer cost | goodput/tail latency | cluster-level admission control | State-Aware Execution Optimization / KV-Cache Management | TBD | integrated |
| patel2024splitwise | serving disaggregation | split prefill/decode state lifecycle | phase splitting and placement | phase imbalance and resource contention | throughput-latency | generalized policy tuning | State-Aware Execution Optimization / KV-Cache Management | TBD | integrated |
| holmes2024fastgen | LLM serving | fused/split prompt-generation working set | dynamic phase fusion and split policy | long-prompt pressure and queue imbalance | average + tail latency | cluster-scale transfer governance | State-Aware Execution Optimization / KV-Cache Management | TBD | integrated |
| chen2024punica | multi-tenant serving | adapter and tenant-specific serving state | adapter-aware batching and memory sharing | tenant interference and state multiplexing | throughput + isolation | broader lifecycle interaction with KV memory | State-Aware Execution Optimization / KV-Cache Management | TBD | integrated |
| li2023alpaserve | model-parallel serving | partitioned model state and multiplexing metadata | statistical multiplexing with model parallelism | interference across tenants and partitions | throughput/cost frontier | lifecycle interaction with KV and adapter state | State-Aware Execution Optimization / KV-Cache Management | TBD | integrated |
| zheng2023sglang | LLM serving | reusable prefix KV and decoding state | radix reuse and structured decoding control | program structure and reuse boundary | throughput under complex programs | generality under mixed workloads | State-Aware Execution Optimization / KV-Cache Management | TBD | integrated |
| fernandez2013osm | stream elasticity | operator state shards | unified scale-out/fault-tolerance transfer | migration and recovery interaction | elasticity + fault handling cost | stronger online observability | State Access and Scheduling / Runtime Control | TBD | integrated |
| nasir2019megaphone | stream migration | keyed operator state | fine-grained state migration | migration latency and locality | latency under reconfiguration | broader fault coupling | State Access and Scheduling / Runtime Control | TBD | integrated |
| mao2025spacker | stream migration | movable distributed state shards | unified redistribution substrate | transfer reuse across scaling and placement | migration overhead + stability | explicit ownership semantics | State Access and Scheduling / Runtime Control | TBD | integrated |
| zhao2024recovery | transactional stream processing | recovery metadata and replay state | recovery-integrated scheduling | replay pressure and steady-state interference | recovery time + steady-state overhead | unified ownership and migration control | State Access and Scheduling / Runtime Control | TBD | integrated |
| carbone2015asynchronous | stream checkpointing | checkpoint snapshots and in-flight state | asynchronous barrier-aligned checkpointing | checkpoint delay and recovery coupling | runtime overhead + fault tolerance | explicit ownership-transfer composition | State Access and Scheduling / Runtime Control | TBD | integrated |
| karpukhin2020dpr | retrieval memory | dense passage vector index | retriever encoding and ANN lookup | retrieval quality vs index maintenance | top-k retrieval quality and E2E QA | update cadence under drift | State Evolution and Reuse / Structured Memory | TBD | integrated |
| khattab2020colbert | retrieval memory | token-level late-interaction index | offline encoding + online late interaction | quality-cost tradeoff in retrieval path | effectiveness with lower FLOPs | memory footprint and update overhead | State Evolution and Reuse / Structured Memory | TBD | integrated |
| wang2024hipporag | retrieval memory | KG + graph memory substrate | graph-based retrieval orchestration | long-term memory structure and drift | quality-cost-latency | dynamic maintenance policies | State Evolution and Reuse / Structured Memory | TBD | integrated |

## Backlog Rows To Fill Next

| Bib key | Area | State object | Control surface | Coupling path | Evaluation boundary | Remaining gap | Target subsection in main.tex | Owner | Status |
|---|---|---|---|---|---|---|---|---|---|

