
# Day 1 — Data Roles & Value Chain

> **Goal:** Understand who does what in data, and how raw data becomes business insight
> **Total Time:** ~3 hours


## Overview

Before writing a single query or building a dashboard, you need to understand the landscape — who owns what, how data moves through an organisation, and where value is actually created. Today is about building that mental map.


## Tasks

### Task 1 — Role Mapping Research
**Duration:** 30 minutes

Research and write a one-page summary comparing five core data roles:

| Role | Primary Focus |
|---|---|
| Data Engineer | Builds and maintains pipelines |
| Data Analyst | Answers business questions with data |
| Data Scientist | Builds predictive models |
| Analytics Engineer | Transforms raw data into clean models |
| BI Developer | Builds dashboards and reports |

For each role, note:
- Their primary responsibility
- Tools they commonly use
- Where they sit in the data pipeline

> **Tip:** Use real LinkedIn job postings to ground your research in actual expectations, not just textbook definitions.
## Data Engineer
### Primary responsibility
Data Engineer Build data pipeline, design architecture, maintain data quality, optimize performance, support analytics and AI, Manage Cloud data platforms, Ensure securities and compliances

### Tools they commonly use
Python, SQL, Apache Spark, AWS S3, Azure Data lake storage, Databricks, Git, GitHub, GitLab, Bitbucket e.t.c

## Data Analyst
### Primary responsibility
Data analyst is responsible for examining data to uncover insights that help an organization make informed business decisions. collect, prepare data, analyze data, creating reports and dashboards, providing business insights, presenting findings, supporting decision making

### Tools they commonly use
SQL, Microsoft Excel, Power BI, Tableau, Python

## Data Scientist
### Primary responsibility
A Data Scientist uses data, statistics, and machine learning to solve complex problems, make predictions, and help organizations make strategic decisions. Understanding business problems, collecting and prepare data, Exploratory data analysis, Building machine learning models, Evaluating models, Communicating insights, Deploying and monitoring models

### Tools they commonly use
Python, SQL, Pandas, Numpy, Matplotlib, Seaborn, Plotly, Scikit-lern, Tensorflow, PyTorch, Apache Spark, Jupyter Notebook, AWS, Azure, google Cloud, Git

## Analytics Engineer
### Primary responsibility
Their primary role is to transform raw, complex data into clean, reliable, and well-organized datasets that analysts and business users can easily use for reporting and decision-making.

### Tools they commonly use
SQL, python, dbt (Data Build Tool), Git, Snowflake, Big Query, Apache Airflow, Power Bi, Tableau, AWS Azure or google cloud

## BI Developer
### BI developer
BI Developer designs, develops, and maintains dashboards, reports, and data visualization solutions that help organizations make informed business decisions.

### Primary responsibility
SQL, Power BI, Tableau, Looker, Microsoft Excel, Pytho, Git

### Task 2 — Draw the Data Value Chain
**Duration:** 30 minutes

**Part A — Sketch from memory first (10 min)**

Without looking anything up, draw the journey of raw data from source to business decision. Label each stage you can think of.

**Part B — Compare and refine (20 min)**

Compare your sketch against the DIKW pyramid:

```
Raw Data → Information → Knowledge → Wisdom → Decision
```

Note where your version differs and update your diagram. Keep this sketch — you will redraw it from memory at the end of the day.

## Data Value Chain
Data Sources
     │
     ▼
Data Collection
(Web App, Mobile App, APIs, Sensors)
     │
     ▼
Data Storage
(Database / Data Lake)
     │
     ▼
Data Cleaning & Transformation
(Remove errors, standardize, join data)
     │
     ▼
Data Warehouse
(Business-ready data)
     │
     ▼
Data Analysis
(SQL, Reports, Dashboards)
     │
     ▼
Insights
(Trends, KPIs, Patterns)
     │
     ▼
Business Decisions
(Marketing, Pricing, Inventory, Strategy)


### Task 3 — Real-World Pipeline Teardown
**Duration:** 60 minutes

Pick any company you interact with daily (Swiggy, Zomato, Amazon, your bank, etc.).

Write a 1–2 page breakdown of how data likely flows through that business. Use this prompt as your structure:

1. **Event** — A customer places an order
2. **Capture** — What data is collected and how?
3. **Storage** — Where does it go?
4. **Transformation** — How is it cleaned and modelled?
5. **Analysis** — What questions does the business ask of it?
6. **Decision** — What action does it drive? (e.g. personalised feed, warehouse stocking)

For each stage, note which data role would own that work.

## How Data Flows Through Amazon
### Event — A Customer Places an Order
A customer visits Amazon, searches for a laptop, adds it to the cart, and completes the purchase using a credit card.

This single event generates multiple pieces of data, including customer information, product details, payment details, shipping address, order time, and device information. Every interaction—from searching for the product to completing the purchase—is recorded because it helps Amazon improve customer experience and optimize operations.

Primary role: Data Engineer (captures and ingests data)
### Capture — What Data Is Collected and How?
When the customer places the order, Amazon collects data from several systems:

Customer ID
Product ID
Product category
Order ID
Quantity purchased
Price and discounts
Payment method
Shipping address
Delivery preference
Timestamp
Device type (mobile/web)
IP address
Search history
Cart activity

This information is captured through Amazon's website or mobile app and sent to backend services via APIs. Event logs record customer interactions such as searches, clicks, and purchases in real time.
Primary role: Data Engineer
### Storage — Where Does It Go?
The captured data is stored in different storage systems depending on its purpose.

Transactional databases store order and payment information.
Data lakes store raw clickstream and application logs.
Data warehouses store cleaned, structured data for reporting and analytics.

Data is replicated from operational systems into analytical storage so reporting does not affect the live shopping experience.

Primary role: Data Engineer

## Transformation — How Is It Cleaned and Modelled?

Raw data usually contains duplicates, missing values, inconsistent formats, or invalid records.

The transformation process includes:

Removing duplicate records
Standardizing date and time formats
Validating customer and product IDs
Calculating total revenue and discounts
Joining customer, product, and order tables
Creating business-friendly datasets such as:
Daily Sales
Customer Purchases
Product Performance
Inventory Levels

The transformed data is tested to ensure accuracy before it is used for reporting.

Primary roles:

Analytics Engineer (builds data models and business-ready datasets)
Data Engineer (maintains transformation pipelines)

## Analysis — What Questions Does the Business Ask?

Business teams use the prepared data to answer questions such as:

### Sales
- Which products sell the most?
- What is today's total revenue?
- Which categories are growing?
### Customer Behaviour
- Which products are frequently purchased together?
- Which customers are likely to make another purchase?
- Why do customers abandon their carts?
### Operations
- Which warehouses need additional inventory?
- Which delivery routes are delayed?
- Which regions have the highest demand?
### Marketing
- Which promotions generate the most sales?
- Which advertisements have the highest conversion rate?

Data analysts create dashboards and reports that help managers understand these trends.

Data scientists use historical data to build machine learning models that predict customer demand, recommend products, and estimate delivery times.

Primary roles:

- Data Analyst
- BI Developer
- Data Scientist

## Decision — What Action Does It Drive?

The insights generated from the data lead to several business decisions.

Personalized Recommendations

Customers receive recommendations such as:

"Customers who bought this also bought..."
"Recommended for you"

Owner: Data Scientist

### Inventory Management
Products with increasing demand are stocked in nearby warehouses to reduce delivery time.
Owner: Data Scientist and Operations Team

### Dynamic Pricing
Prices may change based on demand, competition, and inventory levels.
Owner: Data Scientist

### Marketing Campaigns
Customers who leave items in their carts may receive reminder emails or app notifications.
Owner: Data Analyst and Marketing Team

### Executive Reporting
Business leaders monitor dashboards showing:
- Daily revenue
- Orders per region
- Delivery performance
- Customer satisfaction
- Profit margins

These dashboards support strategic planning and operational decisions.

Owner: BI Developer

### Task 4 — Interview or Case Study Deep Dive
**Duration:** 30 minutes

**Read 3 case studies**

Read published case studies from companies like Netflix, Uber, Spotify, or Airbnb about how they structure and use their data teams. Summarise each in 3–4 sentences.

> Summarise your key takeaway from each source regardless of which option you choose.

## Case Study 1: Netflix

Netflix uses data extensively to personalize the viewing experience for its subscribers. Every interaction, such as searches, clicks, watch time, pauses, and ratings is collected and analyzed to recommend movies and TV shows that match a user's preferences. Data engineers build pipelines to process massive amounts of viewing data, data analysts monitor engagement metrics, and data scientists develop recommendation algorithms that improve customer retention.

- Key Takeaway:

Netflix demonstrates that combining reliable data infrastructure with machine learning enables highly personalized customer experiences, leading to greater user engagement and satisfaction.

## Case Study 2: Uber

Uber relies on real-time data to connect riders with drivers efficiently. The company collects data on ride requests, driver locations, traffic conditions, pricing, and trip duration. Data engineers process streaming data, analytics engineers prepare datasets for reporting, BI developers create operational dashboards, and data scientists build models for demand forecasting, surge pricing, and route optimization.

- Key Takeaway:

Uber shows how real-time data analytics and predictive models can improve operational efficiency, reduce wait times, and optimize resource allocation.

## Case Study 3: Spotify

Spotify uses data to understand users' listening habits and deliver personalized music recommendations. It collects information such as songs played, playlists created, listening duration, skipped tracks, and search history. Data teams use this information to improve recommendation systems, create personalized playlists like Discover Weekly, and provide artists with insights into listener behavior.

- Key Takeaway:

Spotify illustrates how analyzing user behavior can create a highly personalized experience that increases customer engagement and loyalty while helping artists better understand their audiences.


### Task 5 — Reflection & Self-Quiz
**Duration:** 45 minutes

**Part A — Written reflection (25 min)**

Write a 300–400 word reflection answering:

- What surprised me about how data roles are divided?
- Where does the most value get created in the data value chain?
- Which role do I find most interesting and why?

**Part B — Quiz yourself (20 min)**

Close all your notes and:

- [ ] Redraw the full data value chain from memory
- [ ] Name one tool each of the five roles uses
- [ ] Write one sentence describing what each role does

Check your answers, note any gaps, and add them to your running questions list.

### Part A – Written Reflection (300–400 words)
Learning about the different data roles helped me understand that building a data-driven organization requires collaboration among multiple specialists rather than a single "data expert." Initially, I assumed that data analysts and data scientists performed similar tasks. However, I was surprised to learn that each role has a distinct responsibility. Data engineers focus on collecting and managing data infrastructure, analytics engineers prepare clean and reliable datasets, data analysts interpret data to answer business questions, BI developers create dashboards and reports for decision-makers, and data scientists build predictive models using machine learning. This division of responsibilities allows each professional to specialize while working together to deliver business value.

I believe the greatest value in the data value chain is created during the transformation and analysis stages. Raw data by itself has little value because it is often incomplete, inconsistent, or difficult to interpret. By cleaning, organizing, and modeling the data, analytics engineers make it trustworthy and useful. Data analysts and BI developers then transform that information into meaningful insights that business leaders can understand. Finally, data scientists use historical data to predict future outcomes, helping organizations make proactive decisions rather than simply reacting to past events.

The role I find most interesting is Data Engineer. I enjoy the technical aspect of designing data pipelines, managing databases, and ensuring that data flows efficiently across systems. I also find it interesting that every other data role depends on the work of data engineers. Without reliable data collection, storage, and processing, analysts, BI developers, and data scientists would not have accurate data to perform their tasks. As businesses continue to generate increasing amounts of data, I believe data engineering will remain an essential and rewarding career with opportunities to work on cloud platforms, big data technologies, and scalable systems. Learning about these roles has given me a clearer understanding of how organizations convert raw data into valuable business decisions.

## Part B – Self-Quiz
### 1 Data Value Chain (from memory)

- Raw Data
    ↓
Data Collection
    ↓
Data Storage
    ↓
Data Cleaning & Transformation
    ↓
Information
    ↓
Analysis & Visualization
    ↓
Knowledge
    ↓
Wisdom
    ↓
Business Decision

## Deliverables

By end of Day 1 you should have:

- [ ] One-page role comparison summary (Task 1)
- [ ] Annotated data value chain diagram (Task 2)
- [ ] Real-world pipeline breakdown, 1–2 pages (Task 3)
- [ ] Case study summaries (Task 4)
- [ ] Written reflection + completed self-quiz (Task 5)

### 2. One Tool Used by Each Role

| Role               | Tool                  |
| ------------------ | --------------------- |
| Data Engineer      | Apache Airflow        |
| Analytics Engineer | dbt                   |
| Data Analyst       | SQL                   |
| BI Developer       | Power BI              |
| Data Scientist     | Python (Scikit-learn) |

### 3. One-Sentence Description of Each Role

| Role                   | Description                                                                                             |
| ---------------------- | ------------------------------------------------------------------------------------------------------- |
| **Data Engineer**      | Builds and maintains data pipelines and infrastructure to collect, store, and process data.             |
| **Analytics Engineer** | Transforms raw data into clean, reliable, and business-ready datasets.                                  |
| **Data Analyst**       | Analyzes data to identify trends and provide insights that support business decisions.                  |
| **BI Developer**       | Creates dashboards and reports that help stakeholders monitor business performance.                     |
| **Data Scientist**     | Builds statistical and machine learning models to predict outcomes and solve complex business problems. |

### 4. Self-Assessment

**What I remembered well:**

- The stages of the data value chain.
- The responsibilities of each data role.
- Common tools used by each role.

**Gaps I noticed:**

- I need more practice distinguishing the responsibilities of Analytics Engineers and BI Developers.
- I want to deepen my understanding of tools such as Apache Spark, Kafka, and dbt, and how they work together in modern data platforms.
- I would like to learn more about deploying machine learning models into production.

**Running Questions List**

1. How do Apache Airflow and dbt complement each other in a data pipeline?
2. When should an organization use a data lake instead of a data warehouse?
3. What skills are most important for transitioning from Data Analyst to Data Engineer?
4. How are machine learning models monitored and updated after deployment?
5. How do cloud platforms such as AWS, Azure, and Google Cloud differ for data engineering workloads?

## Key Concepts to Know

- **Data pipeline** — the series of steps that move and transform data from source to destination
- **DIKW pyramid** — Data → Information → Knowledge → Wisdom
- **Upstream / downstream** — upstream roles produce data, downstream roles consume it
- **Data consumer vs data producer** — understanding who your work serves


## Resources

- [The Data Engineering Lifecycle — Fundamentals of Data Engineering, O'Reilly](https://www.oreilly.com/library/view/fundamentals-of-data/9781098108298/)
- [Analytics Engineering Glossary — dbt Labs](https://docs.getdbt.com/glossary)
- [Towards Data Science — Role breakdowns](https://towardsdatascience.com)

