# Day 5 — Capstone: From Raw Data to GitHub Portfolio ( 6 Hours )

> **Goal:** Combine everything from Days 1–4 into one complete portfolio project and publish it on GitHub.
>
> **Time:** ~6 hours
>
> **Output:** A public GitHub repository showing a complete beginner ETL project.



# What You Are Building

Today you will organize all of your work into a professional-looking GitHub repository.

Instead of creating lots of new analysis, your goal is to **document** what you already built and present it clearly.

By the end of today you will have:

- A GitHub repository
- Your raw and cleaned datasets
- Basic ETL documentation
- A short business analysis
- A professional README
- A short reflection on what you learned

Think of today as packaging your work for someone else to understand.



# How Today Connects to Days 1–4

| Day | What You Learned | How It Appears Today |
|---|---|---|
| Day 1 | Data roles and value chain | README and reflection |
| Day 2 | ETL pipeline | Dataset and pipeline documentation |
| Day 3 | Data cleaning and EDA | Business analysis |
| Day 4 | Business decisions | Recommendations section |



# Tasks


## Task 1 — Create Your GitHub Repository

Create a new **public** GitHub repository called

```
german-retail-etl
```

Create the following structure.

```
german-retail-etl/
│
├── README.md
├── data/
│   ├── raw_excel
│   └── cleaned_excel
├── analysis/
│   └── ANALYSIS.md
├── docs/
│   └── data_dictionary.md
└── REFLECTIONS.md
```

Only create these folders and files.

You do **not** need additional documentation files.

Commit everything using

```
initial commit: project structure
```

### Why this matters

Most real data projects follow a clear folder structure.

Anyone opening your repository should immediately know where to find:

- data
- documentation
- analysis
- project overview


## Task 2 — Export Your Data

From your Google Sheets workbook export two CSV files.

### Raw dataset

Export the **raw_data** sheet.

Rename it

```
mockaroo_export.csv
```

Save it inside

```
data/raw/
```


### Cleaned dataset

Export the **cleaned_data** sheet.

Rename it

```
german_retail_cleaned.csv
```

Save it inside

```
data/cleaned/
```

Commit both files.

```
add: raw and cleaned datasets
```


## Create a Simple Data Dictionary

Open

```
docs/data_dictionary.md
```

Document only the most important columns.

Use this format.

```markdown
# Data Dictionary

| Column | Description |
|---|---|
| transaction_id | Unique transaction ID |
| timestamp | Date and time of sale |
| city | German city |
| product | Product sold |
| quantity | Units purchased |
| unit_price_eur | Price per unit |
| payment_method | Payment type |
| satisfaction_score | Customer rating |
| returned | Return status |
| total_revenue_eur | Quantity × Unit Price |
| data_quality_flag | Quality check result |
```

You do **not** need to describe every field in detail.

The purpose is to help another person understand the dataset quickly.

Commit the file.

```
docs: add data dictionary
```



### Checkpoint

By now you should have:

- GitHub repository created
- Folder structure completed
- Raw dataset uploaded
- Cleaned dataset uploaded
- Simple data dictionary written
- Two commits completed
