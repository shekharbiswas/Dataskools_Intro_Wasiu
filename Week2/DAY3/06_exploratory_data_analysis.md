# 🔍 What is exploratory data analysis (EDA)? ( 3 Hours )

Exploratory Data Analysis (EDA) is about **looking around in your data before jumping to conclusions**.

It’s the step where you:
- Spot patterns  
- Notice trends  
- Find outliers or strange values  
- Ask better questions

For Lina, this means:
> “Now that my data is clean… what is it telling me?”

Just like flipping through pages before buying a book, EDA helps us **understand the story hidden in our spreadsheet**.

<br>

## 🍋 Lina’s questions after cleaning her data

Now that her lemonade sales data is ready, Lina is curious:

1. 🏆 **What flavors sell the most overall?**  
2. 🌤️ **Do sales increase on sunny weekends?**  
3. 🌱 **Did her new mint recipe (launched on June 8) increase demand?**  
4. 📅 **Which days have the most total sales (in cups)?**  
5. 🛒 **How much does she earn on average per flavor?**

<br>

## 🧭 Step-by-step: exploring with Google Sheets

Lina doesn't use Python or SQL — she just opens Google Sheets. Here’s how she explores the data using built-in features.

<br>

### 📊 Step 1: Create a pivot table

**Goal:** Find out which flavors sold the most

1. Select your entire dataset  
2. Go to `Insert > Pivot table`  
3. For **Rows**, select `Flavor`  
4. For **Values**, select `Cups` → summarize by **SUM**  
5. Optional: sort by largest to smallest

💡 *This tells Lina how many cups of each flavor she sold overall.*

<br>

### 📅 Step 2: Check daily sales patterns

**Goal:** Find out which dates had the most or fewest sales

1. Create a new pivot table  
2. For **Rows**, choose `Date`  
3. For **Values**, choose `Cups` → SUM  
4. Observe highs and lows

💡 *She might notice that weekends (Saturday/Sunday) have higher sales — a trend to track.*

<br>

### 🌤️ Step 3: Add weather context (manually)

Lina remembers sunny days = more people outside. She creates a new column:

| Date       | Weather |  
|------------|---------|  
| 2024-06-01 | Sunny   |  
| 2024-06-02 | Rainy   |  
| 2024-06-03 | Cloudy  |  
| ...        | ...     |  

She then:
- Filters to show only **Sunny days**
- Checks total sales on sunny vs. rainy days

💡 *This adds external context — even a simple note can improve your insights.*

<br>

### 🌱 Step 4: Compare sales before and after a recipe change

Lina started using a new **mint recipe on June 8**. She wants to know:
> “Did mint sales improve after that date?”

Here’s what she does:
- Filter for `Flavor = Mint`
- Sort or filter by `Date`
- Compare average cups sold before vs after June 8

💡 *No need for complex math — just visual inspection and average row counts*

<br>

### 🛒 Step 5: Explore average price per flavor

To see if she’s charging consistently:

1. Insert a pivot table  
2. **Rows**: `Flavor`  
3. **Values**: `Price` → summarize by **AVERAGE**

💡 *If Mint has a higher average price, she might test if customers still buy it in high volume*

<br>

## 🧠 Insights Lina might find

From this light analysis, Lina discovers:
- Lemon is her most consistent seller  
- Mint sales increased slightly after June 8  
- Sales are highest on Saturdays and sunny days  
- Ginger has low sales but strong repeat comments  
- Her prices are fairly consistent, but Mint averages a bit higher

These are **early signals** — not final answers.

<br>

## 🧪 EDA = exploring before explaining

Lina’s key takeaway is:
> “I don’t need to know all the answers right away — I just need to look.”

EDA is where curiosity leads:
- Do I see any trends?
- Anything unexpected?
- Do I need more info?

It helps avoid the trap of rushing to conclusions.

<br>

## ✅ Self-check questions

<details>
<summary>🔍 What’s the goal of EDA?</summary>
To explore the data, understand what’s happening, and discover patterns before doing formal analysis.
</details>

<details>
<summary>📊 Why use a pivot table?</summary>
To summarize data (e.g., total cups per flavor, average price) without writing formulas.
</details>

<details>
<summary>🌤️ How can external context like weather help?</summary>
It helps explain *why* something is happening — not just *what* is happening.
</details>

<details>
<summary>📆 What does it mean to explore “before and after” a change?</summary>
It lets you see if something had an effect — like a new recipe or a marketing campaign.
</details>

<br>

## 🏁 What’s next?

Lina is now ready to make her first real **data-informed business decisions**:

- Which flavor to promote  
- Whether to adjust prices  
- When to prepare more stock

In the final chapter, we’ll show how **data supports real decisions** — even in the smallest businesses.
