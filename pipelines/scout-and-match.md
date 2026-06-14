# Pipeline: Scout and Match

**Purpose:** Find the best jobs available right now and evaluate the top results
before spending time on applications.
**Skills chained:** /job-scout → /job-match (×N)
**Estimated time:** 5–10 minutes

---

## Input

- Role + location (optional — infers from resume if not provided)
- Number of top results to evaluate in depth (default: 3)

Example invocations:
- "Scout and match for Product Manager roles in Toronto"
- "Find AI Engineer jobs and evaluate the top 3"
- "Run scout-and-match" (infers from resume)

---

## Execution Steps

### Step 1 — Scout

1. Read `skills/job-scout/SKILL.md`
2. Read `profile/master-resume.md`
3. Run /job-scout for the specified role or infer from resume
4. Output the full ranked table
5. Announce: "Found [N] jobs. Running full evaluation on the top [3]..."

### Step 2 — Match Top N

For each of the top N ranked jobs (default 3, up to 5):

1. Read `skills/job-match/SKILL.md`
2. Run /job-match — output all 5 blocks (A–E) + score
3. Save match report to `outputs/reports/match_report_[company]_[role]_[date].md`
4. After each: "✅ [Job Title] at [Company] — Score: [X]/100. Continuing..."

### Step 3 — Comparison Summary

After all evaluations, output a comparison table:

```
─────────────────────────────────────────
📊 Match Summary — Top [N] Jobs

| Rank | Score | Job | Company | Recommendation |
|------|-------|-----|---------|----------------|
| 1 | 🟢 88/100 | [Title] | [Company] | Apply immediately |
| 2 | 🟡 74/100 | [Title] | [Company] | Apply — address gaps in cover letter |
| 3 | 🟠 62/100 | [Title] | [Company] | Stretch — apply if targeting growth |

Best pick: [Job Title] at [Company] — [one sentence on why]

─────────────────────────────────────────
Next:
→ Run /full-apply for your top pick to generate resume + cover letter
→ Run /tailored-resume-generator #1 to start the resume for rank 1
─────────────────────────────────────────
```
