# 📘 Day 3 — Task: Organize Our Repo + Write Our Journal Entry

**Time window:** 6 hours (self-paced, spread across the day)
**Actual hands-on effort:**  the lightest day so far. This is
tidying and writing, not building.

---

## 🎯 Objective
Put Day 1 and Day 2's work into one clean repo folder, and write our first
engineering journal entry.

---

## ✅ Step-by-Step

### 1. Organize the Repo (30 min)
Arrange our files like this (rename/move, don't recreate):

```
week4-de-reflection/
├── README.md
├── day1/
│   ├── clean_sales.csv
│   └── flagged_issues.md
├── day2/
│   ├── diagrams/pipeline_architecture.png
│   └── README.md
└── engineering_journal.md
```

### 2. Write the Journal Entry (30–45 min)
Create `engineering_journal.md` and answer just these 3 questions,
2–3 sentences each:

```markdown
# Engineering Journal — Week 4

## Entry 1

**What surprised me this week?**
___ I was surprised by how much effort can go into fixing what looks like a small data issue. A negative qty value, for example, is not always just a technical error—it can have a business meaning. As a data engineer, I learned that I need to understand the data and its context before deciding how to fix it.

**What challenged me the most?**
___The most challenging part was deciding whether an issue should stop the pipeline or just be flagged. I had to think about the impact of bad data and whether the pipeline could safely continue. It also challenged me to separate the business decision from the technical implementation.

**What am I proud of?**
___ I am proud that I approached the data issue systematically instead of simply changing or deleting the problematic values. I focused on understanding the cause, considering the business meaning, and thinking about how the problem could be prevented at the source. This helped me see that good data engineering is not only about cleaning data, but also about building reliable processes.
```

---

## 📦 Deliverable
- Organized repo folder
- `engineering_journal.md` with all 3 questions answered

## 🧭 Definition of Done
- Files are in the folders shown above, nothing missing
- All 3 journal questions are answered honestly, in our own words
