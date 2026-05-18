# Codex Project Instructions

This project is a job-search outreach wizard pack. Codex must treat it as an operating manual, not as a loose writing project.

## Required First Reads

Before doing job-search work, read:

- `START_HERE.md`
- `.agents/skills/job-search-outreach-agent/SKILL.md`
- `profiles/profile.template.json`
- `profiles/do-not-claim.md`
- `templates/outreach-email-template.md`
- Existing tracker CSV files

## Default Mode

Default to `DRAFT_ONLY`.

Do not send email, submit applications, answer unknown sensitive/legal fields, or make irreversible changes unless the user explicitly asks for that exact action.

## Safety Rules

- Contact-first: verify a direct human contact before tailoring for outreach.
- No guessed emails.
- No fake resume claims.
- No unverified metrics.
- No generic inboxes as a substitute for a person contact.
- Gmail drafts by default; never send unless explicitly authorized.
- Stop on legal, immigration, demographic, disability, veteran, criminal history, sponsorship, consent, or background-check questions unless canonical answers are provided.
- Keep submitted, staged, skipped, and drafted work separately logged.

## Before Any Run

Produce a readiness report that states:

- What files were inspected.
- Which required fields are missing.
- Whether a resume source exists.
- Whether Gmail draft creation is available.
- Whether browser automation is available.
- Whether trackers are ready.
- The safest next action.

## Logging

Every role considered must be logged in `trackers/applications-tracker.csv` or a run-specific copy of `trackers/contact-first-run-template.csv`.

Include enough detail for the user to audit:

- Company
- Role
- URL
- Fit score
- Contact verification status
- Resume file used
- Draft or submission status
- Next action
- Notes

## Human Approval Required

Ask before:

- Creating Gmail drafts.
- Opening application portals.
- Filling application forms.
- Uploading resumes.
- Clicking final submit.
- Sending any email or message.
- Using sensitive/legal answers.
- Proceeding when facts are missing or ambiguous.
