# 📘 Task A — README Completeness Check

**Time window:** 6 hours (self-paced, spread across the day)
**Actual hands-on effort:** ~1.5 hours — this is a checklist task. We're
reviewing, not writing new content from scratch.
**Files needed:** `data/pipeline_stages.csv`, our `README.md` from the main task (if completed)

---

## 🎯 Objective
Act as a reviewer checking whether a pipeline's documentation is actually
good enough for a new teammate to use — a real step in most data teams
before a project is considered "done."

---

## 🧾 The Checklist (fill this in)

Create `readme_review.md` with this checklist already provided:

```markdown
# README Completeness Review

Reviewed file: ___
Reviewed by: ___

| Check | Present? (Y/N) | Notes |
|---|---|---|
| States what the pipeline does in 1–2 sentences at the top | ___ | ___ |
| Lists all input/source files | ___ | ___ |
| Lists the output file(s) | ___ | ___ |
| Includes a diagram or visual of the pipeline flow | ___ | ___ |
| Explains each pipeline stage in plain language | ___ | ___ |
| Mentions known data quality issues or limitations | ___ | ___ |
| Would a non-technical teammate understand what this pipeline is for? | ___ | ___ |

## Overall Verdict
🟢 Ready to share   🟡 Needs minor additions   🔴 Needs rework

## Top 2 Improvements
1. ___
2. ___
```


| Check | Present? (Y/N) | Notes |
|---|---|---|
| States what the pipeline does in 1–2 sentences at the top | Y | Title + short framing is present but could be one explicit sentence, not just a title |
| Lists all input/source files | N | raw_lemonade_sales.csv is implied by the diagram but never explicitly named as an input in a "Sources" section |
| Lists the output file(s) | Y | clean_sales.csv is named in the Load stage |
| Includes a diagram or visual of the pipeline flow | Y | Diagram embedded under Pipeline Overview |
| Explains each pipeline stage in plain language | Y | All 6 stages have a 1-sentence explanation |
| Mentions known data quality issues or limitations | N | Doesn't mention the flagged rows (refund, outlier, unmatched customer) from Day 1 — a new teammate wouldn't know these exist without opening flagged_issues.md separately |
| Would a non-technical teammate understand what this pipeline is for? | Y | Plain language throughout, no jargon left unexplained |
---

## ✅ How to Work Through It
1. Go row by row through the checklist against our own README (or a
   sample one if we haven't completed the main task yet).
2. Be honest — this is meant to catch documentation gaps, not to pass
   everything automatically.
3. Only the last two sections require original thinking.

## 📦 Deliverable
- `readme_review.md` (filled-in checklist above)

## 🧭 Definition of Done
- Every row has a Y/N and a short note
- Verdict is chosen and matches the pattern of Y/N answers
- Top 2 improvements are specific and actionable
