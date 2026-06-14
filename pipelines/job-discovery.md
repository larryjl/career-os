# Pipeline: Job Discovery

**Goal:** Explore the market for a target role — find live listings, score them against your resume, and evaluate the top 3 in detail before deciding where to invest application effort.

**Skills used in order:** `/job-scout` → `/job-match` (top 3 results)

**Time estimate:** 10–15 minutes

---

## When to use this pipeline

- You're starting a job search and want to understand what's available
- You want to know your realistic match score before committing to applications
- You're comparing multiple roles or companies before deciding where to focus
- You want market data (salaries, demand trends) before negotiating

---

## Execution Steps

### Step 1 — Find and Rank Jobs (`/job-scout`)

**Trigger:** `"Run job discovery pipeline for [role] in [location]"`

Claude runs `/job-scout` and outputs a ranked table of 8–12 live job listings, scored against your master resume, sorted by match score.

The table includes: score, colour indicator (🟢🟡🟠🔴), job title, company, location, work type, salary (if listed), date posted, apply link.

**Pause point:**
> "Here are your top matches. I'll now run a full evaluation on the top 3. Ready? (yes / pick different jobs: #N #N #N)"

---

### Step 2 — Evaluate Top 3 (`/job-match`)

Claude runs `/job-match` on jobs #1, #2, and #3 in sequence. For each:

- Full A–E evaluation
- Match score /100
- Go/no-go recommendation

**Pause between each job:**
> "✅ Evaluation complete — [Job Title] at [Company]: [X]/100 [🟢/🟡/🟠/🔴]
>  Continue to next job? (yes / skip / stop)"

---

## Output Summary

```
─────────────────────────────────────────
✅ Job Discovery Pipeline Complete

Role searched: [role] | Location: [location]
Jobs found: [N] | Evaluated: 3

  #1 [Job Title] at [Company]
     Score: [X]/100 🟢  |  [Salary]  |  [Remote/Hybrid]
     Recommendation: [one sentence]

  #2 [Job Title] at [Company]
     Score: [X]/100 🟡  |  [Salary]  |  [Remote/Hybrid]
     Recommendation: [one sentence]

  #3 [Job Title] at [Company]
     Score: [X]/100 🟠  |  [Salary]  |  [Remote/Hybrid]
     Recommendation: [one sentence]

Market insight:
  Salary range for [role] in [location]: $[X] – $[Y]
  Demand trend: [growing / stable / shrinking]

Next steps:
  → Run "full application pipeline" for your top pick
  → Or: /tailored-resume-generator #1 to start applying immediately
─────────────────────────────────────────
```
