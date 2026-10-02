# 🍋 Meet Lina and her Google Spreadsheet ( 3 Hours )

<br>

<img width="400" alt="image" src="https://github.com/user-attachments/assets/5a979833-bf60-48a8-b595-61eb1ea73b1d" />

<br>

Lina runs a small weekend lemonade stand and started tracking her sales in **Google Sheets** — just like many real businesses do in their early stages.

She logs:
- The date of each sale  
- Which **flavor** was sold  
- How many **cups** were sold  
- The **price** per cup  
- Any **customer notes**

<br>

<img width="250" alt="image" src="https://github.com/user-attachments/assets/05d6899c-def4-470d-9daa-49d7fdaaac66" />

<br>

Here’s a **sample of her spreadsheet before cleaning**:

| Date       | Flavor   | Cups | Price | Notes            |
|------------|----------|------|-------|------------------|
| 2024-06-01 | Lemon    | 10   | 1.5   | -                |
| 2024-06-01 | lemon    | 5    | 1.5   | Repeat customer  |
| 2024-06-01 | Mint     |      | 1.8   | forgot quantity  |
| 2024-06-02 | GINGER   | 7    | 2     | typo in flavor   |
|            | Lemon    | 10   | 1.5   | Missing date     |
| 2024-06-03 | Lemon    | 10   | 1.5   | -                |
| 2024-06-03 | Lemon    | 10   | 1.5   | - (duplicate row)|
| 2024-06-04 | mint     | 8    | 1.8   | lowercase flavor |

You can view or copy the spreadsheet here:  
🔗 [**Lina Sales Data**](https://docs.google.com/spreadsheets/d/19Xcsp7q2jbOkxY9XdTeQfYYXt0HFTw8h3ncdsWhNqic/edit?usp=sharing)

<br>
<br>

## 📺 What is Google spreadsheet

<br>

[![Google Sheets Beginner](https://img.youtube.com/vi/FIkZ1sPmKNw/0.jpg)](https://www.youtube.com/watch?v=FIkZ1sPmKNw)  



<br>
<br>

## 🧼 What is messy data?

With over 100 rows now in her spreadsheet, Lina starts to notice a common challenge every data user faces:

**The data looks okay at first glance — but it’s full of small issues.**

Messy data is any data that:
- Has **inconsistent values** (e.g., "lemon", "Lemon", "LEMON")
- Has **missing cells** (e.g., no number of cups, no date)
- Has **duplicates or near-duplicates** (copied rows, repeated entries)
- Uses **uncontrolled formats** (e.g., GINGER, ginger, or blank notes)

Just like a cluttered kitchen slows down cooking, messy data **slows down — or completely derails — your analysis**.

Lina doesn’t need complex tools to fix it. A simple Google Spreadsheet is enough to clean, filter, and organize what she already has.

<br>

## ✂️ Cleaning steps Lina should take

Now that Lina has 100+ rows of data in her spreadsheet, things feel overwhelming. But Google Sheets gives her all the tools she needs.

Let’s walk through each step she should follow to clean her lemonade data.

<br>

### 1. Fill in missing values

> “Some rows don’t have the number of cups… and I skipped a few dates!”

**How to fix it:**  
- First, check if the missing value is recoverable (e.g., can she guess it based on other rows?)
- If not, leave it blank or write `MISSING` — never guess randomly
- For prices or flavors, apply the same value used in nearby entries if it makes sense

💡 *Tip: Use filters to highlight all empty rows in the Cups or Date column*

<br>

### 2. Fix formatting issues

> “Wait — I see Lemon, lemon, and LEMON… they should all mean the same thing!”

**How to fix it:**  
- Decide on a standard format (e.g., capitalize first letter: "Lemon", "Mint", "Ginger")
- Use `=PROPER()` or `=UPPER()` functions in Sheets to fix quickly
- Standardize price formatting (no currency symbols, decimals consistent)

💡 *Create a new column for “Clean Flavor” if you want to preserve the original*

<br>

### 3. Remove duplicates

> “Looks like I copied the same row more than once... maybe when pasting from my phone.”

**How to fix it:**
- Use `Data > Data cleanup > Remove duplicates`
- If needed, use a filter to sort by date + flavor + cups and scan manually

💡 *Even small duplicate errors can cause big problems in totals or averages*

<br>

### 4. Keep consistent categories

> “Sometimes I wrote ‘Mint’… sometimes ‘mint’ or even ‘MINT’. Should I fix them all?”

**How to fix it:**
- Use **Data Validation** in Google Sheets to restrict entry to three clean options: Lemon, Mint, Ginger
- Create a reference list of valid values and check for mismatches

💡 *You can create dropdowns to prevent this issue in the future*

<br>

### 5. Organize with filters

> “My sheet is so long now... how do I find what I’m looking for?”

**How to fix it:**
- Go to `Data > Create a filter`  
- Filter by: 
  - Missing values (blank rows)
  - Specific flavors
  - Days when she sold more than 10 cups

💡 *Filters help clean up the view before you clean up the data*

<br>

## 📝 What Lina’s cleaned sheet might look like

After 15 minutes of cleaning, here’s what a cleaned portion of Lina’s data looks like:

| Date       | Flavor | Cups | Price | Notes            |
|------------|--------|------|-------|------------------|
| 2024-06-01 | Lemon  | 10   | 1.5   | -                |
| 2024-06-01 | Lemon  | 5    | 1.5   | Repeat customer  |
| 2024-06-01 | Mint   | 6    | 1.8   | Estimated value  |
| 2024-06-02 | Ginger | 7    | 2     | Corrected flavor |
| 2024-06-03 | Lemon  | 10   | 1.5   | -                |
| 2024-06-04 | Mint   | 8    | 1.8   | -                |

Now Lina’s spreadsheet is:
- Easy to sort and filter  
- Ready to explore with pivot tables and charts  
- A reliable record of her sales

She didn’t need to write a single formula — just observe and organize.

<br>

## 📄 Why clean data = reliable insights

Data cleaning may feel like a chore… but it’s what separates guessing from real decision-making.

With messy data:
- “lemon” and “Lemon” are seen as two different flavors  
- Missing cups throw off total revenue  
- Repeated rows distort her sales trends  

With clean data, Lina can:
- See which flavor is really most popular  
- Trust her averages and totals  
- Feel confident about adjusting prices or restocking ingredients

Data cleaning = confidence.

<br>

## ✅ Self-check questions

<details>
<summary>🧠 What are 3 common problems in messy data?</summary>
- Missing values  
- Inconsistent formats (e.g., Lemon vs lemon vs LEMON)  
- Duplicate or near-duplicate rows  
</details>

<details>
<summary>✏️ Why should categories like flavor be standardized?</summary>
So that we don’t count the same thing under different labels and get misleading totals.
</details>

<details>
<summary>📊 How does cleaning help us later?</summary>
It ensures our charts and calculations reflect the true story in the data.
</details>

<details>
<summary>📅 What should you do if a date is missing?</summary>
Try to look it up, but if you can’t — leave it blank or mark it clearly as missing.
</details>

<br>

## 🏁 What’s next?

Now that Lina’s data is clean, she’s curious:
- Which flavors are most popular overall?  
- Do sales spike on certain days of the week?  
- Did her new mint recipe bring in more customers?

In the next chapter, we’ll guide her through **exploratory data analysis** — using simple filters, pivot tables, and charts to uncover insights.


