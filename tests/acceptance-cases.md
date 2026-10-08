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
- Three Active companies, one complete, one failed, one unattempted: target 3 = completed 1 + failed 1 + remaining 1; cannot claim no new jobs for all three. Next run still targets all Active, with unfinished companies first.
- Partial initial scan: baseline remains incomplete and highlights suppressed until a full baseline completes.
- An officially open role with unknown required authorization: Needs review; may be retained above the score floor, never highlighted as a confirmed eligible match.
- A company board times out or a job URL returns 404: no automatic Closed transition.
- A saved job scores 88 in Tier B after baseline: highlight only if new, verified Open, Eligible and not already marked; readback confirms the write. Chat delivery remains separate from Sheet acknowledgement.
- Missing header or denied write: concrete setup/access blocker, no fabricated successful update; summary still returned.

## Bounded Sheet integration (only when authorized)

Read spreadsheet metadata and existing cells first. Add distinctly named TEST Companies, TEST Open Jobs and TEST Runs tabs rather than editing user data. Use the contract's headers and one fictional company/job. Clearly identify synthetic records in Notes. Write and read back; reprocess the same identities and update only an owned cell. Verify row counts unchanged and manual fields, First Seen and Alerted At preserved. Append a synthetic receipt whose coverage partition balances. Keep fixtures inspectable unless cleanup was requested. This tests storage operations, not search accuracy or scheduler autonomy.

## Actual scheduler validation (separate)

In the user's intended environment, verify web and Sheet tools, accepted prompt length, saved timezone/cadence, one bounded invocation and a repeated invocation. Check receipt, preserved manual values and summary. Do not call scheduled operation verified merely because files were generated or a connector worked in another chat.

## Release review

Validate skill frontmatter, all relative resource links, ignored private paths and exact staged diff. Inspect tracked files and commit metadata for credentials, contact details, real Sheet IDs and absolute local paths before pushing. Report which of the three validation levels were actually exercised.
