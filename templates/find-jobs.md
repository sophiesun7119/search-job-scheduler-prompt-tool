# Find Jobs

Run one bounded scan of tracked companies for matching open jobs using the preferences below. Update the bound Google Sheet and return a concise chat summary. Do not discover additional companies, apply, contact employers or create schedules.

## Binding

{{BINDING}}

## Effective preferences

{{JOB_PROFILE}}

## Shared storage and reporting rules

{{SHEET_CONTRACT}}

## Scan and match

Read the current Active company snapshot, all existing job identities and the latest Jobs receipts. Ignore Watch and Ignore companies. If there are no Active companies, report that company discovery or activation is needed. Attempt unfinished Active companies first; otherwise prioritize Tier A/B/C, Company Score descending, then name. Every run targets ALL Active companies; batch within available capacity and record actual completion rather than silently switching to a rotating sample.

Follow each company's official careers link to its official listings/ATS, including pagination and job details. Where a fetch/extraction tool is available, use it for official routing rather than guessing providers. If the official route is unavailable, use at most one targeted company-careers search to find a route and verify the relationship on the company's official domain. A third-party search snippet alone is not current-open evidence. Report unavailable sources and incomplete detail checks.

Evaluate actual responsibilities, minimum experience, technical transferability and location restrictions, not title or keyword counts alone. Remote can be country/state restricted. Reject explicit hard mismatches; record uncertain required eligibility as Needs review, without inferring personal work authorization. Retain such otherwise matching, officially open candidates for review but exclude them from confirmed high-match highlights.

Rate technical, experience, location, company and career dimensions 0–100 with brief reasons; use the profile's weights and any explicit rating anchors. The company component uses the saved Company Score. Use the profile's missing-evidence convention for an unknown scored dimension, label it uncertain, and never override a hard filter. Compute sum(rating × weight)/100 and round once. Retain matches meeting the configured score floor. Below-floor new candidates are not added; previously saved rows remain and may be updated without deleting user history.

Preserve the official Posted At separately from First Seen. Never fabricate a posting date or call an undated newly found job newly published. Apply a posting-age cutoff only if explicitly present in the effective preferences. Verify current-open evidence before adding a role. For an existing job that can no longer be verified, mark Unverified with the reason rather than Closed without explicit closure evidence.

Deduplicate, update only changed owned fields, and read back. Follow baseline and alert rules exactly. A company with successful full coverage and zero qualifying jobs is completed; inaccessible or partially checked companies are not. Save a Jobs receipt with mutually exclusive completed/failed/remaining IDs and verified write counts. Return a short summary on every run, with qualifying new jobs separately highlighted, unresolved eligibility, failures and uncompleted coverage. Do not claim “no new jobs” across companies that were not successfully scanned.
