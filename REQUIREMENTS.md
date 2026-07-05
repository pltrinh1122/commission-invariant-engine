# REQUIREMENTS: Invariant Extraction Engine

## 1. The Philosophical Intent
The system requires a deterministic execution engine to extract and validate invariants pinned in markdown files against a structural YAML sidecar (`invariants-bond.structure.yaml`).

## 2. The Core Invariants
* **Absolute Determinism:** The engine must execute as a run-to-completion script over a defined corpus. Daemons or persistent state are forbidden.
* **Fail-Closed Architecture:** Any invalid input or state must immediately halt execution.
* **ID Integrity:** Strict integrity between markdown tags and the YAML sidecar is non-negotiable.
* **The Isolation Constraint:** Execution must rely exclusively on the Python 3 standard library.
