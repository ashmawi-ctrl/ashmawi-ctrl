# Abdelrhman Ashmawi

Software engineering, backend, reliability, and applied ML-focused engineer with a production support background in payment systems, REST APIs, webhooks, POS environments, networking, logs, and incident investigation.

I am most interested in technical work where the hard part is understanding an unfamiliar system, reproducing a failure, making a safe change, and proving the behavior with tests or measurable evaluation.

## Engineering focus

- Python and TypeScript backend / developer tooling
- debugging and root-cause analysis
- regression testing and reproducible bug reports
- Git history analysis and failure isolation
- dependency and build compatibility
- concurrency, leases, retries, idempotency, and failure recovery
- API contracts and integration reliability
- Git issues, feature branches, pull requests, and CI
- Dockerized development and evaluation workflows
- SQL, SQLite, structured logs, and operational data analysis
- tabular machine learning and model evaluation

## Project map

### [SWE Task Harness](https://github.com/ashmawi-ctrl/swe-task-harness)

A reproducible evaluator for software-engineering bug-fix tasks.

It copies an unfamiliar codebase into a temporary workspace, proves the baseline failure, checks and applies a real patch, then runs regression verification while recording command output, exit codes, timeouts, and timing.

**Engineering signals:** repository inspection, failing-test reproduction, patch workflows, subprocess control, temporary isolation, Docker, task contracts, CI.

Development trail: [Issue #1](https://github.com/ashmawi-ctrl/swe-task-harness/issues/1) → [PR #2](https://github.com/ashmawi-ctrl/swe-task-harness/pull/2) → green CI → merge.

### [Dependency Upgrade Auditor](https://github.com/ashmawi-ctrl/dependency-upgrade-auditor)

A TypeScript tool for auditing Node.js dependency-upgrade revisions against a known-good Git baseline.

It compares package.json dependency declarations, evaluates base and candidate commits in isolated worktrees, captures test/build evidence, and distinguishes a broken baseline from a candidate regression.

**Engineering signals:** unfamiliar repository evaluation, TypeScript, dependency compatibility, Git worktrees, subprocess execution, integration testing, CI.

Development trail: [Issue #1](https://github.com/ashmawi-ctrl/dependency-upgrade-auditor/issues/1) → [PR #2](https://github.com/ashmawi-ctrl/dependency-upgrade-auditor/pull/2) → green CI → merge. Follow-up work is tracked in [Issue #3](https://github.com/ashmawi-ctrl/dependency-upgrade-auditor/issues/3).

### [Distributed Job Runner](https://github.com/ashmawi-ctrl/distributed-job-runner)

A FastAPI + SQLite backend for durable job execution with explicit worker ownership.

It uses idempotent enqueue, atomic claims, time-bounded leases, exponential retry scheduling, stale-owner rejection, and expired-lease recovery. The integration suite includes a real two-worker race against the same SQLite queue.

**Engineering signals:** backend APIs, persistence, concurrency reasoning, leases, state machines, retries, crash recovery, integration testing, Docker, CI.

Development trail: [Issue #1](https://github.com/ashmawi-ctrl/distributed-job-runner/issues/1) → [PR #2](https://github.com/ashmawi-ctrl/distributed-job-runner/pull/2) → CI-found recovery bug → fix → green CI → merge. Long-running lease renewal is tracked separately in [Issue #3](https://github.com/ashmawi-ctrl/distributed-job-runner/issues/3).

### [Git Regression Bisector](https://github.com/ashmawi-ctrl/git-regression-bisector)

A debugging CLI that finds the first commit that changes a verification command from passing to failing.

It validates known-good / known-bad boundaries, searches first-parent history with binary search, runs probes inside temporary detached worktrees so the caller's checkout is untouched, and preserves command output, timing, timeout state, and commit context in text or JSON reports.

**Engineering signals:** Git internals, regression isolation, binary search, subprocess control, worktree safety, integration testing, CI.

Development trail: [Issue #1](https://github.com/ashmawi-ctrl/git-regression-bisector/issues/1) → [PR #2](https://github.com/ashmawi-ctrl/git-regression-bisector/pull/2), then [Issue #3](https://github.com/ashmawi-ctrl/git-regression-bisector/issues/3) → [PR #4](https://github.com/ashmawi-ctrl/git-regression-bisector/pull/4).

### [Flaky Test Investigator](https://github.com/ashmawi-ctrl/flaky-test-investigator)

A repeat-run investigation tool for distinguishing deterministic failures from unstable test behavior.

It executes the same verification command repeatedly, preserves stdout/stderr and timing for every run, classifies stable-pass / stable-fail / flaky / timeout behavior, and can emit archival JSON reports with p50 and p95 timing.

**Engineering signals:** test reliability, failure classification, deterministic regression fixtures, timeout handling, reporting, CI.

Development trail: [Issue #1](https://github.com/ashmawi-ctrl/flaky-test-investigator/issues/1) → [PR #2](https://github.com/ashmawi-ctrl/flaky-test-investigator/pull/2), then [Issue #3](https://github.com/ashmawi-ctrl/flaky-test-investigator/issues/3) → [PR #4](https://github.com/ashmawi-ctrl/flaky-test-investigator/pull/4).

### [API Contract Guard](https://github.com/ashmawi-ctrl/api-contract-guard)

A CI-friendly tool for detecting breaking structural drift between JSON API responses.

It catches removed fields, nested type changes, object-to-string drift, nullability changes, and list item incompatibilities while separating breaking changes from additive fields.

**Engineering signals:** recursive data structures, compatibility rules, CLI exit semantics, regression tests, Docker, CI.

### [POS Print Queue](https://github.com/ashmawi-ctrl/pos-print-queue)

A SQLite-backed print queue built around a real reliability failure: preventing duplicate receipts when network failures and user retries overlap.

It models job states explicitly, uses idempotency keys, applies exponential retry backoff, distinguishes safe failures from ambiguous delivery, and supports deliberate stale-worker recovery.

**Engineering signals:** state machines, persistence, idempotency, retry safety, failure semantics, CLI design, tests, CI.

### [Webhook Inspector](https://github.com/ashmawi-ctrl/webhook-inspector)

A FastAPI service for reproducing and inspecting webhook integration behavior.

It includes HMAC-SHA256 signature verification, duplicate-event protection, correlation IDs, structured JSON logs, request timing, event inspection, Docker, and automated tests.

**Engineering signals:** HTTP APIs, security primitives, observability, idempotency, backend testing, containerization.

### [Payment Log Analyzer](https://github.com/ashmawi-ctrl/payment-log-analyzer)

A command-line tool that turns payment/API log exports into an operational report.

It parses CSV and JSONL, calculates latency percentiles, groups response codes and endpoint failures, tolerates malformed rows, and flags conflicting terminal transaction states.

**Engineering signals:** data parsing, defensive input handling, statistics, CLI design, operational debugging, tests, CI.

### [Payment Risk ML Pipeline](https://github.com/ashmawi-ctrl/payment-risk-ml-pipeline)

A reproducible baseline for imbalanced tabular payment-risk classification.

It validates dataset assumptions, excludes identifiers explicitly, splits before fitting preprocessing, combines numeric/categorical transformations in a single sklearn pipeline, trains a class-balanced logistic baseline, and reports ROC-AUC, average precision, threshold metrics, and a confusion matrix.

**Engineering signals:** leakage prevention, imbalanced classification, reproducible preprocessing, model persistence, synthetic data generation, Docker, CI.

## How I approach engineering tasks

1. Reproduce the behavior before changing code.
2. Reduce the problem to the smallest useful failing case.
3. Read the surrounding code and identify the actual contract or invariant.
4. Add a regression test that demonstrates the failure.
5. Implement the smallest maintainable fix.
6. Run focused tests, then the broader suite.
7. Document important trade-offs and failure semantics.
8. Ship through a reviewable pull request with CI.

## Tools I use

Python · TypeScript · Node.js · FastAPI · pandas · scikit-learn · SQL · SQLite · REST APIs · Webhooks · Git · GitHub · Docker · pytest · Vitest · Ruff · GitHub Actions · Linux/CLI workflows

## Current direction

I am expanding the same workflow into external open-source contributions and public software/ML evaluation work: unfamiliar codebases, reproducible experiments, focused patches, and measurable results.

I am particularly interested in backend engineering, reliability, software evaluation, applied machine learning, coding-agent benchmarks, and open-source systems.
