# Acceptance cases

These are reproducible review scenarios, not a claim that any live scheduler has been tested. Use fictional Sheet IDs and example.com fixtures. Keep actual outputs/results under ignored local/ and output/. Inspect meaning and behavior, not exact wording. Offline prompt cases require no live search or Sheet writes. One-time setup cases exercise only the explicitly supplied Sheet.

## Prompt generation

| Case | Input | Pass condition |
| --- | --- | --- |
| Default | No profile; valid-shaped fictional Sheet URL | Discloses example defaults; two complete prompts bind the same three tabs; editable sample choices are included, no unknown legal eligibility invented |
| Career/location replacement | Frontend, React/TypeScript, 5 years, New York, strict US remote | No frontend exclusion or backend-only requirement; no Houston preference or nonremote Tier A exception survives the hard override; role/location scoring adapted; other inherited defaults disclosed |
| Partial override | Example except exclude consulting companies and set Jobs weekly | Company exclusion appears where relevant; job cadence weekly; other rules retained consistently; timezone retained explicitly |
| Missing binding | No Sheet URL | Requests binding or returns marked DRAFT; does not claim final ready-to-run files |
| Custom tabs | Employers, Roles, Receipts, with Website renamed Official Site | Both prompts use the same mapping throughout embedded schema and instructions; no unintended default tab/header survives |
| Invalid weights | Job weights sum to 120 | Does not silently calculate on a 100 denominator; asks or proposes explicit normalization before finalizing |
| Regeneration | Change saved location/roles, ask to regenerate | Both fixed output paths updated; local profile/settings consistent; unrelated files untouched; user told to update existing schedules |
| No filesystem | Same complete input in a chat-only environment | Two downloads or clearly named copyable blocks; no assertion of a write to the user's computer |

For every complete output: no unresolved {{...}} tokens, no local paths or “see other prompt” dependencies, no enclosing wrapper text; all required inputs embedded. Confirm weights total 100 and arithmetic once: ratings 80/70/100/90/60 with job weights 35/20/20/15/10 gives 81.5, rounded 82.

## Calibration with supplied prompts

- 150 tracked companies and an excellent new candidate: no invented approval gate; may add under the 200 ceiling and per-run limit. At 200, report alternatives without silent removal.
- Below 80 company with exceptional monitoring reason: do not mechanically force Watch solely from score; explain the chosen status.
- Missing compensation/remote evidence: no automatic 50 or 0; qualify the evidence-based estimate or report unscored if fit cannot be assessed.
- Job at a famous company: company quality is evidence-based, not automatically the saved company score; compensation remains part of the final 10% dimension.
- Example skills include Python/database/ETL and multi-account/multi-region/GovCloud/FedRAMP; changing to frontend reconciles associated requirements rather than erasing all inherited context indiscriminately.
- Company write: sort intact rows including extra/manual columns after material changes; no job-alert logic in the company prompt.
- Job summary: exact hourly prefix and checked/total, blocked, not attempted, new, updates and closures; no-change text only after completed coverage and verified writes.
- Current-source-only candidate: preserve source uncertainty; do not equate credible current evidence with official verification or automatically discard everything due to an inaccessible ATS.
- Compare output with supplied prompts by behavior, list justified differences, and measure length. Do not claim semantic equivalence merely because weights and titles match.

## One-time setup

- New Sheet with an unrelated Sheet1: create the three target tabs and exact headers, leaving Sheet1 untouched and adding no example business records. Verify readback before reporting ready.
- Repeat against compatible tabs: plan zero mutations; preserve tab IDs, cell values and formatting.
- Blank A1 but data/formulas lower down: do not classify the tab as empty; require schema clarification before changes.
- Compatible headers reordered or with extra columns: reuse them and preserve all existing data; explicit aliases carry into both generated prompts.
- Populated tab missing a required header or with duplicate names: ask about mapping/migration; do not overwrite.
- No write tool or denied authorization: still deliver prompts with setup pending, name the connection blocker, and do not assert tabs were created.
- Explicit generate-only/read-only: generate artifacts without spreadsheet mutation, even when a write connector is available.
- Timeout after tab creation: reread metadata and headers before planning another write.

## Execution reasoning (synthetic, no network)

Walk through the generated prompts with these inputs; record expected writes and summary before any live integration test.

- Same company domain discovered twice: one row; an existing Ignore and User Notes survive.
- The same requisition returns with a tracking parameter or reopens: one Job Key, original First Seen/Review Status retained, no new-job highlight.
- One known Closed/Applied/Skip row still participates in identity deduplication.
- Three Active companies, one complete, one failed, one unattempted: target 3 = completed 1 + failed 1 + remaining 1; cannot claim no new jobs for all three. Next run still targets all Active in the selected Tier/score/name order, without counting earlier scans.
- Partial first run with a new Tier B score 88 role: save and highlight it under the example policy while reporting PARTIAL; no full-baseline prerequisite.
- An otherwise matching new role with unknown required authorization: Needs review; may be highlighted at the threshold with the uncertainty stated, never asserted eligible. Known hard mismatch is excluded.
- A company board times out or a job URL returns 404: no automatic Closed transition.
- A saved new Tier B job scores 88: highlight if above threshold and not already marked, including first run; explicitly label uncertain eligibility/availability. A pre-existing re-scored 88 role is not new. Chat delivery is separate from Sheet acknowledgement.
- Missing header or denied write: concrete setup/access blocker, no fabricated successful update; summary still returned.

## Bounded Sheet integration (only when authorized)

Read spreadsheet metadata and existing cells first. Add distinctly named TEST Companies, TEST Open Jobs and TEST Runs tabs rather than editing user data. Use the contract's headers and one fictional company/job. Clearly identify synthetic records in Notes. Write and read back; reprocess the same identities and update only an owned cell. Verify row counts unchanged and manual fields, First Seen and Alerted At preserved. Append a synthetic receipt whose coverage partition balances. Keep fixtures inspectable unless cleanup was requested. This tests storage operations, not search accuracy or scheduler autonomy.

## Actual scheduler validation (separate)

In the user's intended environment, verify web and Sheet tools, accepted prompt length, saved timezone/cadence, one bounded invocation and a repeated invocation. Check receipt, preserved manual values and summary. Do not call scheduled operation verified merely because files were generated or a connector worked in another chat.

## Release review

Validate skill frontmatter, all relative resource links, ignored private paths and exact staged diff. Inspect tracked files and commit metadata for credentials, contact details, real Sheet IDs and absolute local paths before pushing. Report which of the three validation levels were actually exercised.
