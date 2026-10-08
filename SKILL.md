---
name: search-job-scheduler-prompt-tool
description: Generate or revise two personalized scheduler prompts for company discovery and open-job discovery using a shared Google Sheet. Use for preparing prompts from personal preferences, not for executing searches or creating schedules.
---

# Search Job Scheduler Prompt Tool

## Outcome

Deliver two self-contained scheduler prompts that the user can copy in full. One discovers companies; the other reads the company list and finds jobs. Google Sheets provides shared state. As part of a setup-and-generation request, prepare the supplied Sheet once as described below. Do not execute searches, create schedules or install a runtime. Honor an explicit generate-only or read-only request without Sheet writes.

## Inputs and resources

Read [profile-example.md](profile-example.md), the user's supplied profile/preferences, both [company](templates/find-companies.md) and [job](templates/find-jobs.md) templates, and the [Sheet contract](references/google-sheet-contract.md). Resolve resource paths relative to this SKILL.md, regardless of the working directory.

Use explicit current preferences over a supplied saved profile over example defaults. If no profile is supplied, use the example and say so. Accept natural language. Reconcile related rules: replacing backend with frontend also changes relevant technologies and exclusions. Do not infer authorization, visa, citizenship or clearance. Resolve consequential contradictions with a short question; do not interrogate the user about optional details that have disclosed defaults.

Require one Google Sheet URL/ID. Default tab names: Companies, Open Jobs, Runs. Accept tab/header mappings and embed the same mapping in both outputs. Keep stable Runs.Task values Companies / Jobs distinct from user-renamed tab titles. Suggested timing defaults come from the example, not from the user's location automatically. An explicit timing override wins. Missing binding permits a clearly labeled DRAFT only; never fabricate a resource or call it ready.

## One-time Sheet setup

For a request to set up this tool with a supplied Sheet, inspect and prepare that Sheet before final handoff. Use the [setup procedure](references/google-sheet-contract.md#one-time-setup) and its exact headers. Create missing tabs and initialize verified-empty target tabs; reuse compatible existing headers and data. Preserve unrelated tabs, sharing and human data. Do not ask users to manually paste headers when an authorized write tool is available.

Read back headers and persist setup status in local/settings.md. A repeat invocation should make no writes when the structure is already compatible. Ask a focused question only for ambiguous populated schemas or required authorization. If no Sheet tool is available, still generate the prompts, clearly label Sheet setup as pending, and explain how to connect a Sheet-capable tool or use the header reference manually. Never present artifact completion as verified setup.

## Generation

Save the resolved human-readable profile to local/profile.md and Sheet/timing settings to local/settings.md when filesystem writing is available. These are private. Summarize inherited defaults and consequential overrides outside the prompt files.

Expand {{BINDING}}, {{COMPANY_PROFILE}} or {{JOB_PROFILE}}, and {{SHEET_CONTRACT}} in each template. Binding includes the real Sheet URL, exact tabs/header mapping, timezone and suggested cadence; cadence is descriptive and must not instruct the running task to schedule itself. Include only relevant preference sections per task, but keep shared location exceptions, score policies (including missing-evidence treatment), Tier meanings and state rules consistent. Expand {{SHEET_CONTRACT}} with header definitions and runtime rules only; exclude the One-time setup procedure and manual header-pasting directions. Embed the necessary rules as text, replacing default names with the user's mapping; do not leave local references or “see the other prompt.” Check weights sum to 100; ask or propose a disclosed normalization if not.

Keep prompts concise without silently removing filters, evidence rules or shared-state requirements. Check the target editor's actual limits when available. If a complete prompt cannot fit, explain that specific constraint and propose a compact equivalent for review; do not invent a universal limit or silently add an external README dependency.

Write relative to the project root (the directory containing this SKILL.md):

- output/find-companies-prompt.md
- output/find-jobs-prompt.md

Files contain only their complete execution prompt, without wrapper commentary or enclosing code fences. An explicit regeneration request replaces these outputs using the updated inputs; preserve unrelated files. Keep private inputs and outputs out of Git. If local writes are unavailable, supply two same-named downloads, or two separately labeled copyable text blocks. Never claim local files were saved when they were not.

## Acceptance and handoff

Check both prompts for unresolved placeholders, contradictory preferences, inconsistent tab/field names, incorrect scoring arithmetic and local/prior-chat dependencies. Confirm all Active coverage, deduplication, preservation of manual fields, baseline handling, honest partial results and summary/high-match distinction. Use [acceptance cases](tests/acceptance-cases.md) when validating changes to this skill.

Return links to the two files (or equivalent delivery), a brief effective-profile/defaults summary, suggested schedules and setup prerequisites. Distinguish artifact completeness from verified Sheet access and scheduler execution. Report which tabs were created, reused or need attention. The user only needs to complete any necessary connection authorization in the environment that will actually run the tasks. A public-edit link is not proof that a scheduler has a write tool. Provide setup guidance without claiming access or successful execution that has not been tested.
