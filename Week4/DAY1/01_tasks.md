# 📘 Day 1 — Task: Pipeline Reflection & Cleanup

---

## 🎯 Goal

We've been handed a raw sales export, `data/raw_lemonade_sales.csv` (20 rows). It's messy — like most real-world data. Today we clean it by hand, document every decision we make, and think about what a pipeline should automate versus flag for a human.

---

## 📂 Materials

- `data/raw_lemonade_sales.csv` — source file (20 rows)
- `data/customers.csv` — reference table for customer name/email lookups
- `data/products_reference.csv` — reference table for product prices

---

## 🧩 Task

### 1. Find the Issues

We go through `raw_lemonade_sales.csv` row by row. For each problem we find, we log:

- Row number
- What's wrong
- Which category it falls into: **Completeness**, **Consistency**, **Uniqueness**, **Validity**, or **Referential integrity**

### 2. Decide What to Do About Each Issue

For every issue found, we write down:

- Our decision (fix it, flag it, drop it, keep it as-is)
- Our reasoning — why that decision and not another one

Some things to think about as we go:

- Should a missing field be recovered from a reference table, or left as `Unknown`? We should reciver like we did for email and customer name
- Should a duplicate be dropped, or is it actually two separate real events? Yes dropped
- Should an outlier or unusual value be deleted, or kept and flagged for someone else to confirm? Can not be delted but mentioend as business to be confirmed





#### Cleanded raw data

<img width="829" height="359" alt="image" src="https://github.com/user-attachments/assets/f041be2f-d338-4400-8714-31c0b7719a06" />


### 3. Summarize Our Results

We report:

- Starting row count 20
- Final clean row count 18
- How many rows we touched/corrected vs. how many were clean on arrival : 
   - 9 out of 20 ( 45 % of the rows corrected)
- If this pipeline ran daily, what's the *first* check we'd automate — and why?
   - data format validation or data type check - this should be the 1st thing to check.

### 4. Reflection Prompts

We answer before or after cleaning — whichever helps us think it through:

1. **Hard fail vs. soft fail** — Which of the issues we found should cause a pipeline to stop and alert someone immediately? Which should just be logged and flagged while the pipeline keeps running? What's the difference?

- Hard fail = stop the pipeline. Use this when continuing could produce, publish, deploy, or propagate something unsafe, invalid, or materially wrong. It should alert an owner immediately.
- Soft fail = keep going, but record the problem. Use this when the issue is useful to investigate but the pipeline can safely produce a result without it.

2. **Who owns the negative-quantity decision?** — If we find a negative `qty` value, is that a data engineering problem or a business decision? Who should actually decide what it means?

- Data engineering: Implements the technical treatment once that meaning is established: reject it, transform it, map it to a return transaction, or allow it through.

3. **What should the source system fix at entry?** — If we could change one thing about how this data gets entered in the first place (before it ever reaches us), what would it be, and why would that be more valuable than cleaning it after the fact?

- Prevents bad data at the source rather than repeatedly fixing symptoms.
- Preserves meaning. By the time the data reaches us, we may not know whether -2 means a typo, a return, or an adjustment.
- Reduces downstream complexity. Every consumer doesn't need its own cleaning rule.
- Makes errors visible to the person who can actually correct them, while the context is still available.
- Improves every downstream system, not just our pipeline.
### 5. Deliverable

We produce a cleaned file: `data/clean_sales.csv`, including a `data_quality_flag` column that documents every row we touched and why.
