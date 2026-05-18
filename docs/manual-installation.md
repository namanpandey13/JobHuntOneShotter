# Manual Installation

This document explains how to install and run the job-search agent wizard pack manually.

## 1. Create The Repository Folder

Create a folder named:

```text
job-search-agent-wizard
```

Place these files in it:

```text
START_HERE.md
RUN_THIS_FIRST_PROMPT.txt
AGENTS.md
CLAUDE.md
.agents/skills/job-search-outreach-agent/SKILL.md
profiles/profile.template.json
profiles/sensitive-answers.template.json
profiles/do-not-claim.md
trackers/applications-tracker.csv
trackers/contact-first-run-template.csv
templates/outreach-email-template.md
docs/manual-installation.md
```

## 2. Add Your Resume

Add your resume source file to the folder, then update:

```text
profiles/profile.template.json
```

Recommended paths:

```text
resumes/base-resume.pdf
resumes/base-resume.docx
resumes/base-resume.md
```

If you add a `resumes/` folder, commit it only if you are comfortable storing those files in GitHub.

## 3. Fill The Profile

Open:

```text
profiles/profile.template.json
```

Fill in:

- Candidate contact info.
- Resume paths.
- Target titles.
- Target locations.
- Dealbreakers.
- Experience facts.
- Education facts.
- Project facts.
- Truthful proof points.

Do not put sensitive legal answers in the profile file.

## 4. Fill The Do-Not-Claim File

Open:

```text
profiles/do-not-claim.md
```

Add anything the agent must not imply or claim.

Examples:

- Technologies you have only tried once.
- Old jobs you do not want emphasized.
- Metrics you cannot verify.
- Degrees or certifications you do not have.
- Legal or work authorization answers the agent must not infer.

## 5. Decide On Sensitive Answers

Open:

```text
profiles/sensitive-answers.template.json
```

Leave fields as `null` unless you want the agent to use a canonical answer.

`null` means:

```text
Stop and ask the user.
```

Sensitive fields include:

- Work authorization.
- Sponsorship.
- EEO.
- Veteran status.
- Disability status.
- Criminal history.
- Background checks.
- Legal agreements.
- Data processing consent.
- Salary expectations.
- Start date.

## 6. Install In Codex

Open Codex from the root of the folder.

Codex should automatically see:

```text
AGENTS.md
```

Paste:

```text
Read START_HERE.md and run the setup wizard. Operate in DRAFT_ONLY mode. Inspect the workspace, tell me what is complete, what is missing, and what I need to provide before a safe dry run.
```

The agent should report that it read:

- `START_HERE.md`
- `AGENTS.md`
- `.agents/skills/job-search-outreach-agent/SKILL.md`
- Profile files
- Tracker files
- Outreach template

## 7. Install In Claude Code

Open Claude Code from the root of the folder.

Claude Code should see:

```text
CLAUDE.md
```

Paste the contents of:

```text
RUN_THIS_FIRST_PROMPT.txt
```

If Claude starts searching before reporting readiness, stop it and paste:

```text
Stop. Reread START_HERE.md. Give me the readiness report first.
```

## 8. First Dry Run

Use this before any real outreach:

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

## 9. First Real Outreach Run

Use this after the dry run looks good:

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

## 10. Stage Simple Applications

Use only after you trust the dry-run behavior:

```text
Stage up to 2 simple ATS applications only if all required fields are known and truthful.
Upload the tailored resume if file upload works.
Stop before final submit.
If any sensitive/legal field is unknown, stop and add the role to manual review.
```

## 11. Submit Simple Applications

Use only with explicit authorization:

```text
Submit only simple applications where every required field is known, truthful, authorized, and logged.
Do not submit if there is CAPTCHA, account creation, unknown legal text, unknown sensitive answers, or any uncertainty.
Report each submission with company, role, URL, resume used, and timestamp.
```

## 12. Upload To GitHub

Create a new GitHub repository named:

```text
job-search-agent-wizard
```

Upload the folder contents.

Before making the repository public, review whether you have added private resume files, profile files, sensitive answers, or draft emails.

For a public template repository, keep only:

- Template profile files.
- Empty tracker CSVs.
- General instructions.
- No personal resume.
- No real emails.
- No sensitive answers.
