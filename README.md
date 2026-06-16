# 🛒 Supermarket Analysis Project: A Data-Driven Operations Analysis of Q1 2019

> *Cleaning the noise. Finding the signal. Telling the story behind every transaction.*

---

## 📌 Project Overview

This capstone project puts me in the role of a **Data Analyst** for a supermarket chain running three branches across Egypt — **Alexandria, Cairo, and Giza**. Starting from a raw, messy extract of roughly **1,000 transactions** covering Q1 2019, the goal was to turn noisy data into clear, actionable business intelligence — all within a single Excel workflow.

The analysis moves through five stages: data cleaning, descriptive statistics, visual dashboarding, probability modeling, and hypothesis formulation. Every metric calculated answers a real business question; every chart was built with management decision-making in mind.

---

## 🗂️ Dataset

| Attribute      | Detail                                            |
| -------------- | ------------------------------------------------- |
| **Period**     | Q1 2019 (January – March)                         |
| **Branches**   | Alexandria (A), Cairo (B), Giza (C)               |
| **Total Rows** | ~974 (after cleaning)                             |
| **Tool Used**  | Microsoft Excel (Power Query + Formulas + Charts) |

**Key columns:** Invoice ID, Branch, City, Customer Type, Gender, Product Line, Unit Price, Quantity, Tax, Total, Date, Time, Payment Method, COGS, Gross Margin, Gross Income, Customer Rating.

---

## 🔧 Part 1 — Data Cleaning (Power Query)

The raw dataset came with a few structural problems that would have corrupted any downstream analysis if left alone:

- **Merged columns:** `City_CustType` bundled two separate attributes into one field. I split these into `City` and `Customer Type` using the correct delimiter.
- **Text inconsistency:** Product line entries had inconsistent capitalization. I applied *Capitalize Each Word* to normalize everything.
- **Null values:** Rows with blank `Rating` fields were removed — they couldn't contribute to satisfaction analysis.
- **Data types:** `Unit Price` and `Total` were cast to Currency; `Quantity` was cast to Whole Number.

The cleaned output was loaded into a dedicated `Clean_Data` sheet — the single source of truth for all subsequent work.

---

## 📊 Part 2 — Baseline Metrics & Statistical Summary

With clean data in place, I moved to establishing the financial and behavioral baseline for the quarter.

| Metric                             | Value                   |
| ---------------------------------- | ----------------------- |
| **Mean Total Bill**                | $322.26                 |
| **Median Total Bill**              | $253.39                 |
| **Standard Deviation (Rating)**    | ~1.72                   |
| **Margin of Error (95% CI, n=60)** | Calculated via Z = 1.96 |

### 🔍 Observation 1 — Skewness in Sales Revenue

The mean ($322.26) sits noticeably above the median ($253.39) — a gap of $68.87. This is the classic fingerprint of a **right-skewed distribution**: a handful of very large purchases pulling the mean upward while the majority of transactions sit at lower values. With a standard deviation of $245.65, transaction amounts are highly spread out.

**Implication:** The median is a more honest picture of a *typical* customer transaction. Management shouldn't anchor operational expectations to the mean figure.

---

## 📈 Part 3 — Visual Dashboard

I built four visualizations to give management an at-a-glance picture of Q1 operations.

### Scatter Plot — Total Bill vs. Quantity
<img width="800" height="500" alt="xy_scatter" src="https://github.com/user-attachments/assets/69abff2a-4732-4ed5-b0fb-62eecea14aed" />
A positive linear relationship exists between quantity purchased and total bill (R² = 0.4957). About **49.57%** of the variation in total bill is explained by quantity alone — a moderate but meaningful correlation. The trend is real, not random.

---

### Bar Chart — Sales by Branch
<img width="800" height="500" alt="sales_by_branches" src="https://github.com/user-attachments/assets/ed70106a-5371-483f-ae45-fcebf28cc8d9" />
All three branches performed within a tight band in Q1 2019:

| Branch         | Total Sales|
| -------------- | ------------- |
| Alexandria     | $103,013      |
| Cairo          | $102,875      |
| **Giza**       | **$107,993**  |

Giza leads — not by a dramatic margin, but consistently.

---

### Pie Chart — Payment Method Breakdown
<img width="800" height="500" alt="payment_type_by_quantity" src="https://github.com/user-attachments/assets/84ddaf42-dc2b-4c6c-9fbd-fd26883e6590" />

Customer payment preferences were nearly evenly split across all three channels:

- **Ewallet:** 35%
- **Cash:** 34%
- **Credit Card:** 31%

The near-parity signals a diverse, digitally-engaged customer base and opens the door for targeted payment promotions.

---

### Histogram — Distribution of Customer Ratings

Customer ratings (on a scale of 4–10) showed a broadly **uniform distribution**, with a slight spike at the [4, 4.5] bin and a mild dip at the upper end ([9.5, 10]). There's no strong concentration of very high ratings — satisfaction is consistent but hasn't hit exceptional territory.

<img width="800" height="500" alt="histogram_trend" src="https://github.com/user-attachments/assets/7de7dda4-0369-4a40-93ea-af7bc840e664" />
---

### 🔍 Observation 2 — Ewallet Promotion Strategy

**Giza is the best target for any Ewallet campaign.** It had the highest total revenue ($107,993), the widest Ewallet transaction spread, and an estimated Ewallet revenue of ~$37,797 (35% × $107,993) — the highest across all branches. Concentrating a promotion here reinforces existing high-value Ewallet behavior and delivers the best return per marketing dollar.

---

## 🎲 Part 4 — Probability Modeling

### Normal Distribution — Sales Revenue

Using Mean = $322.26 and SD = $245.65:

| Scenario                        | Probability |
| ------------------------------- | ----------- |
| Customer spends **≤ $500**      | **76.53%**  |
| Customer spends **≥ $800**      | **2.59%**   |

**Observation 3:** More than three-quarters of customers spend under $500, and purchases above $800 are statistically rare — roughly 1 in every 39 customers. The data strongly favors a **volume-over-premium strategy**: stock for frequent, moderate-sized baskets rather than high-ticket items that sit on shelves.

---

### Binomial Distribution — Credit Card Usage (p = 0.31)

| Scenario                                        | Probability |
| ----------------------------------------------- | ----------- |
| Exactly 20 of 50 customers pay by credit card   | **4.63%**   |
| Exactly 0 of 10 customers pay by credit card    | **2.45%**   |

Both outcomes are statistical edge cases. Credit card usage is steady but not dominant — planning POS terminals or staffing purely around card traffic would be a miscalculation.

---

### Poisson, Exponential & Uniform Distributions

Additional probability models were applied to specific operational questions:

- **Poisson (Foot Traffic):** Modeled daily transaction probability to guide shift scheduling. Extreme outlier volumes (e.g., 120 transactions/day) are very unlikely and shouldn't drive baseline staffing decisions.
- **Exponential (Equipment Failure):** With printer jams averaging every 45 minutes, the probability of one occurring within a 20-minute window is non-trivial (~36%). Preventive maintenance schedules should account for this.
- **Uniform (Voucher Draw):** Each of 300 receipts holds an equal 1/300 probability of winning — no receipt number carries any advantage.

---

## 🧪 Part 5 — Hypothesis Formulation

### Test 1 — Member vs. Normal Customer Spend

- **H₀:** The average total spend of Member customers = the average total spend of Normal customers.
- **H₁:** The average total spend of Member customers > the average total spend of Normal customers.
- **Test type:** One-tailed (directional) — the marketing team suspects Members spend *more*, not just *differently*.

### Test 2 — Customer Rating by Gender

- **H₀:** The average customer rating for Male shoppers = the average customer rating for Female shoppers.
- **H₁:** There is a difference in average rating between Male and Female shoppers.
- **Test type:** Two-tailed (non-directional) — no prior assumption is made about which group rates higher.

---

## 🛠️ Tools & Techniques

| Category               | Tool / Method                                    |
| ---------------------- | ------------------------------------------------ |
| Data Cleaning          | Excel Power Query                                |
| Descriptive Statistics | Excel (AVERAGE, MEDIAN, MODE, STDEV.S, VAR.S)    |
| Visualizations         | Excel Charts (Scatter, Bar, Pie, Histogram)      |
| Probability Modeling   | NORM.DIST, BINOM.DIST, POISSON.DIST, EXPON.DIST  |
| Hypothesis Framing     | One-tailed and two-tailed T-test structure       |

---

*This project was completed as a capstone for an Excel for Data Analytics course, applying statistical and analytical techniques to a real-world retail operations scenario.*

---

> *"Without data, you're just another person with an opinion."* — W. Edwards Deming
