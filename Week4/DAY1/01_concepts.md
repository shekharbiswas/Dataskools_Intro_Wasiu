# 📘 Day 2 — Concepts: Pipeline Architecture & Documentation

## 🎯 Goal for Today
Yesterday we cleaned data by hand. Today we step back and **draw and
document** the pipeline we just built — the skill that lets someone else
(or future-us) understand a pipeline without reading every line of it.

---

## 🧠 Core Data Engineering Terms (Day 2 Glossary)

| Term | Plain-English Meaning |
|---|---|
| **Pipeline architecture diagram** | A visual map of how data moves: source → staging → clean → output. |
| **Data lineage** | The traceable path of a single piece of data from where it entered to where it ends up — which lets us answer "where did this number come from?" |
| **Ingestion** | The step where raw data first enters the pipeline. |
| **Transformation** | Any step that changes, cleans, joins, or reshapes data. |
| **Sink / Output** | Where the finished data lands — a report, a dashboard, another system. |
| **Documentation debt** | When a pipeline works but nobody wrote down how or why — it becomes risky to change. |
| **README** | The first file anyone opens in a repo — should explain what the pipeline does without reading the code. |
| **Runbook** | A step-by-step doc for operating or troubleshooting a pipeline when something breaks. |
| **Data flow direction** | Diagrams should show data moving one way (usually left→right or top→bottom) so it's easy to follow. |
| **Stakeholder-readable** | Documentation clear enough for a non-engineer (like a business analyst) to understand what the data means. |

---

## 🔍 Today's Materials
We're documenting the *same* pipeline from Day 1 — nothing new to clean.

- `data/raw_lemonade_sales.csv` — source (bronze)
- `data/clean_sales_SOLUTION.csv` — staging/clean output (silver) — copied over from Day 1
- `data/pipeline_stages.csv` — a short reference table listing each stage of the pipeline, used for the diagram

---

## 🧩 The Mental Model

```
[raw_lemonade_sales.csv]
        ↓  (ingestion)
[staging: clean + standardize]
        ↓  (transform: dates, casing, dedup, validation)
[clean_sales.csv]
        ↓  (load)
[reporting / dashboard]
```

A good diagram doesn't need to be fancy — it needs to answer 3 questions at
a glance: **where did the data start, what happened to it, and where did it
end up.**

---

## ❓ Reflection Prompts (answer before starting the task)

1. If a new teammate joined tomorrow, what's the *one* diagram or doc that
   would save them the most time?
2. What's the difference between a README and a runbook — when would we
   reach for each one?
