# Project: Capital Bikeshare — Simple Data Explore 
**Tool:** Google Sheets
**Duration:** 6 hours
**Difficulty:** ⭐⭐ Easy–Moderate

---

## What you're doing
You'll open one bike-trip data file, clean it up a tiny bit, answer a couple of easy questions, and then turn what you found into 5 simple charts and 3 headline stats. That's it. One sheet, simple formulas, a handful of built-in Google Sheets charts.

---

## Task 1 — Get the Data In (1 hour)
1. Download `202309-capitalbikeshare-tripdata.csv` from capitalbikeshare.com/system-data
2. Open a new Google Sheet
3. File → Import → Upload → pick the CSV → **Replace current sheet**
4. Rename this tab `Data`

**That's the whole task.** Take your time looking through the columns — just scroll around and notice what's there (bike type, start time, end time, member or casual rider). No formulas yet.

✅ Done when: the data is sitting in your sheet and you've scrolled through it once.

- we have the data file (sep 2023 reduced):
  https://docs.google.com/spreadsheets/d/1P6JFC8WqIGZPIpdNL2qmrCjsaVmVVJcS0x1adQ9_j0k/edit?gid=1931979345#gid=1931979345


  
---

## Task 2 — Add One Simple Column (1 hour)
We're going to figure out how long each trip took, in minutes. Just one column.

1. Find the column with **started_at** and the column with **ended_at**
2. In the first empty column, type the header: `duration_min`
3. In the first data row, use this simple formula (adjust column letters C and D to match your `started_at` / `ended_at` columns):
```
=ROUND((D2-C2)*1440, 1)
```
4. Click that cell, then drag the little square in the bottom-right corner down to fill the whole column (or copy/paste the cell down).

✅ Done when: every row has a number in `duration_min` showing minutes.

*(No need to worry about bad data or errors — just get the column filled. If a few cells show weird numbers, that's fine for this simple version.)*


<img width="1614" height="667" alt="image" src="https://github.com/user-attachments/assets/a811d317-ad61-4351-b511-a2a8b3dd5901" />

---

## Task 3 — Answer 2 Easy Questions (2 hours)
On a new tab called `Answers`, use simple formulas to find:

| Question | Formula (fill in your own column letters/tab name) |
|---|---|
| What's the **average** trip duration? | `=AVERAGE(Data!E:E)` |
| How many trips were by **members** vs **casual** riders? | `=COUNTIF(Data!K:K,"member")` and `=COUNTIF(Data!K:K,"casual")` |

Then, in a couple of plain sentences underneath, write:
- What was the average trip length? 19.9 minutes
- Were there more member trips or casual trips? More mebver trips
- One sentence guessing *why* that might be.
  - This is because we have more registered users than casual users.

✅ Done when: you have 2 numbers and 2–3 sentences written in plain English.

<img width="1870" height="429" alt="image" src="https://github.com/user-attachments/assets/f5ffac82-2287-440d-82bf-dff33d068f85" />

---

## Task 4 — Build 5 Visuals + 3 Headline Stats (2 hours)
Now let's turn the data into something people can actually look at. Stay on the `Answers` tab (or add a new tab called `Charts` if you'd rather keep it separate) and build all of the below using Google Sheets' built-in **Insert → Chart** tool — no add-ons, no scripting.

### The 3 headline stats
Add these three numbers near the top of the tab, each with a short label above it (like a mini dashboard):

| Stat | Formula |
|---|---|
| **Total trips** | `=COUNTA(Data!A:A)-1` *(subtracts 1 for the header row)* |
| **Average trip duration (min)** | `=AVERAGE(Data!E:E)` *(you already have this from Task 3)* |
| **% of trips by members** | `=COUNTIF(Data!K:K,"member")/COUNTA(Data!K:K)` *(format the cell as a percentage)* |

- The total trips is 20000
- The Average trip duration is 19.9
- The Average trips by members is 64% 


### The 5 plots
For each one, select the relevant column(s) in `Data`, then **Insert → Chart**, and pick the chart type Sheets suggests (or the one listed below).

1. **Trip duration histogram** — select `duration_min` → Insert → Chart → change chart type to **Histogram**. Shows how trip lengths are distributed (are most trips short hops or long rides?).

<img width="449" height="272" alt="image" src="https://github.com/user-attachments/assets/b9331b2e-18b6-49b4-a496-1e15c55291fa" />

2. **Trips by hour of day (line chart)** — add a helper column `hour` using `=HOUR(C2)` on `started_at`, then build a pivot table (Insert → Pivot table) counting trips by `hour`, and chart it as a **line chart**. Shows the daily commute pattern.                                                                                                                                                                                 <img width="654" height="402" alt="image" src="https://github.com/user-attachments/assets/2101fa36-5ed2-40e9-b6f4-5f42b9790739" />




3. **Member vs casual split (pie chart)** — use your two `COUNTIF` numbers from Task 3, put them in two cells with labels "Member" / "Casual", select both, Insert → Chart → **Pie chart**.
4. **Trips by day of week (bar chart)** — add a helper column `day` using `=TEXT(C2,"ddd")`, pivot table counting trips by `day`, chart as a **column/bar chart**. Shows weekday vs weekend riding habits.
5. **Top 10 start stations (bar chart)** — pivot table on the `start_station_name` column, sort descending by count, keep the top 10 rows, chart as a **horizontal bar chart**. Shows where demand is concentrated.

Give every chart a plain-English title (e.g. "How long do trips usually take?" instead of "duration_min histogram") — this is a hands-on habit worth building early: a chart nobody can read at a glance isn't finished yet.

✅ Done when: you can see all 5 charts and all 3 stats on one tab without scrolling sideways, and each chart has a title a non-technical person could understand.

---

## That's it! 🎉
No cleaning rules, no A/B testing, no dashboard tooling, no pipeline stages. Just: import → one formula column → two simple answers → five charts and three stats anyone could glance at and understand.
