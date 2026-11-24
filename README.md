# Customer Shopping Behavior Analysis

End-to-end data analytics project: **Python → PostgreSQL → Power BI → Report & Presentation**.
It uncovers what drives revenue, subscriptions and discount usage across 3,900 retail purchases.

---

## Overview

A retail brand wants to know who its customers are, what they buy, and whether subscriptions and discounts are actually paying off. This project cleans the data, answers 10 business questions with SQL, visualizes the findings in an interactive dashboard, and turns them into actionable recommendations.

**Headline findings**

- Revenue differences come from **customer count, not basket size**: average order value is $58–$61 across every segment.
- **100% of subscriber orders are discounted**, yet subscribers spend no more than non-subscribers ($59.49 vs $59.87).
- Discounted orders are slightly **smaller** than full-price ones ($59.28 vs $60.13).
- **Loyalty drives subscription**: 18.1% of New customers subscribe vs 27.9% of Loyal customers.

---

## Dataset

| Item | Detail |
|---|---|
| File | `customer_shopping_behavior.csv` |
| Size | 3,900 rows × 18 columns (one row per customer) |
| Customer | Age, Gender, Location, Subscription Status |
| Purchase | Item Purchased, Category, Purchase Amount (USD), Season, Size, Color |
| Behavior | Discount Applied, Promo Code Used, Previous Purchases, Frequency of Purchases, Review Rating, Shipping Type, Payment Method |
| Data quality | 37 missing values in `Review Rating` |

---

## Tools

| Purpose | Tool |
|---|---|
| Data loading, cleaning, EDA | Python (pandas) |
| Database & business queries | PostgreSQL |
| Dashboard | Power BI |
| Reporting | PDF report |
| Presentation | PowerPoint |

---

## Steps

1. **Load & explore (Python)** – imported the CSV with pandas; inspected structure with `info()` and `describe()`.
2. **Clean data** – imputed 37 missing ratings using the median rating per product category; renamed columns to `snake_case`.
3. **Feature engineering** – created `age_group` (age quartiles) and `purchase_frequency_days`.
4. **Consistency check** – found `promo_code_used` identical to `discount_applied` in every row and dropped it.
5. **Load to PostgreSQL** – pushed the cleaned DataFrame into a database table.
6. **SQL analysis** – answered 10 business questions:
   revenue by gender, high-spending discount users, top-rated products, shipping-type comparison, subscribers vs non-subscribers, discount-dependent products, customer segmentation (New / Returning / Loyal), top products per category, repeat buyers vs subscriptions, revenue by age group.
7. **Dashboard (Power BI)** – built an interactive dashboard with slicers.
8. **Report & presentation** – documented the method and findings, then summarized them in a 9-slide deck.

---

## Dashboard

The Power BI dashboard shows:

- KPI cards: **3.9K customers · $59.76 average purchase · 3.75 average rating**
- Subscription split (27% subscribed / 73% not)
- Revenue and sales by category and by age group
- Slicers: subscription status, gender, category, shipping type

![Dashboard](images/dashboard.png)

---

## Results

| Metric | Result |
|---|---|
| Total revenue | $233,081 |
| Top category | Clothing – 44.7% of revenue (Clothing + Accessories = 76.5%) |
| Revenue by gender | Male $157,890 · Female $75,191 (reflects 68% / 32% customer mix) |
| Discounted purchases | 43% of orders |
| Customer segments | Loyal 3,116 · Returning 701 · New 83 |
| Top-rated items | Gloves (3.86), Sandals (3.84), Boots (3.82) |

**Recommendations**

- Test discount depth on Hat, Sneakers and Coat (~50% discounted) to protect margin.
- Replace flat subscriber discounts with tiered, non-price perks.
- Prompt New and Returning customers to subscribe after repeat orders.
- Build loyalty tiers to retain the large Loyal base.
- Grow female-customer acquisition: their spend per order already matches.

---

## How to Run

```bash
# 1. Clone the repository
git clone https://github.com/ayushnegi278-arch/customer_behavior_analysis.git
cd customer_behavior_analysis

# 2. Install dependencies
pip install -r requirements.txt

# 3. Create a PostgreSQL database
createdb shopping_behavior

# 4. Run the Python notebook/script (cleaning + load to PostgreSQL)
#    Update the database credentials at the top of the file first.
jupyter notebook notebooks/analysis.ipynb

# 5. Run the SQL queries
psql -d shopping_behavior -f sql/business_queries.sql

# 6. Open the dashboard
#    Open dashboard/customer_behavior.pbix in Power BI Desktop
#    and point the data source to your PostgreSQL database.
```

---

## Project Structure

```
├── data/              customer_shopping_behavior.csv
├── notebooks/         analysis.ipynb
├── sql/               business_queries.sql
├── dashboard/         customer_behavior.pbix
├── images/            dashboard.png
├── reports/           Customer_Shopping_Behavior_Analysis_Report.pdf
├── presentation/      Customer_Shopping_Behavior_Case_Study.pptx
└── README.md
```

---

## Author

**Ayush Negi** · [LinkedIn](https://www.linkedin.com/in/ayush-negi-4496b33bb) · [GitHub](https://github.com/ayushnegi278-arch)
