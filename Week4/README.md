# 📅 Week 4: Documentation, Reflection & Portfolio Building

## 🧠 This Week, We'll Explore
- How to use **diagramming tools** (draw.io / Canva) to document data pipelines
- How to structure and document our projects on **GitHub**
- Telling a compelling **data pipeline story** — from raw source to clean output
- Identifying our **strengths and areas for improvement** as data engineers
- Writing about our **first-month experience**
- Reviewing all the **key terms and concepts** we've learned so far, including how **Spark, Kafka, and Google Sheets** fit together in a real pipeline
- Turning our week's work into a short, presentable **Canva deck**

---

## 📊 Effort Chart: Week 4 Overview

| Day    | Title                                | Description                                                             | Effort Level  |
|--------|----------------------------------------|---------------------------------------------------------------------------|----------------|
| Day 1  | Pipeline reflection & cleanup          | Revisit, clean, and re-document a past data pipeline                      | ⭐⭐⭐ Medium |
| Day 2  | Architecture & pipeline diagramming    | Visualize our pipeline (source → transform → load) in draw.io/Canva       | ⭐⭐⭐ Medium |
| Day 3  | GitHub + Data Engineering Journal      | Organize our repo properly, write our first journal entry                 | ⭐ Very Light |
| Day 4  | DE portfolio intro                     | Identify interests, build confidence, and plan our next project           | ⭐ Very Light |
| Day 5  | Canva & presentation guidelines        | Turn the week's work into a short, clean presentation                     | ⭐ Very Light |
| Extra  | Spark, Kafka & Sheets concepts check   | Reference material + basic questions on how these tools connect           | ⭐ Very Light |

💡 This week is about **reviewing, documenting, and reflecting** — helping us
communicate our pipelines clearly and prepare our portfolio for future
projects. Effort tapers down through the week on purpose — Days 3–5 are
meant to be light wrap-up work, not new building.

---

## 📘 Weekly Skeleton

### 📅 Day 1: Pipeline Reflection & Cleanup
`day1/01_concepts.md` · `day1/01_task.md` · `day1/01_task_SOLUTION.md`

- 🧪 We revisit a messy multi-source dataset (`raw_lemonade_sales.csv` +
  `customers.csv` + `products_reference.csv` + `daily_weather.csv`)
- 🔍 We apply what we've learned: null handling, schema validation,
  deduping, outlier checks, referential integrity
- 🧠 We answer reflection questions: hard fail vs. soft fail, who owns a
  judgment call, what the source system should fix at entry
- ✅ We clean it, validate it, and summarize what changed
- 🎯 **Optional lighter alternates:** `day1/02_task_pipeline_data_quality_audit.md`
  (fill-in audit report) and `day1/03_task_schema_mapping.md` (source-to-staging
  schema mapping table) — same dataset, different skill focus

---

### 📅 Day 2: Pipeline Architecture & Documentation
`day2/01_concepts.md` · `day2/01_task.md` · `day2/01_task_SOLUTION.md`

- 🎨 We use draw.io or Canva to diagram our pipeline: source → staging →
  transform → load → output, using `day2/data/pipeline_stages.csv` as a guide
- 📊 We document the same pipeline from Day 1 — nothing new to clean
- 💬 We write a short explanation for each stage, in our own words
- ✅ We export the diagram and embed it in a `README.md`
- 🎯 **Optional lighter alternates:** `day2/02_task_readme_completeness_check.md`
  (documentation review checklist) and `day2/03_task_data_lineage_trace.md`
  (trace 3 orders from raw → clean)

---

### 📅 Day 3: GitHub + Engineering Journal
`day3/01_concepts.md` · `day3/01_task.md` · `day3/01_task_SOLUTION.md`

- 📁 We organize Day 1 and Day 2's work into one clean repo folder
- 🧾 We write our **first Engineering Journal entry**:
  - What surprised me this week?
  - What challenged me the most?
  - What am I proud of?

---

### 📅 Day 4: Personal Growth & DE Project Ideas
`day4/01_concepts.md` · `day4/01_task.md` · `day4/01_task_SOLUTION.md`

- 🧠 We add a second journal entry: what felt most like "us," and what
  domain we want to work with next
- 🎯 We draft one small, *finishable* project idea — scoped down on
  purpose, reusing a skill we already practiced this week
- ✅ We save it as `next_project_idea.md`

---

### 📅 Day 5: Canva & Presentation Guidelines
`day5/01_concepts.md` · `day5/01_task.md`

- 🎨 Simple Canva guidelines: template-first, one idea per slide, minimal
  text, consistent colors and fonts
- 🗣️ Presentation guidelines: open with what the pipeline does, follow its
  actual flow, show the diagram instead of describing it, end with one takeaway
- ✅ We build a 5-slide deck reusing Day 1's problem, Day 2's diagram and
  before/after example, and Day 3's journal takeaway — under 3 minutes to present

---

### 📚 Extra: Spark, Kafka & Google Sheets Concepts
`reference/concepts.md` · `reference/task.md` · `reference/task_SOLUTION.md`

- 🧠 Extended data engineering glossary: streaming vs. batch, data lake vs.
  warehouse vs. lakehouse, Kafka terms (topics, partitions, offsets, schema
  registry), Spark terms (DataFrames, lazy evaluation, shuffles, watermarking)
- 🔗 How Kafka (ingestion), Spark (transformation), and Google Sheets
  (lightweight reporting) work together — with a worked example scaling
  our lemonade pipeline up to a real streaming architecture
- ✅ A basic concepts-check task: term matching, short answer, true/false

---

## 🗂️ Actual Repo Structure

```
week4-de-reflection/
├── README.md
├── day1/
│   ├── 01_concepts.md
│   ├── 01_task.md
│   ├── 01_task_SOLUTION.md
│   ├── 02_task_pipeline_data_quality_audit.md
│   ├── 03_task_schema_mapping.md
│   └── data/
│       ├── raw_lemonade_sales.csv
│       ├── customers.csv
│       ├── products_reference.csv
│       ├── daily_weather.csv
│       └── clean_sales_SOLUTION.csv
├── day2/
│   ├── 01_concepts.md
│   ├── 01_task.md
│   ├── 01_task_SOLUTION.md
│   ├── 02_task_readme_completeness_check.md
│   ├── 02_task_readme_completeness_check_SOLUTION.md
│   ├── 03_task_data_lineage_trace.md
│   ├── 03_task_data_lineage_trace_SOLUTION.md
│   └── data/
│       ├── pipeline_stages.csv
│       ├── raw_lemonade_sales.csv
│       └── clean_sales.csv
├── day3/
│   ├── 01_concepts.md
│   ├── 01_task.md
│   └── 01_task_SOLUTION.md
├── day4/
│   ├── 01_concepts.md
│   ├── 01_task.md
│   └── 01_task_SOLUTION.md
├── day5/
│   ├── 01_concepts.md
│   └── 01_task.md
├── reference/
│   ├── concepts.md
│   ├── task.md
│   └── task_SOLUTION.md
├── diagrams/
│   └── pipeline_architecture.png
└── engineering_journal.md
```

---

## ✅ How to Use This Week
1. Each day, read `01_concepts.md` first — it's short and sets up the
   vocabulary for that day's task.
2. Complete `01_task.md`. Days 1 and 2 have optional lighter alternate
   tasks if we want extra practice on a specific skill.
3. Check our own work against the matching `_SOLUTION.md` file — these
   are model answers with reasoning, not just final numbers.
4. By Day 5, everything produced across the week feeds directly into the
   final presentation — nothing needs to be rebuilt from scratch.
