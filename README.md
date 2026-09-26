# Abdelrhman Ashmawi

Backend, reliability, and applied ML-focused engineer with a production support background in payment systems, REST APIs, webhooks, POS environments, networking, logs, and incident investigation.

I am most interested in technical work where the hard part is understanding a system, reproducing a failure, making a safe change, and proving the behavior with tests or measurable evaluation.

## Engineering focus

- Python backend and developer tooling
- debugging and root-cause analysis
- regression testing and reproducible bug reports
- API contracts and integration reliability
- idempotency, retries, state machines, and failure recovery
- tabular machine learning and model evaluation
- Git issues, feature branches, pull requests, and CI
- Dockerized development and evaluation workflows
- SQL, structured logs, and operational data analysis

## Project map

### [SWE Task Harness](https://github.com/ashmawi-ctrl/swe-task-harness)

A reproducible evaluator for software-engineering bug-fix tasks.

It copies an unfamiliar codebase into a temporary workspace, proves the baseline failure, checks and applies a real patch, then runs regression verification while recording command output, exit codes, timeouts, and timing.

**Engineering signals:** repository inspection, failing-test reproduction, patch workflows, subprocess control, temporary isolation, Docker, task contracts, CI.

Development trail: [Issue #1](https://github.com/ashmawi-ctrl/swe-task-harness/issues/1) → [PR #2](https://github.com/ashmawi-ctrl/swe-task-harness/pull/2) → green CI → merge.

### [API Contract Guard](https://github.com/ashmawi-ctrl/api-contract-guard)

A CI-friendly tool for detecting breaking structural drift between JSON API responses.

It catches removed fields, nested type changes, object-to-string drift, nullability changes, and list item incompatibilities while separating breaking changes from additive fields.

**Engineering signals:** recursive data structures, compatibility rules, CLI exit semantics, regression tests, Docker, CI.

Development trail: [Issue #1](https://github.com/ashmawi-ctrl/api-contract-guard/issues/1) → [PR #2](https://github.com/ashmawi-ctrl/api-contract-guard/pull/2) → green CI → merge.

### [Payment Risk ML Pipeline](https://github.com/ashmawi-ctrl/payment-risk-ml-pipeline)

A reproducible baseline for imbalanced tabular payment-risk classification.

It validates dataset assumptions, excludes identifiers explicitly, splits before fitting preprocessing, combines numeric/categorical transformations in a single sklearn pipeline, trains a class-balanced logistic baseline, and reports ROC-AUC, average precision, threshold metrics, and a confusion matrix.

**Engineering signals:** leakage prevention, imbalanced classification, reproducible preprocessing, model persistence, synthetic data generation, Docker, CI.

Development trail: [Issue #1](https://github.com/ashmawi-ctrl/payment-risk-ml-pipeline/issues/1) → [PR #2](https://github.com/ashmawi-ctrl/payment-risk-ml-pipeline/pull/2) → green CI → merge.

### [POS Print Queue](https://github.com/ashmawi-ctrl/pos-print-queue)

A SQLite-backed print queue built around a real reliability failure: preventing duplicate receipts when network failures and user retries overlap.

It models job states explicitly, uses idempotency keys, applies exponential retry backoff, distinguishes safe failures from ambiguous delivery, and supports deliberate stale-worker recovery.

**Engineering signals:** state machines, persistence, idempotency, retry safety, failure semantics, CLI design, tests, CI.

Development trail: [Issue #1](https://github.com/ashmawi-ctrl/pos-print-queue/issues/1) → [PR #2](https://github.com/ashmawi-ctrl/pos-print-queue/pull/2) → green CI → merge.

### [Webhook Inspector](https://github.com/ashmawi-ctrl/webhook-inspector)

A FastAPI service for reproducing and inspecting webhook integration behavior.

It includes HMAC-SHA256 signature verification, duplicate-event protection, correlation IDs, structured JSON logs, request timing, event inspection, Docker, and automated tests.

**Engineering signals:** HTTP APIs, security primitives, observability, idempotency, backend testing, containerization.

### [Payment Log Analyzer](https://github.com/ashmawi-ctrl/payment-log-analyzer)

A command-line tool that turns payment/API log exports into an operational report.

It parses CSV and JSONL, calculates latency percentiles, groups response codes and endpoint failures, tolerates malformed rows, and flags conflicting terminal transaction states.

**Engineering signals:** data parsing, defensive input handling, statistics, CLI design, operational debugging, tests, CI.

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

Python · pandas · scikit-learn · FastAPI · SQL · SQLite · REST APIs · Webhooks · Git · GitHub · Docker · pytest · Ruff · GitHub Actions · Linux/CLI workflows

## Current direction

I am expanding the same workflow into external open-source contributions and public ML evaluation work: unfamiliar codebases, reproducible experiments, focused patches, and measurable results.

I am particularly interested in backend engineering, reliability, AI/software evaluation, applied machine learning, coding-agent benchmarks, and open-source systems.
