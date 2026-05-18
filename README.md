📌 Project Overview
This repository features an end-to-end data analytics project focused on evaluating supermarket performance, customer purchasing behaviors, and operational efficiencies. Utilizing an iterative analysis workflow, the project processes thousands of historical transaction records to discover patterns across multiple retail branches, optimize marketing outreach, and assist inventory managers with data-driven decision-making.

The project transitions from standard exploratory data analysis (EDA) into advanced probability distribution modeling and hypothesis testing to validate critical business assumptions.
🛠️ Data Architecture & Workflow
The analysis is structured across specialized modules designed to transition raw data into actionable retail strategies:

1. Data Cleansing & Transformation (Clean data)
Prepared a transaction ledger spanning diverse geographical branches (including Yangon, Naypyitaw, and Mandalay).

Standardized features including unit pricing, quantities, cost of goods sold (COGS), gross income, and consumer ratings.

Structured date and time features to capture distinct shifting trends and foot traffic velocity.

2. Descriptive Statistics & Baseline Performance (Status Summary)
Engineered baseline metrics across the revenue funnel (Mean Sales: ~$322.26).

Monitored dispersion and structural bounds via variance and standard deviation mapping to understand customer basket sizes.

Established random sampling baselines (60 sample buckets) calculating Margin of Error ($61.04 at a 95% Certainty Level) to ensure analytical data integrity.
3. Probability Distribution Modeling (Distribution)Applied statistical distributions to solve distinct operational challenges:Normal Distribution: Modeled purchase totals to evaluate basket sizes. Discovered that while there is a ~76.5% probability of a transaction falling at or below $500, there is only a slim ~2.59% probability of a transaction exceeding $800, directing focus toward high-volume smaller baskets.Binomial Distribution: Evaluated payment method probabilities. Calculated specific success rates for credit card transactions within fixed walk-in batches to optimize checkout counter infrastructure.Poisson Distribution: Modeled daily foot traffic transaction frequency (Average $\lambda \approx 10.94$ transactions per segment) to predict next-day transaction volumes.Exponential Distribution: Analyzed point-of-sale (POS) equipment failure rates ($\lambda \approx 0.022$) to calculate the precise probability of hardware disruptions over time.
4. Hypothesis Testing (Hypothesis)
Executed statistical tests to validate core commercial assumptions:

Test 1 (Card Member Expenditures): Conducted a One-Tailed Directional Test to determine if subscription/membership status yields a statistically significant increase in average spending compared to "Normal" checkout customers.

Test 2 (Gender-Based Rating Variances): Conducted a Two-Tailed Non-Directional Test to evaluate whether a statistical difference exists between customer satisfaction ratings provided by male versus female shoppers.

🎯 Key Strategic Insights
Targeted Marketing Optimization: Visual analysis and data mapping isolated explicit branch trends. For example, observations indicate that if the marketing team has a limited promotional budget for "E-Wallet" users, campaigns should be aggressively funneled into the Giza/Mandalay pipeline to maximize conversion.

Workforce & Shift Scheduling: Poisson distribution models on hourly transactions provide store managers with the baseline predictive analytics needed to schedule employee shifts dynamically. This optimizes labor costs and minimizes overtime expenses during low-sales periods.

Inventory Focus: Normal distribution modeling strongly suggests that the store keeper shouldprioritize high-turnover inventory optimization for small-to-medium basket sizes rather than overstocking items tailored for rare, ultra-high-value baskets. 💻 Tech & Methodology Stack
Exploratory Data Analysis (EDA): Descriptive analytics, central tendency assessment, and  dispersion calculations.

Inferential Statistics: Z-scores, standard error calculations, interval estimation, and directional/non-directional hypothesis testing.

Operational Modeling: Continuous and discrete probability distributions (Normal, Binomial, Poisson, Exponential).

Data Visualization: Trend lines, scatter plots, column bar charts, distribution histograms, and contribution pie charts.prioritize high-turnover inventory optimization for small-to-medium basket sizes rather than overstocking items tailored for rare, ultra-high-value baskets.
