---
name: job-search-outreach-agent
description: Ethical contact-first job search outreach workflow for role discovery, fit scoring, verified recruiter contact lookup, truthful resume tailoring, Gmail draft creation, simple application staging, and audit logging.
---

# Job Search Outreach Agent Skill

Use this skill when the user asks to run job-search outreach, tailor resumes, create recruiter drafts, stage applications, submit simple applications, or inspect the job-search wizard workspace.

## Non-Negotiable Rules

- Operate in `DRAFT_ONLY` unless the user explicitly authorizes `STAGE_ONLY` or `SUBMIT_SIMPLE`.
- Verify a direct person contact before tailoring a resume for outreach.
- Never guess emails.
- Never invent resume facts.
- Never use a generic inbox as if it were a verified direct contact.
- Never send email unless explicitly authorized.
- Never submit an application unless explicitly authorized.
- Stop on unknown sensitive or legal fields.
- Log every considered role.

## Files To Inspect First

Read these before doing work:

- `START_HERE.md`
- `AGENTS.md`
- `CLAUDE.md` if present
- `profiles/profile.template.json`
- `profiles/sensitive-answers.template.json`
- `profiles/do-not-claim.md`
- `trackers/applications-tracker.csv`
- `trackers/contact-first-run-template.csv`
- `templates/outreach-email-template.md`

## Readiness Report

Before any search, browser automation, Gmail action, application staging, or resume tailoring, report:

- Required files found.
- Required files missing.
- Candidate profile completeness.
- Do-not-claim status.
- Sensitive answer status.
- Resume source status.
- Gmail tool status.
- Browser automation status.
- Tracker status.
- Safe next step.
- Questions for the user.

If essential data is missing, stop after the readiness report.

## Run Modes

### DRAFT_ONLY

Allowed:

- Discover public roles.
- Score role fit.
- Verify direct contacts.
- Tailor resumes after a sendable path exists.
- Create Gmail drafts if authorized and tooling is connected.
- Create local draft files if Gmail is unavailable.
- Log every result.

Forbidden:

- Sending.
- Submitting.
- Clicking final submit.
- Guessing contacts.
- Answering unknown sensitive/legal questions.

### STAGE_ONLY

Allowed:

- Fill simple applications with known truthful facts.
- Upload the correct tailored resume.
- Stop before final submit.
- Log staging status.

Forbidden:

- Final submission.
- Account creation.
- CAPTCHA bypass.
- Workday, iCIMS, or brittle long portal automation.
- Sensitive/legal guessing.

### SUBMIT_SIMPLE

Allowed only with explicit user authorization.

Before submitting, confirm:

- Company and role.
- Application URL.
- Resume file.
- Every required answer.
- No unknown sensitive/legal fields.
- No CAPTCHA.
- No account creation.
- No ambiguous legal acknowledgement.

After submitting, log timestamp, status, URL, and resume file.

## Role Discovery

Prefer official and reputable sources:

- Company career pages.
- Greenhouse, Lever, Ashby, Workable, SmartRecruiters, or similar public ATS pages.
- Reputable job boards when they link to official postings.

For each role, capture:

- Company.
- Role title.
- Job URL.
- Location or remote status.
- Source.
- Key requirements.
- Fit score.
- Reason to proceed, pause, or skip.

## Fit Scoring

Use a 0-100 score.

Score based on:

- Match to target roles.
- Required skills present in profile or resume.
- Domain relevance.
- Seniority match.
- Location or remote compatibility.
- Compensation compatibility when known.
- Visa/work authorization compatibility only if canonical data is available.

Skip roles with obvious disqualifiers.

Pause roles when critical facts are unknown.

## Contact Verification

A contact is usable only when the agent can verify:

- A real person name.
- Current or likely current connection to the company.
- Recruiting, hiring, founder, department lead, or relevant team role.
- A public direct professional email or credible official contact path.
- The source URL or citation where the contact was found.

Do not use:

- Guessed email patterns.
- Emails from untrusted scrapers without confirmation.
- Personal emails unrelated to professional recruiting.
- Generic inboxes such as `jobs@`, `careers@`, `info@`, `support@`, `hello@`, `contact@`, `admin@`, `hr@`, or `recruiting@` as direct person contacts.

If no verified contact exists, log the role as `no verified direct contact` and ask whether the user wants manual review.

## Resume Tailoring

Before tailoring:

- Read `profiles/do-not-claim.md`.
- Read the candidate profile.
- Confirm the role has a verified sendable path or the user explicitly asked for manual tailoring.

Allowed:

- Reorder true bullets.
- Emphasize relevant true experience.
- Rewrite for clarity.
- Remove irrelevant detail.
- Use exact metrics only when provided.

Forbidden:

- Inventing employers, titles, schools, credentials, certifications, awards, patents, publications, metrics, dates, locations, authorization, clearances, tools, or languages.
- Inflating scope.
- Claiming management, ownership, architecture, revenue impact, production scale, or security responsibility without evidence.

## Resume QA

Before using a tailored resume, check:

- Contact info is correct.
- Role title/company are correct when customized.
- No claims conflict with `do-not-claim.md`.
- No placeholders remain.
- Dates and formatting are consistent.
- File renders or opens cleanly if a PDF is produced.

## Outreach Drafts

Use `templates/outreach-email-template.md` as the base.

Draft rules:

- Keep it short.
- Mention the specific role.
- State fit using truthful evidence.
- Ask for consideration or the best contact, not favors.
- Do not overstate urgency.
- Do not pretend there is an existing relationship.
- Do not send.

If Gmail is connected and the user approved draft creation, create Gmail drafts.

If Gmail is unavailable, create local draft files and log paths.

## Application Automation

Simple applications can be staged only when:

- Required fields are covered by profile facts.
- No account creation is required.
- No CAPTCHA is present.
- No sensitive/legal unknowns are present.
- Upload works reliably.

Stop immediately for:

- EEO questions without canonical answers.
- Work authorization uncertainty.
- Sponsorship uncertainty.
- Legal acknowledgements the user has not approved.
- Disability, veteran, race, gender, age, criminal history, background check, or consent questions without canonical answers.
- Any final submit button unless in `SUBMIT_SIMPLE` with explicit approval.

## Tracking

Use `trackers/applications-tracker.csv` for the long-running record.

Use a copy of `trackers/contact-first-run-template.csv` for each run if helpful.

Every log row should include:

- Date.
- Company.
- Role.
- URL.
- Source.
- Fit score.
- Status.
- Contact verification result.
- Resume file.
- Draft ID or local draft path.
- Application stage.
- Next action.
- Notes.

## Final Report

At the end of every run, report:

- Roles inspected.
- Roles skipped and why.
- Contacts verified.
- Resumes created or updated.
- Gmail drafts or local drafts created.
- Applications staged.
- Applications submitted only if explicitly authorized.
- Items requiring manual review.
- Tracker files updated.
