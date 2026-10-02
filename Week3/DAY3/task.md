# Day 3 Task: Probability, Sampling & Fairness ( 6 Hours )

> **Dataset:** Capital Bikeshare — one month is enough (pick July, August, or September 2023)
> **Tool:** Google Sheets
> **Effort:** ⭐ Light
> **Time:** ~4 hours

---

## 🗺️ Your Task Map for Today

| Part | Activity | Time |
|------|----------|------|
| Part 0 | Prep a small sample dataset | 30 min |
| Part 1 | Probability from real counts | 50 min |
| Part 2 | Independent vs dependent events | 40 min |
| Part 3 | The sampling experiment | 60 min |
| Part 4 | Simulate a biased sample | 45 min |
| Part 5 | Reflection & write-up | 35 min |

---

## 📦 Part 0 — Prep a Small Sample Dataset (30 min)

Download **one** month (e.g. July 2023) from [capitalbikeshare.com/system-data](https://capitalbikeshare.com/system-data).

1. Open the CSV file.
2. Copy the first **1,500 rows** (excluding header) into a new tab called `all_data`.
3. Keep the header row.

> 💡 We're using a smaller slice on purpose — it's plenty to see the same patterns without a giant sheet slowing you down.

Add your `duration_min` column using the Day 2 formula, and apply the same filter (1–180 minutes only). Note your clean row count.

---

## 🎲 Part 1 — Probability from Real Counts (50 min)

Probability = (number of times something happened) ÷ (total things that could have happened). This is **empirical probability** — from real data, not theory.

### Step 1 — Create a `probabilities` tab

In `A1` type `Total Trips`, and in `B1`:
```
=COUNTA(all_data!A:A)-1
```

### Step 2 — Fill just three probabilities

| Event | Count Formula | Count | Probability |
|-------|--------------|-------|-------------|
| Casual rider | `=COUNTIF(all_data!L:L,"casual")` | | |
| Member rider | `=COUNTIF(all_data!L:L,"member")` | | |
| Electric bike | `=COUNTIF(all_data!B:B,"electric_bike")` | | |


<img width="522" height="211" alt="image" src="https://github.com/user-attachments/assets/45973732-c322-48ae-af78-112280c09dc0" />

Format the Probability column as a percentage.

### Step 3 — Sanity check

Does P(casual) + P(member) = 100%? Write one sentence on why or why not.

**yes that is 1 ( 100% )**
---

## 🔗 Part 2 — Independent vs Dependent Events (40 min)

Two events are **independent** if knowing one tells you nothing about the other.

### Step 1 — One comparison only

Calculate:

| Probability | Formula |
|------------|---------|
| P(electric \| casual) | `=COUNTIFS(all_data!L:L,"casual",all_data!B:B,"electric_bike")/COUNTIF(all_data!L:L,"casual")` |
| P(electric \| member) | `=COUNTIFS(all_data!L:L,"member",all_data!B:B,"electric_bike")/COUNTIF(all_data!L:L,"member")` |

Both probabilities are approx 33% and that means 1 out of 3 person using electric bikes.


### Step 2 — The independence test

Compare the two numbers. Answer in 2–3 sentences: are casual riders and members equally likely to pick electric bikes, or is there a real difference? Would you call these two variables independent or dependent?

*(Skip the "your own investigation" pair this round — one comparison is enough to get the concept.)*

---

## 🔬 Part 3 — The Sampling Experiment (60 min)

*If we can't look at all 1,500 trips, how small a sample can we trust?*

### Step 1 — Record the "true" population value

From `all_data`, note just one ground-truth number:

| Metric | True Value (all rows) |
|--------|--------------------------|
| % casual riders |  35% 

35% Casual riders


### Step 2 — Randomize once

Add column `N` called `random_number`: `=RAND()`. Fill down, then Paste Special → values only to freeze it.

Sort `all_data` by column N (ascending).

We did the sorting based on random number and also based on duration.

<img width="1450" height="644" alt="image" src="https://github.com/user-attachments/assets/f45bba62-5d9c-4c8d-bb4c-defddb299681" />


### Step 3 — Compare just two sample sizes

| Sample Size | % Casual |
|-------------|----------|
| True (all) | |
| n = 20 (rows 2–21) | |
| n = 200 (rows 2–201) | |

Use: `=COUNTIF(all_data!L2:L21,"casual")/20*100` (adjust range for n=200).

*(No chart required this round — the two numbers are enough to make the point.)*

### Step 4 — One question

In 2–3 sentences: what's the relationship between sample size and accuracy, based on what you just saw?

---

## 🚨 Part 4 — Simulate a Biased Sample (45 min)

A large sample isn't automatically trustworthy.

### The scenario

A researcher only looks at trips starting between **7–9 AM**.

### Step 1 — One helper column

Add column `O` called `hour_of_day`:
```
=HOUR(TIMEVALUE(MID(C2,12,8)))
```
Fill down.

### Step 2 — Create the biased sample

Use Data → Create a filter on `all_data`. Filter column `O` to show only 7 and 8.

Calculate just one metric on the filtered rows:

| Metric | Biased Sample (7–9 AM) | True Value (all data) |
|--------|-------------------------|-------------------------|
| % casual | | |

### Step 3 — Interpret the bias

Answer in 3–4 sentences: how does % casual differ between the biased sample and the full dataset, and who is likely missing from the 7–9 AM window?

---

## ✍️ Part 5 — Reflection & Write-Up (35 min)

In a tab called `day3_writeup`, answer **one** question:

**Random vs biased:** In your own words (3–4 sentences), explain the difference between a random sample and a biased sample to someone who has never studied statistics. Use an example from this dataset.

---

## ✅ Deliverables Checklist

- [ ] `all_data` tab with ~1,500 rows and `duration_min` column
- [ ] `probabilities` tab with 3 probabilities + sanity check
- [ ] Independence comparison (electric bike vs rider type) completed
- [ ] True % casual recorded
- [ ] `random_number` column added and frozen
- [ ] Sampling table filled for n=20 and n=200
- [ ] Sample-size accuracy question answered
- [ ] Helper column (hour) added
- [ ] Biased sample comparison (% casual only) complete
- [ ] Bias interpretation question answered
- [ ] Write-up in `day3_writeup` (1 reflection question)

---

> A *random* sample — even a small one — is more trustworthy than a large *biased* one.
