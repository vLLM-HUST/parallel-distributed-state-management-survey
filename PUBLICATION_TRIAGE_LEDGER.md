# Self-Publication Triage Ledger

This file records a paper-by-paper triage of the publication list in /home/shuhao/private-materials/张老师个人信息-发表文章目录.md using the survey's inclusion criteria.

## Decision Labels

- `core`: belongs in the analytical core of the survey because it makes state an explicit runtime object and exposes a reusable control surface.
- `context`: useful boundary-setting or supporting context, but should not carry the main analytical load of the survey.
- `exclude`: should stay out of the survey prose because state is incidental, the paper is mainly an application result, or the artifact is superseded by a stronger version.

## Ledger

| No. | Paper | Decision | Rationale | Handling |
| --- | --- | --- | --- | --- |
| 1 | Scalable Transactional Stream Processing on Multicore Processors | core | Journal MorphStream extension; explicit dependency state, nondeterministic access, and multiversioned window control. | Keep as canonical transactional-stream extension. |
| 2 | Spacker: Unified State Migration for Distributed Streaming | core | State migration is the control surface; evaluates completion time, latency spike, and overhead tradeoffs. | Keep in access/governance line. |
| 3 | Fast Parallel Recovery for Transactional Stream Processing on Multicores | core | Recovery metadata and replay scheduling are explicit runtime state mechanisms. | Keep in recovery coupling line. |
| 4 | MorphStream: Scalable Processing of Transactions over Streams | exclude | Demo paper; showcases system and UI rather than adding a new systems mechanism. | Do not use in survey prose. |
| 5 | A Survey on Transactional Stream Processing | context | Survey paper, useful for positioning and related-survey contrast, not primary evidence. | Keep only as survey-context citation. |
| 6 | Scalable Online Interval Join on Modern Multicore Processors in OpenMLDB | core | Shared interval indexes, ordering constraints, and concurrency control are first-class runtime concerns. | Keep in access/locality subsection. |
| 7 | MorphStream: Adaptive Scheduling for Scalable Transactional Stream Processing on Multicores | core | Core SIGMOD MorphStream paper; explicit adaptive scheduling over transactional dependency state. | Keep in transactional-stream core. |
| 8 | Parallelizing Intra-Window Join on Multicores: An Experimental Study | core | Carefully decomposes join design space into execution style, join method, and partitioning under multicore state pressure. | Keep in access-cost design-space comparison. |
| 9 | Towards Concurrent Stateful Stream Processing on Multicore Processors | core | TStream makes concurrent state access and scheduling the main systems abstraction. | Keep in access/control evolution line. |
| 10 | BriskStream: Scaling Data Stream Processing on Shared-Memory Multicore Architectures | core | NUMA-local operator placement and shared-memory locality explicitly govern state access cost. | Keep in locality/topology line. |
| 11 | Multi-Query Optimization for Complex Event Processing in SAP ESP | core | Shared subplans and execution-path restructuring expose state sharing as a control problem. | Keep in early access-observability line. |
| 12 | Revisiting the Design of Data Stream Processing Systems on Multi-Core Processors | core | Identifies hidden contention and NUMA effects in stateful stream execution. | Keep in observability/locality framing. |
| 13 | Data-Aware Adaptive Compression for Stream Processing | core | Journal extension of compressed stream processing with explicit format-selection control and end-to-end boundaries. | Keep as preferred journal form of adaptive compression line. |
| 14 | Enabling Adaptive Sampling for Intra-Window Join | core | Sampling policy is exposed as runtime control over quantity-quality-cost tradeoffs for stateful joins. | Keep in approximation-aware execution. |
| 15 | MAST: Towards Efficient Analytical Query Processing on Point Cloud Data | exclude | Approximate query processing exists, but the main abstraction is application-specific point-cloud analytics rather than reusable state-management control. | Do not integrate into main survey. |
| 16 | LibAMM: Empirical Insights into Approximate Computing for Accelerating Matrix Multiplication | core | Explicitly studies approximation strategy selection under memory and accuracy tradeoffs. | Keep in quality-boundary section. |
| 17 | PECJ: Stream Window Join on Disorder Data Streams with Proactive Error Compensation | core | Compensation state and low-latency accuracy boundary are central runtime objects. | Keep in approximation/control line. |
| 18 | CStream: Parallel Data Stream Compression on Multicore Edge Devices | core | Compression dictionaries and scheduling across heterogeneous cores are explicit managed state. | Keep as preferred journal form of CStream line. |
| 19 | Predictive and Near-Optimal Sampling for View Materialization in Video Databases | core | Predictive materialization treats sample views and utility state as managed online assets. | Keep in approximation/materialization comparison. |
| 20 | A Hardware-Conscious Stateful Stream Compression Framework for IoT Applications (Vision) | context | Vision paper clarifies motivation, but not a stable evaluated mechanism. | Use only if historical setup is needed. |
| 21 | Parallelizing Stream Compression for IoT Applications on Asymmetric Multicores | core | Explicit task decomposition and asymmetry-aware scheduling over compression state. | Keep as conference anchor for CStream line. |
| 22 | CompressStreamDB: Fine-Grained Adaptive Stream Processing without Decompression | core | Representation and operator path are explicit runtime controls over compressed state. | Keep in execution-state path line. |
| 23 | Fine-Grained Multi-Query Stream Processing on Integrated Architectures | core | Preferred journal version of FineStream; device mapping and query sharing are explicit control surfaces. | Prefer when normalizing FineStream references later. |
| 24 | FineStream: Fine-Grained Window-Based Stream Processing on CPU-GPU Integrated Architectures | context | Earlier conference version of the FineStream line, largely superseded by the TPDS journal paper. | Keep only if venue history matters. |
| 25 | Hardware-Conscious Stream Processing: A Survey | context | Survey paper is useful for positioning, not analytical-core evidence. | Keep as related-survey context only. |
| 26 | FlowRAG: Continual Learning for Dynamic Retriever in Retrieval-Augmented Generation | core | Dynamic retriever adaptation under evolving corpora makes memory evolution a runtime control problem. | Keep in retrieval-memory core. |
| 27 | StreamFP: Fingerprint-guided Data Selection for Efficient Stream Learning | core | Buffer admission and retention become explicit state-selection controls. | Keep in retention-governance line. |
| 28 | CANDOR-Bench: Benchmarking In-Memory Continuous ANNS under Dynamic Open-World Streams | core | Turns dynamic ANN maintenance, churn, and freshness into first-class evaluation/control surfaces. | Keep in retrieval-index maintenance line. |
| 29 | A Framework of Knowledge Graph-Enhanced Large Language Model Based on Global Planning | core | Planner-visible question decomposition and retrieval order create explicit runtime controls over structured memory. | Keep in structured-memory line, especially for planner control. |
| 30 | Scalable Machine Learning for Real-Time Fault Diagnosis in Industrial IoT Cooling Roller Systems | context | Adaptive updates and coreset ideas are present, but the paper is primarily an industrial application system. | Mention only if application boundary examples are needed. |
| 31 | Ferret: An Efficient Online Continual Learning Framework under Varying Memory Constraints | core | Budget-aware retention, pipeline planning, and memory elasticity are central runtime mechanisms. | Keep in retention-governance core. |
| 32 | A Framework of Knowledge Graph-Enhanced Large Language Model Based on Question Decomposition and Atomic Retrieval | core | Atomic retrieval and decomposition expose structured memory traversal as a control problem. | Keep alongside the journal extension. |
| 33 | MOStream: A Modular and Self-Optimizing Data Stream Clustering Algorithm | core | Summarization, windowing, refinement, and outlier control are explicit adaptive dimensions. | Keep in evolution/update section. |
| 34 | SentiStream: A Co-Training Framework for Adaptive Online Sentiment Analysis in Evolving Data Streams | core | Stream adaptation is treated as a continuous state-update loop rather than offline retraining. | Keep in evolution/update section. |
| 35 | Data Stream Clustering: An In-depth Empirical Study | core | Decomposes the DSC design space into reusable maintenance dimensions with explicit accuracy-efficiency tradeoffs. | Keep as empirical basis for MOStream-style modularization. |
| 36 | Multi-Hop Knowledge Editing via Critic-Guided Multi-Agent Reasoning | exclude | Based on current repository summary, the paper is reasoning/editing centric and does not expose a reusable runtime state-management surface. | Keep out unless later materials reveal explicit memory-governance mechanisms. |
| 37 | FusionFlow: Enabling Deep Structural Exploration for Automated Agentic Workflow Generation | exclude | Available summary and web snippets emphasize workflow generation and optimization, not managed runtime state as the primary object. | Keep out of current survey scope. |
| 38 | GRACE: Alleviating Reconstruction Cost in Dynamic Graph Processing Systems | context | Strong dynamic-layout maintenance paper, but graph-update systems are not yet a main analytical cluster in the survey. | Use as broader-systems context only. |
| 39 | Select Edges Wisely: Monotonic Path Aware Graph Layout Optimization for Disk-Based ANN Search | core | Disk-based ANN graph layout is treated as a control surface over future traversal locality and maintenance cost. | Keep in vector-index state layer section. |
| 40 | Detecting Hallucination in Large Language Models through Deep Internal Representation Analysis | exclude | Main contribution is model-side detection accuracy, not runtime memory, scheduling, or maintenance control. | Do not integrate into survey. |
| 41 | MatSwarm: Trusted Swarm Transfer Learning Driven Materials Computation for Secure Big Data Sharing | exclude | Collaborative learning and security are central; state-management control is not the organizing abstraction here. | Keep out of survey. |
| 42 | PREACT: Predictive Resource Allocation for Bursty Workloads in a Co-located Data Center | exclude | Resource prediction is important systems work, but the managed object is service workload allocation rather than shared, evolving application state. | Keep out of current survey scope. |
| 43 | Low-Latency Video Conferencing via Optimized Packet Routing and Reordering | exclude | Focuses on routing and jitter control, not state management as defined in the survey. | Exclude. |
| 44 | Payment Behavior Prediction on Shared Parking Lots with TR-GCN | exclude | Application-centric prediction system; state is incidental rather than the main runtime control surface. | Exclude. |
| 45 | Revisiting the Design of Parallel Stream Joins on Trusted Execution Environments | context | Join design-space and scheduling issues are relevant, but the main framing is TEE/security-specific rather than a central survey cluster. | Keep as optional side context only. |
| 46 | Periodic Weather-Aware LSTM with Event Mechanism for Parking Behavior Prediction | exclude | Application-centric temporal modeling, not runtime state governance. | Exclude. |
| 47 | NebulaStream: Complex Analytics Beyond the Cloud | context | Strong edge-to-cloud state-management vision, but mainly a broad systems/vision bridge rather than core comparative evidence. | Keep in broader literature context only. |
| 48 | PewLSTM: Periodic LSTM with Weather-Aware Gating Mechanism for Parking Behavior Prediction | exclude | Same reason as later parking papers: application-centric modeling rather than runtime state control. | Exclude. |
| 49 | TraV: An Interactive Exploration System for Massive Trajectory Data | exclude | Interactive system and progressive execution are interesting, but not centered on reusable state-management mechanisms. | Exclude. |
| 50 | Understanding Co-Running Behaviors on Integrated CPU/GPU Architectures | core | Hardware sharing and memory-behavior analysis contribute to state-path execution reasoning on integrated architectures. | Keep as hardware-conscious supporting core. |
| 51 | Elastic Multi-resource Fairness: Balancing Fairness and Efficiency in Coupled CPU/GPU Architectures | context | Relevant to heterogeneous resource allocation, but state itself is not the primary managed runtime object. | Keep only as supporting hardware context. |
| 52 | Melia: A MapReduce Framework on OpenCL-Based FPGAs | exclude | Parallel framework and energy optimization are central, not shared evolving state management. | Exclude. |
| 53 | To Co-run, or Not to Co-run: A Performance Study on Integrated Architectures | context | Early workshop precursor to the stronger TPDS co-running paper. | Use only as historical predecessor if needed. |
| 54 | In-Cache Query Co-Processing on Coupled CPU/GPU Architectures | context | Useful hardware-conscious memory-path result, but not a central state-management paper in the survey's current framing. | Keep as optional support only. |
| 55 | OmniDB: Towards Portable and Efficient Query Processing on Parallel CPU/GPU Architectures | exclude | Demo/portability artifact rather than a substantive state-management mechanism paper. | Exclude. |
| 56 | Neuromem: A Granular Decomposition of the Streaming Lifecycle in External Memory for LLMs | core | Explicitly decomposes external-memory lifecycle and benchmarks insertion/retrieval evolution under streaming settings. | Keep in structured memory and middleware line. |
| 57 | SAGE: A Dataflow-Native Framework for Modular, Controllable, and Transparent LLM-Augmented Reasoning | core | Exposes pluggable index, async update, window, and join services as modular reasoning-state middleware. | Keep in structured memory and middleware line. |

## Immediate Takeaways

1. The analytical core remains concentrated in four coherent clusters: stateful streaming and migration, hardware-conscious/approximate execution, retrieval-memory and vector-index governance, and continual retention or memory middleware.
2. Many collaborative AI and application papers are not missing from the survey by accident; they fail the current inclusion rule because they optimize model behavior or an application task without making runtime state control the main systems abstraction.
3. The most defensible next additions beyond the current manuscript are not more application papers, but tighter comparative prose around Neuromem, SAGE, FlowRAG, CANDOR-Bench, and the stream-join or clustering design-space papers.