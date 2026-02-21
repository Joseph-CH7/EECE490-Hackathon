☕ Stories Coffee — Revenue Optimization, Forecasting & Decision Support

Course: EECE 490 — Machine Learning Hackathon
Project Type: Business Intelligence + Forecasting + Strategic Optimization
Tools: Python, Pandas, Prophet, Scikit-Learn, Matplotlib, ipywidgets

📂 Required Raw POS Files

The POS system exports reports with coded names.
Before running the notebook, rename them exactly as follows:

Original Export File	Rename To
REP_S_00134_SMRY.csv	Monthly sales.csv
rep_s_00014_SMRY.csv	Product profitability.csv
rep_s_00191_SMRY-3.csv	Sales by Groups.csv
rep_s_00673_SMRY.csv	Category summary.csv

⚠️ Filenames must match exactly (including spacing and capitalization).

Place them in the project directory before execution.

1. Business Problem

Stories Coffee operates a multi-branch network with:

25+ branches

300+ products

Strong seasonal variation

Uneven profitability distribution

The objective of this project is to:

Identify revenue concentration

Detect structural profit leaks

Optimize pricing strategy

Improve branch performance

Forecast future sales

Build an executive-level decision tool

Rather than focusing on expansion, the strategy focuses on:

Increasing profitability through targeted optimization of products and branches.

2. Data Engineering & Cleaning Pipeline

Four messy POS reports were cleaned and transformed into structured datasets.

Clean Outputs Produced

monthly_wide
Year × Branch × Jan–Dec × Total

category_branch
Branch-level totals with revenue, cost, profit, margin

product_profit
Product-level profitability preserving hierarchy

groups_sales
Division and group-level sales breakdown

Cleaning Included

Removal of page headers and report noise

Normalization of branch names

Duplicate row removal

Removal of fake “Stories” branch rows

Removal of date-stamp rows

Safe revenue reconstruction when needed:

Revenue = Total_Cost + Total_Profit
3. Exploratory Data Analysis (EDA)
Revenue Concentration

Calculated total revenue per branch

Computed revenue share (% of total)

Ranked branches by performance

Finding:
Top 3 branches generate more than one-third of company revenue.

Seasonality Analysis

Monthly totals (2025) show:

Peak months: July–August

Strong Q4: October–December

Weakest month: June

Sales volatility is seasonal but predictable.

4. Product Strategic Clustering (KMeans)

Products were clustered using:

Total Quantity Sold

Total Profit

Average Margin

After feature scaling, KMeans was applied (3 clusters).

Clusters were scored using business weights:

40% Profit

35% Margin

25% Volume

Final Labels

Star → High volume + High margin

Core Products → Stable profit contributors

Low Performer → Weak financial impact

Key finding:
Profitability is highly concentrated in yoghurt combos, bottled water, and classic bakery items.

5. Branch Ranking Model

Branches were scored using normalized metrics:

50% Total Profit

30% Revenue

20% Margin

Branches were segmented into:

Top

Mid

Underperformer

6. Sales Forecasting (Prophet Model)

A time-series forecasting model was built per stable branch.

Stability Criteria

Minimum 8 months of data

Last 3 months active

Positive total sales

Forecast Target

February–December 2026

Steps:

Convert wide data to long format

Trim pre-opening zeros

Remove placeholder trailing zeros

Train Prophet model per branch

Aggregate forecasts

Estimated runtime: ~2–3 minutes.

7. Interactive CEO Dashboard & Decision Support System

The project includes a fully interactive executive dashboard using ipywidgets.

Option A — Executive Dashboard

Year selector

Branch filter

KPI overview

Monthly trend visualization

Branch leaderboard

Top products by profit

Menu Engineering quadrant visualization

Forecast display (if available)

Option B — Strategic What-If Simulator

Interactive sliders allow simulation of:

Price increase on Stars & Plowhorses

Promotion lift on Puzzles

Removal of low-performing Dogs

Impact is estimated using transparent business logic.

8. How to Run the Project
Install Dependencies
pip install -r requirements.txt

Required libraries:

pandas

numpy

matplotlib

scikit-learn

prophet

ipywidgets

Execution Order

Rename POS files correctly.

Run data cleaning pipeline.

Run EDA section.

Run clustering section.

Run branch ranking.

Run forecasting section.

Run CEO dashboard cell
