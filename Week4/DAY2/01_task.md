# 📘 Day 2 — Task: Pipeline Architecture & Documentation

**Time window:** 6 hours (self-paced, spread across the day)
**Actual hands-on effort:** ~2 hours — this is a lighter day. We're
documenting a pipeline that already exists (from Day 1), not building
anything new.
**Files needed:** `data/pipeline_stages.csv`, `data/raw_lemonade_sales.csv`,
`data/clean_sales.csv`

---

## 🎯 Objective
Turn yesterday's cleanup work into a diagram and a short written explanation
that someone else could follow without re-doing our thinking.

---

## ✅ Step-by-Step

### 1. Draw the Pipeline (45 min)
- Open draw.io or Canva.
- Using `data/pipeline_stages.csv` as our guide, draw 6 boxes in order,
  connected by arrows: Ingestion → Standardize → Handle Missing Values →
  Deduplicate → Validate → Load.
- Label each box with the stage name only — keep it clean and readable.

  <img width="922" height="62" alt="data pipeline drawio (1)" src="https://github.com/user-attachments/assets/0d3f2841-2a15-495a-970d-e045a8f1d0ec" />


### 2. Explain Each Stage (30 min)
- For each of the 6 boxes, write 1–2 sentences (not more) explaining what
  happens there, in our own words — reuse the `description` column in
  `pipeline_stages.csv` as a starting point, not a copy-paste.


 * Ingestion: We load the raw data as it is.. It is same as its found in the sources systems
 * Standardize: We fix inconsistent data ( ex- date `06/01/2024` → `2024-06-01`)
 * Handle missing values: We recover missing customer_name or customer_email.
 * Deduplicate: We remove rows that represent the same real-wprld order logged more than once.
 * Validate: We check every product and customer in our data has a matching record in the reference tables.
 * Load: We write final clean dataset to a differnt sheet of the excel.
   

### 3. Export & Attach (15 min)
- Export the diagram as a PNG.
- Save it as `diagrams/pipeline_architecture.png`.
- Add it to a `README.md` under a "Pipeline Overview" heading, with our
  stage explanations underneath.

### 4. Reflect (15 min)
- Answer the 2 reflection prompts from `01_concepts.md` directly in the
  README, under a "Notes" section.

---

## 📦 Deliverables
- `diagrams/pipeline_architecture.png`
- `README.md` with the diagram embedded + stage explanations + reflection answers

---

## 🧭 Definition of Done
- Diagram shows all 6 stages in the correct order with arrows
- Every stage has a short, original explanation (not copy-pasted)
- Diagram is actually embedded in the README, not just linked
- Reflection prompts are answered
