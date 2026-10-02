# Day 1 Task: Think Like an Analyst ( 6 Hours )

> **Dataset:** [Capital Bikeshare System Data](https://capitalbikeshare.com/system-data)
> **Tool:** Google Sheets
> **Effort:** ⭐⭐ Light
> **Time:** ~6 hours

---

## 🗺️ Your Task Map for Today

| Part | Activity | Time |
|------|----------|------|
| Part 0 | Download & import data | 45 min |
| Part 1 | Explore the columns | 60 min |
| Part 2 | The Question Pyramid | 75 min |
| Part 3 | Spot the gaps | 60 min |
| Part 4 | First counts with COUNTIF | 60 min |
| Part 5 | Your Analyst Brief | 60 min |

---

## 📦 Part 0 — Get the Data into Google Sheets (45 min)

1. Go to [capitalbikeshare.com/system-data](https://capitalbikeshare.com/system-data)
2. Download **one month** of trip data — try September 2023 (`202309-capitalbikeshare-tripdata.csv`)
3. Open [sheets.google.com](https://sheets.google.com) → **File → Import → Upload** the CSV
4. In the import dialog: choose **"Replace spreadsheet"**, separator = **Comma**
5. Click Import

You should now see a spreadsheet with around 300,000–400,000 rows and these columns:

```
ride_id | rideable_type | started_at | ended_at |
start_station_name | end_station_name |
start_lat | start_lng | end_lat | end_lng | member_casual
```

> ⚠️ If Google Sheets warns you that the file is large, that is fine — just let it load.

**Checkpoint:** Count the rows. In an empty cell, type `=COUNTA(A:A)-1` (the `-1` removes the header). Write down your total trip count for the month.

---

## 🔍 Part 1 — Explore Every Column (60 min)

Before doing any analysis, spend time *reading* the data like a journalist reading a new document.

### Step 1 — Column glossary
For each column below, write in your own words what it contains and give one example value from your data:

| Column | What it means | Example value from your data |
|--------|--------------|------------------------------|
| `ride_id` | a unique identifier for each ride | E3573C008D481AD0|
| `rideable_type` | The type of ride used for the ride | electric_bike|
| `started_at` / `ended_at` | The date and time when the ride started and ended| started_date 2023-09-07 12:39:20, ended_date at 2023-09-07 12:49:32|
| `start_station_name` / `end_station_name` | The name of the station where the ride begans and end | start_station_name 7th & S St NW, end_station_name Columbus Circle / Union Station|
| `start_lat` / `start_lng` | The latitude and longitude coordinating of the starting location | start_lat 38.92, start_lng -77.03|
| `member_casual` | Indicates whether the person riding the bike is a registered member or a casual rider. | member |

### Step 2 — Spot unusual values
Scroll through 50–100 rows manually. Note anything that looks odd, empty, or surprising. Write down at least **2 observations.**

Examples of things to look for:
- Are there rows where `start_station_name` is blank?
   - yes there are 44935 blank station names
     
- Are there trips that seem to start and end at the same station?
  - Yes there are trips with same start and end station
  
- Do all `rideable_type` values look consistent?
   - yes as we have only 3 rideable types

- There are a lot rows where start_station_name is blank?
   - yes , there are roughly 40000 or more rows with start station blank
  
- There is no trip that start and end at the same time
- There is only classic and electric bike inside the rideable field, they look consistent
   - yes thats correct

### Step 3 — What are the unique values?

In a new sheet tab (name it `exploration`), use these formulas to find out the distinct values in two key columns:

**Unique rider types:**  
Click an empty cell and manually look through column `member_casual`. You should find only two values. Write them down.

- member
- casual

**Unique bike types:**  
Do the same for `rideable_type`. How many distinct bike types are there? Write them down.

- There are three distict bike types, which are:
  1. electric_bike
  2. classic_bike
  3. docked_bike
> 💡 You can sort a column (Data → Sort sheet → Sort by column) to group identical values together, making it easy to spot all unique entries.

---

## 🧩 Part 2 — The Question Pyramid (75 min) — Light Version

Good analysts don't start by calculating — they start by asking the *right questions*. The Question Pyramid has three levels: each level goes deeper. This round, do just one pass through each level instead of several.

### 📐 Level 1 — Descriptive: *What happened?*

These are questions the data can answer directly with counting or filtering. Write **1 of your own** descriptive question about this dataset.

Here's a starter example (do NOT just copy this — write your own):
- *"How many trips were taken by members vs casual riders?"*

**Your Level 1 question:**
1. 

<img width="663" height="408" alt="image" src="https://github.com/user-attachments/assets/1180005f-dda9-4357-9f46-0754615dccaf" />


---

### 🔎 Level 2 — Diagnostic: *Why might this be?*

Take that same question and go one level deeper. Write **1 possible explanation** for what you might find — before checking the data.

**Your question (from Level 1):**  
Possible explanation:
- 
Members are registered users so thesy are more.

---

### 🚀 Level 3 — Predictive / Prescriptive: *So what should we do?*

This question goes *beyond* what the data alone can answer. Write **1 Level 3 question** that connects your analysis to a real business or city planning decision.

Example (don't copy): *"If certain stations are always running out of bikes in the morning, what extra data would we need to predict demand and pre-position bikes overnight?"*

**Your Level 3 question:**
1.  Station level data - which is stations capacity

We have to explore more data sources and know different files here: 
https://github.com/MobilityData/gbfs/blob/master/gbfs.md


---

## 🚩 Part 3 — Spot the Gaps (60 min)

Every dataset has limits. A good analyst is honest about what the data *cannot* tell them.

### 3A — What is missing?

List **3 things** you would *like* to know that this dataset does not contain:

1. Station capacity
2. Profit data
3. Revenue data

Think about: rider demographics, weather, pricing, purpose of the trip, physical ability, time spent looking for a bike, etc.

---

### 3B — Who is invisible in this data?

Think about all the people who travel around Washington DC by bike. Who might be *underrepresented or completely absent* from this dataset — and why?

Write 3–4 sentences. Consider things like: who can afford a bikeshare membership, who lives near stations, who has physical access to the bikes, who might avoid riding in certain conditions.

- People who live near the station do not need bike riding 
- people who lives near work place also don't need bike riding
---

### 3C — The misleading chart trap

Here is a statement someone might make after looking at this data:

> *"Members are more responsible riders because they return bikes on time more often than casual riders."*

Write 2–3 sentences explaining why this conclusion could be **misleading** — what information are we missing that would be needed to judge "responsibility"?

---

## 📊 Part 4 — First Counts with COUNTIF (60 min)

Now we get hands-on. You'll use `COUNTIF` and `COUNTIFS` — two of the most important Google Sheets formulas for analysts.

### Formula reference

```
=COUNTIF(range, "value")           → counts rows where one column matches a value
=COUNTIFS(range1, "val1", range2, "val2")  → counts rows matching TWO conditions at once
```

---

### Step 1 — Create a summary tab

Create a new sheet tab called `summary`. Build this table manually (type the labels, fill the formulas):

| Question | Formula | Your Answer |
|----------|---------|-------------|
| Total trips | `=COUNTA(Sheet1!A:A)-1` | |
| Trips by members | `=COUNTIF(Sheet1!L:L,"member")` | |
| Trips by casual riders | `=COUNTIF(Sheet1!L:L,"casual")` | |
| Classic bike trips | `=COUNTIF(Sheet1!B:B,"classic_bike")` | |
| Member + classic bike | `=COUNTIFS(Sheet1!L:L,"member",Sheet1!B:B,"classic_bike")` | |

> ⚠️ Adjust column letters if your data imported differently. `L` should be `member_casual`, `B` should be `rideable_type`.

---

### Step 2 — Calculate percentages

Next to each count, add a column that calculates the percentage of total trips. Use the formula:

```
= [your count cell] / [total trips cell] * 100
```

Format those cells as numbers with 1 decimal place (Format → Number → Custom number format → `0.0"%"`)

---

### Step 3 — Interpret your numbers

Answer these questions in your summary tab (just type them below your table):

1. What percentage of trips are by members vs casual riders? Does that surprise you?
2. What percentage of trips use classic bikes vs electric bikes? Is it more or less than you expected?

---

## ✍️ Part 5 — Your Analyst Brief (60 min)

This is the most important deliverable of the day. Write a **structured brief** of 200–300 words covering:

1. **What this dataset is:** One sentence describing it in plain English for someone who has never heard of Capital Bikeshare.
2. **What it can tell us:** 2–3 sentences on the most interesting questions it can answer.
3. **What it cannot tell us:** 2–3 sentences on the most important gaps or limitations.
4. **Who might be missing:** 1–2 sentences on any groups underrepresented in the data.
5. **Your investigation focus:** 1–2 sentences on the specific question *you* want to investigate this week — and why.

Write this in a Google Doc or in a new tab in your spreadsheet called `analyst_brief`.

> 📌 Save this brief. You will come back to it on Day 4 to see whether your analysis answered the question you started with.

---

## ✅ Deliverables Checklist

- [ ] Data imported into Google Sheets (row count recorded)
- [ ] Column glossary table completed
- [ ] 2 unusual observations from manual scroll
- [ ] Unique values for `member_casual` and `rideable_type` noted
- [ ] 1 Level 1 question written
- [ ] Level 2 deep-dive for that question (1 explanation before checking data)
- [ ] 1 Level 3 question written
- [ ] 3 data gaps listed
- [ ] "Who is invisible" paragraph written
- [ ] Misleading conclusion critique written
- [ ] Summary tab with COUNTIF table and percentages complete
- [ ] Answers to 2 interpretation questions
- [ ] Analyst brief written (200–300 words)

---

## 💡 Bonus (if you finish early)

Sort the `start_station_name` column (copy it to a new tab first so you don't disturb the raw data). Count how many unique station names appear. Do any station names look like errors or duplicates? What would you do about that as an analyst?

---

> The best analysts spend more time *understanding the question* than running formulas. Every number you calculate next week is only as good as the question behind it.
