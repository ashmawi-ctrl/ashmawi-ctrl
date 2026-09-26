# Abdelrhman Ashmawi

Technical Support professional moving deeper into software engineering through production-focused backend and reliability projects.

My day-to-day background is in payment integrations, REST APIs, webhooks, POS systems, logs, networking, incident investigation, and root-cause analysis. I use that experience to build small tools around failure handling, observability, reproducibility, and safe recovery.

## Engineering focus

- debugging production-style failures from logs and symptoms
- reading and changing unfamiliar codebases
- writing regression tests before or alongside fixes
- API contracts, webhooks, idempotency, retries, and failure states
- Git branches, issues, pull requests, and CI checks
- Python, SQL, FastAPI, SQLite, Docker, GitHub Actions
- documenting design trade-offs instead of hiding edge cases

## Selected work

### [POS Print Queue](https://github.com/ashmawi-ctrl/pos-print-queue)

SQLite-backed print queue built around a real reliability problem: preventing duplicate receipts when users retry after network failures.

Highlights:
- idempotency keys
- explicit job state machine
- exponential retry backoff
- ambiguous-delivery handling
- worker-crash recovery
- issue-driven feature development and regression tests
- GitHub Actions quality checks

Recent engineering workflow: [Issue #1](https://github.com/ashmawi-ctrl/pos-print-queue/issues/1) → [PR #2](https://github.com/ashmawi-ctrl/pos-print-queue/pull/2) → CI → merge.

### [Webhook Inspector](https://github.com/ashmawi-ctrl/webhook-inspector)

FastAPI service for inspecting signed webhook deliveries and reproducing integration failures.

Highlights:
- HMAC-SHA256 signature verification
- duplicate-event detection
- correlation IDs
- structured JSON logging
- request latency tracking
- automated tests
- Docker + CI

### [Payment Log Analyzer](https://github.com/ashmawi-ctrl/payment-log-analyzer)

CLI for turning payment/API log exports into an operational report.

Highlights:
- CSV and JSONL parsing
- p50 / p95 / max latency
- response-code analysis
- per-endpoint metrics
- malformed-row handling
- transaction terminal-state conflict detection
- Markdown and JSON reports

## How I approach a bug

1. reproduce the behavior with the smallest useful case
2. identify the boundary where the observed behavior becomes incorrect
3. add or improve a regression test
4. make the smallest maintainable fix
5. run linting and the full test suite
6. document important failure semantics and trade-offs
7. ship through a reviewable pull request

## Currently building toward

- API contract compatibility tooling
- network diagnostics for POS environments
- Dockerized software-engineering task harnesses
- open-source bug fixes and test contributions

I am particularly interested in backend engineering, reliability, developer tooling, software evaluation, and open-source work.
