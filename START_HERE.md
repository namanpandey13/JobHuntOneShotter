# Job Search Agent Wizard

This folder is a practical wizard pack for running an ethical, contact-first job-search agent in Claude Code or Codex.

The goal is not to create a bot that blindly applies everywhere. The goal is to help an agent prepare truthful, review-ready outreach and simple application staging while keeping the human in control.

## Core Rule

The agent must work in this order:

1. Confirm the workspace is installed correctly.
2. Read the candidate profile and do-not-claim file.
3. Find or inspect real public roles.
4. Score fit before spending time.
5. Verify a direct human contact before tailoring a resume for outreach.
6. Tailor only from true candidate facts.
7. Create Gmail drafts or local draft files by default.
8. Log everything.
9. Stop before sending, submitting, guessing, or answering unknown sensitive/legal questions.

## Folder Structure

```text
job-search-agent-wizard/
|-- RUN_THIS_FIRST_PROMPT.txt
|-- START_HERE.md
|-- AGENTS.md
|-- CLAUDE.md
|-- .agents/
|   `-- skills/
|       `-- job-search-outreach-agent/
|           `-- SKILL.md
|-- profiles/
|   |-- profile.template.json
|   |-- sensitive-answers.template.json
|   `-- do-not-claim.md
|-- trackers/
|   |-- applications-tracker.csv
|   `-- contact-first-run-template.csv
|-- templates/
|   `-- outreach-email-template.md
`-- docs/
    `-- manual-installation.md
```

## What To Do First

Open this folder in Claude Code or Codex.

Paste the contents of:

```text
RUN_THIS_FIRST_PROMPT.txt
```

The agent should inspect this folder and produce a readiness report before it searches for roles, opens a browser, creates drafts, or touches application portals.

## Required Human Inputs

Before a real run, fill in:

```text
profiles/profile.template.json
profiles/do-not-claim.md
```

Optional:

```text
profiles/sensitive-answers.template.json
```

Only fill the sensitive answer file if you are comfortable storing canonical answers locally. If a sensitive or legal answer is blank, the agent must stop and ask before using the answer.

## Setup Wizard

Ask the agent to do a setup check.

It must inspect:

- `START_HERE.md`
- `RUN_THIS_FIRST_PROMPT.txt`
- `AGENTS.md`
- `CLAUDE.md`
- `.agents/skills/job-search-outreach-agent/SKILL.md`
- `profiles/profile.template.json`
- `profiles/sensitive-answers.template.json`
- `profiles/do-not-claim.md`
- `trackers/applications-tracker.csv`
- `trackers/contact-first-run-template.csv`
- `templates/outreach-email-template.md`

It must report:

- Which required files exist.
- Which candidate fields are missing.
- Whether a resume source file is available.
- Whether Gmail tools are connected.
- Whether browser automation is available.
- Whether it can run in `DRAFT_ONLY`.
- What it needs from you before a real run.

## Run Modes

### DRAFT_ONLY

Use this mode first.

The agent may:

- Find roles.
- Score fit.
- Verify direct public recruiter or hiring-team contacts.
- Tailor resumes from truthful facts.
- Render or prepare resume files.
- Create Gmail drafts if Gmail is connected and draft creation is allowed.
- Create local draft files if Gmail is not connected.
- Log results.

The agent must not:

- Send emails.
- Submit applications.
- Guess emails.
- Use generic inboxes as if they were direct contacts.
- Claim skills, employers, schools, metrics, or credentials not present in the candidate facts.
- Answer unknown sensitive/legal questions.

### STAGE_ONLY

Use this mode only after `DRAFT_ONLY` works.

The agent may:

- Open simple ATS applications.
- Fill known, truthful, non-sensitive fields.
- Upload the correct resume if upload works.
- Stop before final submission.
- Log the staging status.

The agent must stop for:

- CAPTCHA.
- Account creation.
- Workday, iCIMS, or long brittle portals.
- Unknown sensitive/legal questions.
- Required fields not covered by the profile.
- Any final submit button.

### SUBMIT_SIMPLE

Use this only when you explicitly authorize it.

The agent may submit only if:

- The role is verified and logged.
- Every required field is known and truthful.
- No sensitive/legal answer is unknown.
- No CAPTCHA or account creation is present.
- The portal is simple and stable.
- The exact resume file is known.
- You explicitly asked the agent to submit.

## Contact-First Workflow

The agent must prefer a verified direct person contact over a generic application path.

A contact is verified only when:

- The person appears publicly connected to the company.
- The email is public or discoverable from a credible source.
- The email domain matches the company or an official recruiting domain.
- The agent can cite where it found the contact.

The agent must not use:

- Guessed emails.
- Pattern-generated emails without public confirmation.
- Personal emails that are not clearly for recruiting or professional contact.
- Generic inboxes such as `jobs@`, `careers@`, `info@`, `support@`, `hello@`, or `contact@` as a substitute for direct outreach.

## Resume Tailoring Rules

The agent may reframe real experience for relevance.

The agent may not invent:

- Employers.
- Job titles.
- Degrees.
- Certifications.
- Years of experience.
- Programming languages.
- Metrics.
- Revenue numbers.
- Security clearances.
- Work authorization.
- Publications.
- Patents.
- Open source work.
- Leadership scope.

Before tailoring, the agent must read:

```text
profiles/do-not-claim.md
```

## Gmail Draft Behavior

Gmail drafts are allowed only in draft mode.

The agent must:

- Create drafts, not send.
- Use the verified contact email only.
- Keep the message short and truthful.
- Mention the role and why the candidate is a fit.
- Attach or reference the tailored resume only if available.
- Log the Gmail draft ID if Gmail returns one.

If Gmail is not connected, create local draft files and log their paths.

## First Dry Run Prompt

```text
Run a dry run for up to 3 roles in DRAFT_ONLY mode.

Do not create Gmail drafts yet.
Do not open application portals.
Do not send email.
Do not submit anything.

Inspect the candidate profile, do-not-claim file, tracker headers, and outreach template.
Then report what would happen for each role:
- fit score
- missing facts
- whether a direct contact is findable
- whether resume tailoring is safe
- whether the role should proceed, pause, or be skipped
```

## First Outreach Run Prompt

```text
Run a contact-first outreach run for up to 3 high-fit roles.

Mode: DRAFT_ONLY.

Only proceed when a public direct person email is verified.
Do not use guessed emails.
Do not use generic inboxes as direct contacts.
Generate tailored resumes only after a verified sendable path exists.
Use only facts from the profile, resume, and approved notes.
Read profiles/do-not-claim.md before tailoring.
QA each resume before drafting outreach.
Create Gmail drafts only if Gmail tooling is connected and draft creation is available.
Otherwise create local draft files.
Log every role in trackers/applications-tracker.csv.
```

## Final Operating Principle

The agent may accelerate honest work. It may not replace human judgment where truth, legal status, identity, consent, or final submission is involved.
