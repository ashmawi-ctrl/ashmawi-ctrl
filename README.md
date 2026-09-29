# Abdelrhman Ashmawi

Software engineering portfolio focused on **backend systems, reliability, debugging, testing, developer tooling, and applied ML**.

My background is rooted in production technical support around payment systems, REST APIs, webhooks, POS environments, networking, logs, and incident investigation. I use that experience to build software around real failure modes: retries, stale state, broken contracts, flaky tests, dependency regressions, worker crashes, and reproducible debugging.

## Core Software Engineering

**Languages & runtime**
- Python
- TypeScript
- Node.js
- SQL

**Backend & APIs**
- FastAPI
- REST APIs
- Webhooks
- request validation
- API contracts
- HMAC signatures
- idempotency
- background workers

**Data & persistence**
- SQLite
- relational data modeling
- durable state machines
- transactional updates
- CSV / JSONL processing
- model artifact persistence

**Reliability & distributed-systems fundamentals**
- retries and exponential backoff
- worker leases and ownership
- crash recovery
- stale-state recovery
- concurrency reasoning
- duplicate prevention
- failure classification
- timeout handling

**Testing & quality**
- pytest
- Vitest
- unit tests
- integration tests
- regression tests
- deterministic fixtures
- flaky-test investigation
- linting and type checking

**Git & software delivery**
- Git history analysis
- branches and pull requests
- issues and acceptance criteria
- patch workflows
- isolated worktrees
- GitHub Actions
- Docker
- reproducible local commands

**Debugging & observability**
- structured logs
- correlation IDs
- latency analysis
- root-cause investigation
- regression isolation
- stdout / stderr capture
- machine-readable diagnostic reports

**Applied ML**
- pandas
- scikit-learn
- preprocessing pipelines
- class imbalance
- leakage prevention
- ROC-AUC / average precision
- reproducible model evaluation

## Selected Engineering Work

### [SWE Task Harness](https://github.com/ashmawi-ctrl/swe-task-harness)

Reproducible evaluation for software-engineering bug-fix tasks.

It copies a target codebase into an isolated workspace, proves the baseline failure, verifies and applies a patch, then runs regression checks while preserving command output, exit codes, timeouts, and timing.

**Focus:** unfamiliar codebases · patches · failing-test reproduction · Docker · subprocesses · regression verification · CI

Development trail: [Issue #1](https://github.com/ashmawi-ctrl/swe-task-harness/issues/1) → [PR #2](https://github.com/ashmawi-ctrl/swe-task-harness/pull/2) → CI → merge.

---

### [Dependency Upgrade Auditor](https://github.com/ashmawi-ctrl/dependency-upgrade-auditor)

TypeScript tooling for comparing dependency-upgrade revisions against a known-good Git baseline.

It evaluates base and candidate commits in isolated worktrees, reports `package.json` dependency changes, executes explicit verification commands, and separates a broken baseline from a candidate regression.

**Focus:** TypeScript · Node.js · dependency compatibility · Git worktrees · process execution · integration tests · CI

Development trail: [Issue #1](https://github.com/ashmawi-ctrl/dependency-upgrade-auditor/issues/1) → [PR #2](https://github.com/ashmawi-ctrl/dependency-upgrade-auditor/pull/2) → green CI → merge.

Follow-up: [Issue #3](https://github.com/ashmawi-ctrl/dependency-upgrade-auditor/issues/3) covers lockfile validation and revision setup commands.

---

### [Distributed Job Runner](https://github.com/ashmawi-ctrl/distributed-job-runner)

FastAPI + SQLite backend for durable job execution with explicit worker ownership.

It implements idempotent enqueue, atomic claims, time-bounded leases, exponential retry scheduling, stale-owner rejection, and expired-lease recovery. The integration suite includes a real two-worker race against the same queue.

**Focus:** backend APIs · concurrency · persistence · leases · retries · state machines · crash recovery · Docker · CI

Development trail: [Issue #1](https://github.com/ashmawi-ctrl/distributed-job-runner/issues/1) → [PR #2](https://github.com/ashmawi-ctrl/distributed-job-runner/pull/2) → CI-found recovery bug → fix → green CI → merge.

Follow-up: [Issue #3](https://github.com/ashmawi-ctrl/distributed-job-runner/issues/3) covers lease renewal for long-running work.

---

### [Git Regression Bisector](https://github.com/ashmawi-ctrl/git-regression-bisector)

Debugging CLI for locating the first commit that changes a verification command from passing to failing.

It validates known-good and known-bad boundaries, searches first-parent history with binary search, executes probes in temporary detached worktrees, and preserves commit context and command evidence in text or JSON reports.

**Focus:** Git internals · binary search · regression isolation · temporary worktrees · subprocess control · integration testing

Development trail: [Issue #1](https://github.com/ashmawi-ctrl/git-regression-bisector/issues/1) → [PR #2](https://github.com/ashmawi-ctrl/git-regression-bisector/pull/2), then [Issue #3](https://github.com/ashmawi-ctrl/git-regression-bisector/issues/3) → [PR #4](https://github.com/ashmawi-ctrl/git-regression-bisector/pull/4).

---

### [Flaky Test Investigator](https://github.com/ashmawi-ctrl/flaky-test-investigator)

Repeated-run test investigation for distinguishing deterministic failures from unstable behavior.

It records every execution, classifies `stable-pass`, `stable-fail`, `flaky`, or `timeout`, and emits structured reports with per-run evidence and timing percentiles.

**Focus:** test reliability · failure classification · deterministic fixtures · timeouts · JSON reports · CI

Development trail: [Issue #1](https://github.com/ashmawi-ctrl/flaky-test-investigator/issues/1) → [PR #2](https://github.com/ashmawi-ctrl/flaky-test-investigator/pull/2), then [Issue #3](https://github.com/ashmawi-ctrl/flaky-test-investigator/issues/3) → [PR #4](https://github.com/ashmawi-ctrl/flaky-test-investigator/pull/4).

---

### [API Contract Guard](https://github.com/ashmawi-ctrl/api-contract-guard)

CI-friendly structural compatibility checks for JSON API responses.

It detects removed fields, nested type changes, object-to-string drift, nullability changes, and list-item incompatibilities while keeping additive changes separate from breaking changes.

**Focus:** API compatibility · recursive data structures · CLI design · regression tests · Docker · CI

## Additional Projects

### [POS Print Queue](https://github.com/ashmawi-ctrl/pos-print-queue)
SQLite-backed print queue covering idempotency, retries, ambiguous physical delivery, worker recovery, and explicit failure semantics.

### [Webhook Inspector](https://github.com/ashmawi-ctrl/webhook-inspector)
FastAPI service with HMAC signature verification, duplicate-event protection, correlation IDs, structured logging, request timing, tests, and Docker.

### [Payment Log Analyzer](https://github.com/ashmawi-ctrl/payment-log-analyzer)
CLI for CSV / JSONL operational analysis including latency percentiles, response-code trends, malformed rows, and conflicting transaction terminal states.

### [Payment Risk ML Pipeline](https://github.com/ashmawi-ctrl/payment-risk-ml-pipeline)
Reproducible tabular ML baseline with leakage-safe preprocessing, mixed numeric/categorical features, class balancing, model persistence, and imbalanced-class metrics.

## Engineering Workflow

I try to keep changes reviewable and evidence-driven:

1. reproduce the failure or define the expected behavior
2. reduce it to a focused test case
3. inspect the surrounding code and identify the relevant invariant
4. add regression or integration coverage
5. implement the smallest maintainable change
6. run focused checks and the broader suite
7. investigate CI failures instead of assuming success
8. document limitations and failure semantics
9. ship through an issue, branch, pull request, and green CI

## Stack

`Python` · `TypeScript` · `Node.js` · `FastAPI` · `SQL` · `SQLite` · `REST APIs` · `Webhooks` · `Git` · `GitHub` · `Docker` · `pytest` · `Vitest` · `Ruff` · `GitHub Actions` · `pandas` · `scikit-learn` · `Linux / CLI workflows`

## Current Focus

- backend and reliability engineering
- software evaluation and developer tooling
- unfamiliar-code debugging
- open-source contributions
- applied ML evaluation
- coding-agent / software-engineering benchmark workflows
