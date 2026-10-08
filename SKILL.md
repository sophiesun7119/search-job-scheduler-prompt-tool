---
name: search-job-scheduler-prompt-tool
description: Prepare a Google Sheet and generate two concise personalized scheduler prompts for company and job discovery. Use for setup or prompt revision from preferences, not for executing searches or creating schedules.
---

# Search Job Scheduler Prompt Tool

## Outcome and inputs

Deliver two self-contained prompts: discover companies, then discover jobs from that company list. Read the [example profile](profile-example.md), [company template](templates/find-companies.md), [job template](templates/find-jobs.md) and [Sheet contract](references/google-sheet-contract.md), resolving paths from this skill's directory. Use supplied preferences/profile; if none, use the example and disclose it. Require a Sheet URL/ID; default tabs Companies/Open Jobs/Runs. Missing binding permits an explicitly labeled draft only.

Explicit current preferences override a supplied saved profile, which overrides example defaults. Accept natural language. Preserve meaningful specifics (technologies, location exceptions, score meaning, notification conditions), not just broad job titles. Reconcile related rules when a user changes career/location. Do not infer citizenship, work authorization, sponsorship or clearance. Ask only about consequential contradictions or missing required inputs; disclose defaults for optional inputs.

## Behavioral fidelity

Separate personal preferences, execution policies and storage representation. A schema convenience must not silently change selection, ranking, coverage or alerts. For each generation resolve: role/technology/experience; hard constraints versus soft location preferences; company discovery/categories/Tiers; score dimensions and uncertainty; company limits/status/sorting; job identity/lifecycle; scan scope/order/completion; first-run and recurring alerts/summary. Keep the resolved policy in private local/profile.md; storage/timing in local/settings.md.

If existing prompts are supplied, compare them with the effective profile before generation. They are evidence of intended behavior, not automatically the standard. Preserve compatible explicit policies; resolve genuine conflicts and disclose intentional improvements. Do not introduce numeric location anchors, missing-data scores, approval gates, initial-alert silence, stricter eligibility gates or additional quotas merely to make a template deterministic. Optional policies require explicit selection; they are not hidden defaults. Numeric weights alone do not preserve score semantics.

## One-time setup

For setup-and-generation, use the [setup procedure](references/google-sheet-contract.md#one-time-setup) to create missing tabs and verified-empty headers, preserve compatible existing data and read back. Repeat setup must reuse compatible structure without writes. Explicit generate-only/read-only or calibration-only requests skip Sheet writes. Incompatible populated schemas need a focused mapping decision; never migrate silently. If the connector is unavailable, generate artifacts with setup pending and name the authorization/tool step. Do not run searches, create schedules or install a runtime.

## Compose concise outputs

Expand the two templates using only each task's necessary profile sections and runtime storage rules. Company output: Career, Location, Company preferences, Scoring evidence; company headers/storage, shared write rules, Runs. Job output: Career, Location, Job preferences, Scoring evidence, job coverage/timing; relevant company read fields, job headers/storage, shared write rules, Runs. Include concrete tab/header mappings and the Sheet URL. Exclude the other task's lifecycle/alert/discovery procedure and all setup/history narration. Company output must not contain job baseline or alert instructions.

Use {{BINDING}}, {{COMPANY_PROFILE}}, {{COMPANY_STORAGE}}, {{JOB_PROFILE}}, {{JOB_STORAGE}} and {{JOB_SUMMARY}} as composition slots, not file dependencies. Runtime prompts never reference this repository, another prompt or previous chat for policy. Include the actual cadence/timezone but do not tell tasks to schedule themselves. Adapt the job summary prefix to the selected cadence; hourly example uses `Open Jobs hourly:`. Preserve explicit output fields and no-change wording. Weights sum to 100; do not normalize silently. Use a calculator when needed; round the final score only.

Keep each requirement once where possible. Prefer compact prose/lists; schemas can be inline field lists. Remove generic explanations and duplicate safety paragraphs before removing behavior. Measure final length and compare against supplied prompts when available. Aim for a shorter result without loss of policy; this is a quality check, not an invented platform limit. Actual editor acceptance remains unverified unless tested.

Write these fixed paths relative to the root containing SKILL.md:

- output/find-companies-prompt.md
- output/find-jobs-prompt.md

Each file is the full copyable execution prompt, without wrapper commentary. Explicit regeneration replaces these files, preserving unrelated data. Keep local/ and output/ Git-ignored. Without filesystem access, provide same-named downloads or two labeled copyable blocks; do not claim local writes.

## Verify and hand off

Use [acceptance cases](tests/acceptance-cases.md) for changes. Check meaningful behavioral cases, not merely keyword presence: same facts plus same profile must lead to consistent inclusion, scoring criteria and notification decisions. Review unchanged, altered, omitted and newly introduced rules against supplied prompts. Record deviations and their reasons privately; never put development provenance into public instructions.

Check no unresolved slots, no contradictory preferences, matching schema/identity rules, protected human data, truthful partial coverage and mandatory summaries. Ensure all material original concepts are either represented or explicitly identified as changed. Return the two output links, adopted defaults, actual setup status and remaining intentional differences. Separate prompt verification, Sheet integration and scheduler execution; never claim one proves another. Only necessary connection authorization or a real ambiguity should interrupt the user's simple path from profile + Sheet to prompts.
