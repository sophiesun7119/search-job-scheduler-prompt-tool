# Runtime parity audit: generic prompt generator vs. deployed schedules

This repository is a reusable **generator**, not a snapshot of any user's private scheduled tasks. The examples and generated prompts must not be presented as proof that a separate scheduler currently executes the same policies.

## Why an audit matters

Real-world company and jobs workflows commonly evolve independently after prompts are generated. An existing Google Sheet may have company statuses `Active / Inactive / Cooldown`, an eligibility date, one table for prospective roles, another for actual applications, and per-company/per-run logs. Meanwhile a generic starter template may still assume `Active / Watch / Ignore`, a single `Runs` receipt, or a full-roster-per-run scan. These are **semantically different operating modes**.

| Dimension | Starter template in this repo | Example evolved runtime pattern | Migration guidance |
| --- | --- | --- | --- |
| Company eligibility | Active/Watch/Ignore | Active/Inactive/Cooldown with Next Eligible Date | Ask for authoritative live dropdown/header mapping; never translate Watch to Cooldown without user consent |
| Scanning cadence | Every Active company on each run | Per-tier batches of at most 25, persisted cycle position | Treat as opt-in behavior change; preserve fairness, unattempted accounting, retries |
| Telemetry | Generic `Runs` receipt | Separate `Scan Status` and `Scan Runs` | Map exact live columns; no silent schema replacement |
| Identity | Stable ATS ID, normalized URL | Hard pre-insert full-history dedup, status-safe upsert | Verify legacy decisions and direct job links remain protected |
| Failure accounting | Completed/failed/remaining | CHECKED/BLOCKED/NOT_ATTEMPTED and cumulative categorized failure counts | Distinguish site failure from a truly unattempted company |
| Application tracking | Not managed here | Separate submitted-application tab and optional Gmail reconciliation | Do not edit application rows or inbox state from discovery task |
| Notifications | Mandatory chat summary in prompt | Chat summary policy + independent platform notification toggles | Verify saved task settings; text alone does not guarantee push |
| Source of authority | Generated prompt text | Saved prompt + actual Sheet state | Inspect saved prompt, live headers and run receipts before claiming runtime parity |

## Checklist for a user asking to reproduce an existing scheduler

1. Read the **actual saved task prompts** and their cadence, timezone, enabled/notification flags, not just spreadsheet README tabs.
2. Inspect current Sheet metadata, headers, dropdown values, status meanings, tab ownership and logging fields. Avoid publishing any account-specific IDs, company data or applicant details.
3. Diff generator output against **both** existing tasks: inclusion/eligibility, scan scope and rotation, scoring, hard dedup, write ownership, retry/bookmark/retention, chat reporting and notifications.
4. Classify each difference as **intentional portability default**, **runtime evolution**, **incompatible schema**, or **unresolved defect**. Ask for explicit choice before changing semantics.
5. Test on synthetic data: never modify a running schedule during a documentation audit. Schema migrations, live prompt updates and task creation require separate explicit authorization.
6. Validate separately: (a) prompt generation, (b) connected Sheet read/write semantics, (c) actual scheduled execution and chat/push delivery. None proves the others.

## Implementation status

The generic templates in this repo still default to all-Active-per-run, Active/Watch/Ignore and Companies/Open Jobs/Runs. This guide **does not retrofit** tier-batch execution, eligibility reactivation or a multi-tab Scan Runs schema into generated prompts; those are separate engineering tasks and acceptance tests. The repo remains useful for generating **new generic workflows** or as a structured input for a deliberate custom migration.

Do **not** paste private runtime prompts or live sheet identifiers into a public issue or this repository. Use fictional fixtures when documenting differences.
