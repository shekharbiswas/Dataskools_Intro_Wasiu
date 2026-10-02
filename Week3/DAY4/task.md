# Day 4 Task: Compare Two Bike Types — Simple Version ( 6 Hours )

- **Dataset:** Your `all_data` sheet from Day 3
- **Tool:** Google Sheets
- **Time:** ~6 hours
- **Difficulty:** ⭐ Easy 

---

## What you're doing

You're checking whether classic bikes and electric bikes get ridden for different amounts of time. Three simple tasks: write a guess, compare the averages, write what you found. No p-values, no effect size math, no confound checks.

---

## Task 1 — Write Your Guess (1.5 hours)

Before looking at any numbers, write a few sentences answering:

```
Question: Do you think electric bike rides are longer, shorter, or 
about the same length as classic bike rides? 

My guess: ________ because ________.

Why would Capital Bikeshare care about this? (1 sentence)
```

That's the whole task — just your honest guess in writing, saved somewhere on a new tab called `ab_test`.

✅ Done when: you've written your guess and reasoning, 3–4 sentences total.

We checked the averages in our spreadsheet and I think
- I think electric bike rides will be shorter than classic bikes.
- I think electric bike riders spend less time on same distance.

---

## Task 2 — Find the Average for Each Bike Type (2.5 hours)

On your `ab_test` tab, build this simple table:

| Bike Type | Average Duration (min) | Number of Trips |
|---|---|---|
| Classic | `=AVERAGEIF(all_data!B:B,"classic_bike",all_data!M:M)` | `=COUNTIF(all_data!B:B,"classic_bike")` |
| Electric | `=AVERAGEIF(all_data!B:B,"electric_bike",all_data!M:M)` | `=COUNTIF(all_data!B:B,"electric_bike")` |

*(Adjust column letters B and M if your bike-type or duration columns are in different spots.)*

<img width="627" height="226" alt="image" src="https://github.com/user-attachments/assets/fcbb73fa-f2ad-4727-ac99-899ee2911f0b" />

Then calculate one simple thing:

```
Difference = Average(Classic) - Average(Electric)
```
Difference = 7.19

✅ Done when: you have two averages, two trip counts, and one difference number.

---

## Task 3 — Write What You Found (2 hours)

In a couple of plain-English sentences underneath your table, answer:

- Was your Task 1 guess right or wrong? Our 1st guess was right
- Which bike type had longer average trips, and by how many minutes? classic_bike with difference of 7.19
- Give one simple reason why that might be true (e.g. "maybe electric bikes are used for quicker errands"). classic_bike are more manual, so it likely to be less faster than electric_bike

That's your whole write-up — no jargon, no formulas, just a few honest sentences a friend could understand.

✅ Done when: you have 3–4 sentences comparing your guess to what the numbers actually showed.

---

## That's it! 🎉

No hypothesis testing formulas, no p-values, no sample prep, no effect size, no confound analysis. Just: guess → compare two averages → write what happened.
