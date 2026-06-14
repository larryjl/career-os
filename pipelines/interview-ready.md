# Pipeline: Interview Ready

**Purpose:** Prepare thoroughly for an upcoming interview — prep kit then live practice.
**Skills chained:** /interview-prep → /mock-interview
**Estimated time:** 20–30 minutes

---

## Input

- Job description or rank number from a previous scout result
- (Optional) Interview date — helps calibrate urgency

---

## Execution Steps

### Step 1 — Interview Prep Kit

1. Read `skills/interview-prep/SKILL.md`
2. Read `profile/master-resume.md`
3. Run /interview-prep for the specified job
4. Output: 10 questions + 3 STAR+R frameworks + 5 ask-them questions + checklist
5. Save to `outputs/interview-notes/prep_[company]_[role]_[date].docx`
6. Ask: "Ready to run a live mock interview now? (yes / later)"

### Step 2 — Mock Interview (if yes)

1. Read `skills/mock-interview/SKILL.md`
2. Pull the 10 questions from Step 1 — do not regenerate
3. Run /mock-interview using those questions
4. 5 questions, one at a time — wait for answers, give feedback per question
5. Output the full debrief at the end
6. Save to `outputs/interview-notes/mock_debrief_[company]_[role]_[date].md`

---

## Completion Output

```
✅ Interview Ready — [Job Title] at [Company]

Prep Kit:   outputs/interview-notes/prep_[filename].docx
Debrief:    outputs/interview-notes/mock_debrief_[filename].md

Overall Readiness: [Ready / Nearly Ready / More Prep Needed]
Top thing to work on before the real interview: [from debrief]

Tip: Re-run /mock-interview the night before. The second session is always stronger.
```
