# Day 2 Task: Measuring & Describing the Rides ( 6 Hours )

> **Dataset:** Same Google Sheet from Day 1 (September 2023 trip data)
> **Tool:** Google Sheets
> **Effort:** ⭐ Light
> **Time:** ~6 hours

---

## 🗺️ Your Task Map for Today

| Part | Activity | Time |
|------|----------|------|
| Part 1 | Calculate trip duration | 50 min |
| Part 2 | The five-number summary | 65 min |
| Part 3 | Visualise the distribution | 65 min |
| Part 4 | Compare members vs casual riders | 70 min |
| Part 5 | Outliers — who are those riders? | 50 min |
| Part 6 | Interpret & write up | 60 min |

---

## 📐 Part 1 — Calculate Trip Duration (50 min)

### Step 1 — Add a duration column

1. Name the first empty column (should be `M`) `duration_min`.
2. In `M2`, type:

```
=((DATEVALUE(MID(D2,1,10)) + TIMEVALUE(MID(D2,12,8))) - (DATEVALUE(MID(C2,1,10)) + TIMEVALUE(MID(C2,12,8)))) * 1440
```

<img width="1606" height="502" alt="image" src="https://github.com/user-attachments/assets/d73a40c7-c09c-455d-8204-0ad9be501353" />

3. Fill down for all rows (`Ctrl+Shift+End` then `Ctrl+D`).

> ⚠️ If the sheet slows down, work with the first 50,000 rows only.

### Step 2 — Remove bad data

1. Data → Create a filter
2. Filter `duration_min` to show only rows **greater than 1 and less than 180**
3. Note how many rows remain.

<img width="1818" height="948" alt="image" src="https://github.com/user-attachments/assets/5bdfdafa-900a-4479-b890-ae41ceec84c9" />

---

## 📏 Part 2 — The Five-Number Summary (65 min)

Create a tab called `stats_summary`.

### Step 1 — Build this table (4 stats instead of 6)

| Statistic | Formula | Your Value |
|-----------|----------------------------------------|------------|
| Count (clean trips) | `=COUNTA(Sheet1!M2:M500000)-COUNTBLANK(Sheet1!M2:M500000)` | |
| Median | `=MEDIAN(Sheet1!M2:M500000)` | |
| Mean (Average) | `=AVERAGE(Sheet1!M2:M500000)` | |
| Standard Deviation | `=STDEV(Sheet1!M2:M500000)` | |

> 💡 Adjust `M500000` to your actual last row (check with `Ctrl+End`).

<img width="696" height="370" alt="image" src="https://github.com/user-attachments/assets/541f66de-d3df-4e20-9c9e-3c854d291aae" />

### Step 2 — Mean vs median

1. Is the mean higher or lower than the median? By how many minutes?
2. Would you tell a city planner the "typical" trip duration is the mean or the median? Write 1–2 sentences.

*(Skip the separate spread-ratio calculation this round — the mean/median gap already tells you the data is skewed.)*

---

## 📈 Part 3 — Visualise the Distribution (65 min)

Create a tab called `histogram_data`.

### Step 1 — Frequency table (3 bins instead of 5)

| Bin Label | Lower Bound | Upper Bound | Count |
|-----------|-------------|-------------|-------|
| 0–15 min | 0 | 15 | |
| 15–45 min | 15 | 45 | |
| 45–180 min | 45 | 180 | |

```
=COUNTIFS(Sheet1!M:M, ">"&B2, Sheet1!M:M, "<="&C2)
```

### Step 2 — Make a bar chart

Select `Bin Label` and `Count` → Insert → Chart → Bar chart. Title: `"Trip Duration Distribution — September 2023"`.

### Step 3 — Describe what you see

1. Which bin has the most trips?
2. Is the distribution roughly symmetric or does it have a long tail on the right?

---

## 👥 Part 4 — Compare Members vs Casual Riders (70 min)

### Step 1 — Comparison table (2 stats instead of 3)

| Statistic | Members | Casual Riders |
|-----------|---------|---------------|
| Count | `=COUNTIF(L:L,"member")` | `=COUNTIF(L:L,"casual")` |
| Mean Duration | `=AVERAGEIF(L:L,"member",M:M)` | `=AVERAGEIF(L:L,"casual",M:M)` |

*(Skip the "% of trips > 30 min" split this round.)*

- the Count Member is 77, and the count of casual is 25
- The Mean Duration of Member is 14.50572391, and Mean Duration of Casual rider is 12.22533333

### Step 2 — Reuse your existing chart

Instead of building a second histogram, just compare the two mean durations directly — no new chart needed this round.

### Step 3 — Answer these questions

1. Which group has a higher mean duration? By how many minutes?
2. If you were setting per-minute pricing after the first 30 minutes, which group would you charge more — and does your data support that?

---

## 🚨 Part 5 — Outliers: Who Are Those Riders? (50 min)

### Step 1 — Count extreme trips

| Question | Formula | Answer |
|----------|---------|--------|
| Trips over 60 min | `=COUNTIFS(M:M,">"&60)` | |

### Step 2 — Effect of outliers on the mean

Filter to trips ≤ 60 min only, recalculate `AVERAGE`. How much does the mean drop?

Write one sentence: *"Outliers pull the mean [up/down] by approximately X minutes, which means..."*

### Step 3 — Interpretation

In 1–2 sentences: who do you think the longest-duration riders are, and what does that suggest about how the company should define a "successful" trip?

---

## ✍️ Part 6 — Interpret and Write Up (60 min)

In a tab called `day2_writeup`, write a short note of **~100 words** for a non-technical manager, covering:

- What the typical trip duration looks like (use the right stat!)
- How members and casual riders differ
- One limitation of this analysis

---

## ✅ Deliverables Checklist

- [ ] `duration_min` column added and filtered
- [ ] Five-number summary table complete (4 statistics)
- [ ] Mean vs median question answered with explanation
- [ ] Histogram frequency table built with COUNTIFS (3 bins)
- [ ] Bar chart created and labelled
- [ ] 2 distribution shape questions answered
- [ ] Member vs casual comparison table complete (2 statistics)
- [ ] 2 comparison interpretation questions answered
- [ ] Outlier count (1 formula) complete
- [ ] Outlier effect on mean calculated
- [ ] Day 2 write-up (~100 words, plain English)

---

## 💡 Bonus (if you finish early)

Add a column called `hour_of_day` using:
```
=HOUR(TIMEVALUE(MID(C2, 12, 8)))
```

Then build a frequency table of trip counts by hour (0–23) using COUNTIFS. Which hour has the most trips?

---

> The mean is a useful number — but it lies when data is skewed. Always look at the shape before trusting a single summary statistic.
