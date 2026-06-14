# Pipeline: Full Apply

**Purpose:** Take a single job from discovery to application-ready in one session.
**Skills chained:** /job-scout → /job-match → /tailored-resume-generator → /cover-letter-generator
**Estimated time:** 8–12 minutes per job

---

## Input

Provide one of:
- A role + location: "Product Manager, remote Canada"
- A job description (pasted directly)
- A rank number from a previous /job-scout result: "#1"

---

## Execution Steps

### Step 1 — Scout (skip if JD already provided)

If no JD is provided:
1. Read `skills/job-scout/SKILL.md`
2. Read `profile/master-resume.md`
3. Run /job-scout for the specified role + location
4. Output the ranked table
5. Ask: "Which job would you like to apply for? (Enter rank number or paste a different JD)"

### Step 2 — Match Evaluation

1. Read `skills/job-match/SKILL.md`
2. Run /job-match on the selected job
3. Output all 5 blocks (A through E) + score
4. If score is below 55, flag: "This role is a significant mismatch (score: X/100).
   Apply anyway? (yes / pick a different job)"
5. Confirm: "Score: [X]/100. Continue to resume? (yes / skip)"

### Step 3 — Tailored Resume

1. Read `skills/tailored-resume-generator/SKILL.md`
2. Run /tailored-resume-generator using the job description from Step 1/2
3. The ATS keywords from /job-match Block E should inform keyword selection
4. Generate and save the .docx to `outputs/resumes/`
5. Confirm: "Resume saved to [path]. Continue to cover letter? (yes / skip)"

### Step 4 — Cover Letter

1. Read `skills/cover-letter-generator/SKILL.md`
2. Run /cover-letter-generator using the same job description
3. Use the tailored resume from Step 3 as context for achievement selection
4. Generate and save the .docx to `outputs/cover-letters/`
5. Confirm: "Cover letter saved to [path]."

---

## Completion Output

After all steps, output this summary:

```
─────────────────────────────────────────
✅ Application Pack Ready — [Job Title] at [Company]

Match Score:   [X]/100 ([🟢/🟡/🟠/🔴])
Resume:        outputs/resumes/[filename].docx
Cover Letter:  outputs/cover-letters/[filename].docx

Next:
→ Run /interview-prep to prepare for the interview
→ Run /mock-interview to practise live when the interview is scheduled
─────────────────────────────────────────
```
