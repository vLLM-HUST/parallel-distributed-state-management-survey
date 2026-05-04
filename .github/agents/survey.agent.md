# Parallel Distributed State Management Survey Agent Notes

## Repository Role

- This repository is a long-form survey manuscript workspace, not an implementation repo.
- The primary artifact is the survey in `main.tex`, supported by `refs.bib`, `LITERATURE_MATRIX.md`, `HANDOFF.md`, and `WRITING_FRAMEWORK.md`.
- The expected output is synthesis prose with a clear systems abstraction, not a bibliography dump or paper-by-paper summary list.

## First Reads

Before editing, read these files in order:

1. `README.md`
2. `HANDOFF.md`
3. `WRITING_FRAMEWORK.md`
4. `LITERATURE_MATRIX.md`
5. `main.tex`

The goal of this first pass is to identify one subsection-sized literature cluster to deepen, not to remap the entire manuscript.

## Core Working Contract

Every paper integrated into the manuscript should be understood through the same scaffold:

1. What is the state object?
2. What control surface does the runtime expose?
3. What coupling path makes that control matter system-wide?
4. What evaluation boundary does the paper optimize or bound?
5. What systems gap remains open?

If these five fields are not clear, the paper is not ready for prose integration.

## Default Workflow

When asked to continue the survey, prefer this sequence:

1. Pick one cluster-sized unit, such as serving disaggregation, stream migration and checkpointing, retrieval index evolution, or continual-retention control.
2. Update `LITERATURE_MATRIX.md` before writing new synthesis into `main.tex`.
3. Add or correct BibTeX entries in `refs.bib` before citing them in prose.
4. Expand the existing subsection locally instead of rewriting top-level structure.
5. Compile the manuscript and verify there are no undefined citation warnings.

## Writing Rules

- Preserve the three-axis organization: access and scheduling, execution optimization, evolution and reuse.
- Group papers by mechanism and control problem, not by chronology alone.
- Each expanded subsection should contain: local problem framing, mechanism synthesis, comparison/tradeoff discussion, and an explicit open gap.
- Favor cross-paper comparison sentences over serial summary sentences.
- Treat strong tables and matrices as support for prose, not as the final deliverable.

## Editing Constraints

- Do not do broad structural rewrites unless the current taxonomy clearly fails to host a literature cluster.
- Do not insert large numbers of references without adding synthesis.
- Do not let the manuscript collapse into an author-centric work list.
- Prefer canonical venue versions over arXiv when the stable venue is known.
- Leave uncited references only when they are clearly staged for the next subsection.

## Definition Of Done

A survey-editing task is complete only when:

1. The targeted subsection gained real synthesis, not just extra citations.
2. `LITERATURE_MATRIX.md` reflects the integrated papers.
3. `refs.bib` is consistent with the new discussion.
4. `main.tex` compiles cleanly.
5. The new text ends with at least one explicit open systems gap or design implication.

## Build Command

Use the repository's documented build path:

`TEXINPUTS=third_party/acmart-src//: /home/shuhao/miniconda3/envs/vllm-hust-dev/bin/tectonic main.tex`

## Non-Goals

- This repo is not for experiments, benchmark harnesses, or code patches.
- It should not become a disconnected reading-note archive.
- It should not be used to dump copied abstracts or venue-by-venue lists.

## One-Sentence Principle

- Advance the survey by deepening one control problem at a time, and always convert literature intake into comparative systems prose.