# Survey Writing Framework

This document is the handoff scaffold for continuing the survey draft on efficient state management in parallel and distributed systems. The goal is to let multiple students extend the manuscript without turning it into a pile of disconnected paper summaries.

## Core Rule

Every added paper must be integrated through the same analytical frame:

1. What is the state object?
2. What control surface does the runtime expose over that state?
3. What coupling path makes that control decision matter system-wide?
4. What evaluation boundary does the paper actually optimize or bound?
5. What important systems gap still remains after this paper?

If a reading note cannot answer these five questions, it is not ready to enter the manuscript.

## Target Manuscript Shape

The paper should eventually stabilize around the following architecture:

1. Introduction
2. Scope and Survey Methodology
3. Unifying View of Stateful Computing Systems
4. Taxonomy of State Management Problems
5. State Access and Scheduling
6. State-Aware Execution Optimization
7. State Evolution and Reuse
8. Cross-Cutting Design Principles
9. Integrated Research Agenda
10. Evaluation Dimensions
11. Conclusion

The current draft already has this spine. Future work should deepen sections instead of inventing many new top-level sections.

## Preferred Expansion Units

Students should work in subsection-sized chunks. Good expansion units are:

- state migration, elasticity, and checkpointing
- transactional stream processing and dependency-aware scheduling
- LLM serving disaggregation and prefill/decode lifecycle control
- KV-cache reuse, reclamation, and admission policies
- retrieval-memory architectures and vector-index state management
- continual-learning memory budgets and retention control
- approximation and quality-bounded stateful execution

Each chunk should add both literature coverage and synthesis prose.

## Section Ownership Suggestions

Use one owner per subsection-sized cluster.

- Student A: stream processing, migration, elasticity, checkpointing
- Student B: hardware-conscious execution, approximation, compression
- Student C: LLM serving, KV cache, serving disaggregation, scheduling
- Student D: retrieval memory, vector indexes, RAG systems
- Student E: continual learning, memory retention, long-horizon reuse

One student can cover multiple clusters, but each cluster should have a clear owner at any given time.

## Required Output Per Paper

Before touching `main.tex`, create a short note for the paper in this format:

```text
Paper:
Area:
State object:
Control surface:
Coupling path:
Evaluation boundary:
Key empirical claim:
Limitations / open gap:
Where it belongs in main.tex:
BibTeX key:
```

Do not copy the abstract into the manuscript. Convert the note into 1-3 sentences of comparative survey prose.

## Required Output Per Subsection

Each expanded subsection should contain all of the following:

1. A short opening paragraph that defines the local control problem.
2. A synthesis paragraph that groups papers by mechanism, not by chronology alone.
3. A comparison paragraph that explains tradeoffs or boundary differences.
4. A closing paragraph on open systems gaps.

If a subsection only contains paper-by-paper summaries, it is incomplete.

## Writing Template For Comparative Paragraphs

Use this pattern when integrating papers:

```text
Paper/line X treats <state object> as a runtime-managed object and exposes <control surface>.
Paper/line Y extends or contrasts with it by changing <coupling path or evaluation boundary>.
Read together, these papers show that <higher-level systems lesson>.
The remaining gap is <missing control capability, portability limit, or evaluation weakness>.
```

## Citation Policy

- Add BibTeX entries to `refs.bib` first.
- Do not leave bibliography entries uncited unless they are part of a clearly planned next subsection.
- Prefer canonical conference or journal venues over raw arXiv when the final venue is known.
- Use arXiv only when no stable venue version is available yet.

## Editing Policy For `main.tex`

- Expand locally. Do not rewrite the whole manuscript in one pass.
- Preserve the three-axis structure: access, execution, evolution.
- When adding a new paragraph, attach it to one of the existing subsections whenever possible.
- Add a new subsection only if the local literature cluster has a distinct control problem that cannot be expressed cleanly inside the current subsection.

## Definition Of Done For A Student Task

A subsection task is complete only if:

1. At least 4-8 relevant papers were read and integrated.
2. New references were added to `refs.bib` if needed.
3. The subsection gained synthesis, not only enumeration.
4. `main.tex` compiles cleanly.
5. No undefined citation warnings remain.
6. The subsection now states at least one clear open systems gap.

## Immediate Backlog

The highest-value next expansions are:

1. serving disaggregation, prefill/decode separation, and state lifecycle control
2. vector-index systems as runtime state layers, including construction, compression, update, and lookup paths
3. checkpointing, migration, and elasticity as a unified operator-state control problem
4. stronger cross-cutting comparison tables across streaming, serving, and retrieval systems

## Suggested Next Artifact

If the team keeps growing, create a separate `LITERATURE_MATRIX.md` with one row per paper and the five analytical fields. That file can become the staging area before prose is added to the survey.