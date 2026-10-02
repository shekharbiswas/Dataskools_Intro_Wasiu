# Google Sheets — Session Quiz


## Part 1 — Navigation and Data Setup (Q1–Q5)

**Q1.** You open a dataset with 500 rows. After scrolling down to row 200, the column headers disappear. What is the fastest fix, and exactly where do you click to apply it?

**Q2.** What is the difference between "Sort sheet" and "Sort range" in Google Sheets? When would you use one over the other?

**Q3.** You freeze the first row of your sheet. A thick grey horizontal line appears. What does that line represent, and how do you remove the freeze?

**Q4.** A colleague shares a sheet with you and has applied a filter that hides 40 rows. You want to apply your own filter without affecting what they see. What feature do you use?

**Q5.** You have a dataset with columns A to M. You want column A (student IDs) to stay visible while scrolling right through the other columns. Write the exact menu path to achieve this.



## Part 2 — Formulas for EDA (Q6–Q14)

**Q6.** Write the formula to count how many rows in column B contain the word "Completed".

**Q7.** Write the formula to count rows where column C is "Berlin" AND column D is greater than 500.

**Q8.** Write the formula to sum all values in column D where the corresponding value in column B is "Active".

**Q9.** What is the correct argument order for SUMIFS? Why is it different from SUMIF, and what mistake do beginners most often make?

**Q10.** Write the formula to calculate the average final_score (column I) only for students whose status (column J) is "Completed".

**Q11.** You want to check data completeness. Write two different formulas — one that counts non-empty cells in column F, and one that counts empty cells in the same column.

**Q12.** Column A contains student IDs. Some IDs appear more than once. Write a formula using COUNTIF that flags duplicate entries in a helper column — the formula should return TRUE for any row that is a repeat.

**Q13.** Write the formula that returns a deduplicated list of all unique values from column C (city). Then write the formula to sort that list alphabetically.

**Q14.** You use =AVERAGE(D2:D200) but the result seems too low. You suspect some cells in D are blank. Does AVERAGE include blank cells in its calculation? What about zero values? Explain the difference.


## Part 3 — Data Cleaning (Q15–Q20)

**Q15.** A student's name in cell A2 is "  anna müller  " (extra spaces, all lowercase). Write a single formula that fixes both the spacing and the capitalisation in one step.

**Q16.** Column B contains city names but they are inconsistent — "berlin", "Berlin" and "BERLIN" all appear. You want to standardise them all to "Berlin". Write the formula that would clean one cell, and describe how you would apply the fix across the whole column.

**Q17.** Your ID column should always contain exactly 8 characters (e.g. "STU00012"). Write a formula that checks whether the value in B2 has the correct length, returning "OK" if it does and "Check" if it does not.

**Q18.** Column A contains entries like "Data Science, Python, SQL" — all three values in one cell separated by a comma. Which function would you use to split them into separate columns, and what is the syntax?

**Q19.** You want to replace all hyphens in a phone number stored in cell C2 (e.g. "030-445-9821") with nothing, so it becomes "030445982". Write the formula.

**Q20.** What does the IFERROR function do, and why is it particularly useful when using VLOOKUP in a real dataset? Write an example.


## Part 4 — Pivot Tables, Charts and Lookups (Q21–25)

**Q21.** You build a Pivot Table with "course" in Rows and "monthly_fee_eur" in Values. By default it shows SUM. You want to see the average fee per course instead. Describe the exact clicks to change the aggregation.

**Q22.** You want to see a cross-tab of course (rows) vs city (columns) showing the count of students at each intersection. Describe how you set this up in the Pivot Table editor.

**Q23.** What is the difference between VLOOKUP and XLOOKUP? Give one practical reason you would prefer XLOOKUP in a real analysis.

**Q24.** You have a main sheet with a "course" column and a separate reference sheet called "Courses" where column A has course names and column C has the instructor name. Write the VLOOKUP formula to pull the instructor name into the main sheet, starting from cell B2.

**Q25.** You insert a Sparkline chart in cell H2 using the data in B2:G2. The sparklines for different rows look incomparable because each one scales to its own min and max. What setting do you change to make all sparklines use the same scale?



## Part 5 — Thought Questions (Q26–Q30)

**Q26.** You receive a dataset of 2,000 rows from a client. Before running any formula, what are the five first things you would check, and why does the order matter?

**Q27.** A junior analyst on your team applies filters, deletes rows, and sorts the data directly on the original sheet — all without making a copy first. What are the risks of this approach, and what habits would you recommend they develop instead?

**Q28.** You run =COUNTIF(B:B,"Completed") and get 312. You also run =COUNTA(B2:B500) and get 499. But when you add up COUNTIF for all three statuses (Completed, Active, Dropped) you only get 480. What are two possible explanations for the gap of 19 rows?

**Q29.** You are asked to present a summary of student performance to a non-technical manager. You have final_score, sessions_attended, and status available. Which two charts would you choose, what would each show, and what would you NOT show and why?

**Q30.** Google Sheets has limits — it struggles with very large datasets, has no version control by default, and formulas can break when rows are inserted or deleted. Knowing this, describe a situation where Google Sheets is the right tool for data work, and a situation where it is the wrong tool and something else should be used instead.



*End of Quiz — 30 Questions*
