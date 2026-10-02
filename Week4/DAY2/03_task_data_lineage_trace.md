# 📘 Task B — Trace the Data Lineage

**Time window:** 6 hours (self-paced, spread across the day)
**Actual hands-on effort:** ~1.5 hours — a short tracing exercise, filling
in a table rather than building anything new.
**Files needed:** `data/raw_lemonade_sales.csv`, `data/clean_sales.csv`

---

## 🎯 Objective
Pick 3 individual rows and trace them from raw source all the way to the
clean output — practicing the habit of being able to answer "where did
this specific number come from?"

---

## 🧾 The Lineage Table (fill this in)

Create `lineage_trace.md` with this table already provided:

```markdown
# Data Lineage Trace — 3 Sample Orders

| order_id | Raw value(s) as they appeared | What changed and why | Final value in clean_sales.csv |
|---|---|---|---|
| 1002 | ___ | ___ | ___ |
| 1008 | ___ | ___ | ___ |
| 1017 | ___ | ___ | ___ |

## One thing I noticed tracing these
___
```

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/39f239c4-c580-4c17-b2ec-cc6b6b56bd46" />


| order_id | Raw value(s) as they appeared | What changed and why | Final value in clean_sales.csv |
|---|---|---|---|
| 1002 | order_date = 06/01/2024 | Date was in MM/DD/YYYY format while every other row used YYYY-MM-DD; standardized to ISO 8601 so dates sort and compare correctly | order_date = 2024-06-01 |
| 1008 | qty = 150 | Quantity is far outside the typical order size (1–5 units); notes field said "bulk order - check" so it wasn't deleted, just flagged for business confirmation rather than assumed to be an error | qty = 150 (unchanged), data_quality_flag = "outlier - flagged for business confirmation" |
| 1017 | unit_price = (blank) | Price was missing; looked up Mint Lemonade in products_reference.csv, which lists a standard_price of 3.0, and filled it in rather than dropping the row | unit_price = 3.0, data_quality_flag = "unit_price inferred from products_reference.csv" |


---

## ✅ How to Work Through It
1. Pick order `1002` in `raw_lemonade_sales.csv` — note its raw values.
2. Find the same `order_id` in `clean_sales.csv` — note what's different.
3. In one sentence, explain *why* it changed (refer back to Day 1's
   `flagged_issues.md` / solution if we have it).
4. Repeat for `1008` and `1017`.
5. Write one short observation at the bottom — anything that surprised us
   about how much a single row can change through a pipeline.

## 📦 Deliverable
- `lineage_trace.md` (filled-in table above)

## 🧭 Definition of Done
- All 3 rows are traced with raw value, change reason, and final value
- Each "what changed and why" is a real reason, not just "it was cleaned"
- Closing observation is included
