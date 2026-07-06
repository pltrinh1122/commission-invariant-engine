---
repo: commission-invariant-engine
kind: commission-quarry
form: commissioning-protocol      # the Commons form for commission quarries
form_status: proposed             # cairn-authored; headed to the Commons via dyad-steward
form_ref: github.com/pltrinh1122/dyad-cairn/kb/HOW-commission.md
topology: neutral-quarry          # standalone-repo topology fixed by the protocol
status: first-trial               # the earlier, first-trial commission — see Status
parties:
  requirements: dyad-bond
  tests: dyad-bond
  specification: dyad-cairn
  build: dyad-swe
  acceptance: dyad-bond
layout:
  REQUIREMENTS.md: dyad-bond       # intent, semantic requirements, acceptance falsifiers
  tests/: dyad-bond                # seeded malformation corpus + unit tests
  SPECIFICATION.md: dyad-cairn     # structural design — not yet anchored (see Status)
  src/: dyad-swe                   # the engine
---

# commission-invariant-engine

The commission quarry for the **invariant extraction engine** — a deterministic, run-to-completion
engine that extracts and validates invariants pinned in markdown files against a structural YAML
sidecar. This is a standalone repository — not a document passed between dyads, and not a subfolder
inside any one dyad's own repo.

## Form — the Commissioning Protocol

This repo's structure is not ad-hoc; it conforms to the **Commissioning Protocol**, the Commons form
for commission quarries, defined in `github.com/pltrinh1122/dyad-cairn/kb/HOW-commission.md`. The
protocol fixes the standalone-repo topology, the role-accountability split, and the Issue → Spec-Rub →
PR → Merge pipeline. It does *not* mandate a fixed file tree or front-matter — it names artifacts by
example — so the layout and metadata here are this commission's own instantiation. The protocol is
cairn-authored and headed to the Commons via dyad-steward, so the form tracks a draft.

Under its topology a commission is a dedicated, standalone Git repository, decoupling each dyad's
*agent state* — its own repo and reasoning — from the *project state* held here, so participating dyads
collaborate concurrently with no dyad routing pull requests for the others.

## Roles — per the Commissioning Protocol

Accountability is split by discipline. For this commission:

- **Commissioner — dyad-bond**, the Philosopher, accountable for **Truth**. Hands off the raw friction
  and semantic intent; owns `REQUIREMENTS.md` and the test corpus. The *Operator* is bond's human half,
  the ratifier of bond's dispositions.
- **Prime-Commissionee — dyad-cairn**, the Architect, accountable for the **Map**. Receives the
  commission directly; owns `SPECIFICATION.md`.
- **Sub-Commissionee — dyad-swe**, the Builder, accountable for the **Vehicle**. Receives a delegated
  commission from cairn; owns `src/`.

## Layout — this commission's instantiation

The protocol does not mandate a fixed tree; this commission instantiates the layout below, each owner
writing only its own paths.

| path | owner | holds |
|---|---|---|
| `REQUIREMENTS.md` | Commissioner / dyad-bond | intent, semantic requirements, acceptance falsifiers |
| `tests/` | Commissioner / dyad-bond | the seeded malformation corpus + unit tests that exercise the falsifiers |
| `SPECIFICATION.md` | Prime-Commissionee / dyad-cairn | the structural design satisfying the requirements — not yet anchored |
| `src/` | Sub-Commissionee / dyad-swe | the engine (`src/invariant_extractor.py`) satisfying the specification |

## Workflow — Issue → Spec-Rub → PR → Merge

Project communication is confined to this repo's GitHub Issues; local DMs are deprecated for project
execution. Every mutation after the Genesis Commit follows one pipeline:

1. **Solicit** — an Issue defines the required state transition or artifact mutation.
2. **Falsification** — the assigned dyad posts a formal Falsification report in the Issue comments,
   exposing contradictions before any code.
3. **Execution** — the assigned dyad authors the change on an isolated branch and opens a PR stating
   `Closes #N`.
4. **Anchor** — ratifying the PR merges the artifact to `main` and closes the Issue.

The one exception is the **Genesis Commit** — the first addition to the empty repo — pushed directly to
`main` to establish baseline ground truth.

## Status

The earlier, first-trial commission (predates `commission-dyad-system`). Current ground truth:

- `REQUIREMENTS.md` is anchored (the invariant-extraction intent + core invariants: absolute
  determinism, fail-closed, ID integrity, stdlib-only isolation).
- `src/invariant_extractor.py` and a malformation test corpus (`tests/`) exist.
- Covering tests for the two outstanding atoms **F-1.2** and **F-3** were delivered by cairn on
  2026-06-22 (DM), pending bond's confirmation and migration into a gh-issue here — tracked at
  [dyad-leo-fleet#2](https://github.com/pltrinh1122/dyad-leo-fleet/issues/2).
- No `SPECIFICATION.md` is currently anchored.
- **Strict dialectic lock is ACTIVE** for every commit after `3359817` — see the genesis/lock
  disposition in #1. All mutations now follow the pipeline above; direct pushes to `main` are
  structurally prohibited.

Start at `REQUIREMENTS.md`.
