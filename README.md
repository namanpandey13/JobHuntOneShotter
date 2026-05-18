# JobHuntOneShotter

An ethical, contact-first job-search wizard for Claude Code or Codex.

This project helps an agent run a careful job-search workflow:

- inspect your profile and resume facts
- find or review real roles
- score role fit
- verify direct public recruiter or hiring-team contacts
- tailor resumes only from truthful facts
- create Gmail drafts or local draft files
- stage simple applications only with approval
- log submitted, staged, drafted, skipped, and manual-review work separately

It is intentionally conservative. The default mode is `DRAFT_ONLY`.

## Quick Start For Non-Technical Users

1. Download this repo as a ZIP from GitHub.
2. Unzip it.
3. Open the folder in Claude Code or Codex.
4. Copy `profiles/profile.template.json` to `profiles/profile.json`.
5. Fill in `profiles/profile.json`.
6. Put your resume in `resumes/`.
7. Edit `profiles/do-not-claim.md`.
8. Paste the contents of `RUN_THIS_FIRST_PROMPT.txt` into Claude Code or Codex.
9. Wait for the readiness report.
10. Start with a dry run.

## Important Safety Rules

- Do not send emails automatically.
- Do not submit applications automatically.
- Do not guess recruiter emails.
- Do not invent resume claims.
- Do not answer legal or sensitive questions unless the answer is explicitly provided.
- Do not treat generic inboxes like `jobs@`, `careers@`, or `info@` as direct person contacts.
- Use Gmail drafts or local draft files first.

## First Prompt

```text
Read START_HERE.md first and run the setup wizard exactly as written.

Operate in DRAFT_ONLY mode unless I explicitly authorize another mode.

Before doing any job-search work, inspect the workspace and give me a readiness report.
```

## Where Things Go

```text
profiles/profile.json              private candidate profile
profiles/do-not-claim.md           claims the agent must not make
profiles/sensitive-answers.json    optional private sensitive answers
resumes/                           local resumes, not committed
drafts/                            local outreach drafts, not committed
trackers/                          public template trackers
```

## Public Repo Warning

Do not commit private resumes, real sensitive answers, real draft emails, or personal application records to a public GitHub repo.

