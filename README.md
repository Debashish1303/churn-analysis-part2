# Capstone Project: D2C Customer Churn Intelligence & Retention Strategy
## Part 2 — RFM Segmentation & Targeted Retention Engine

This repository contains the dataset engineering, segment logic development, and strategic execution framework for **Part 2** of the D2C Customer Churn Capstone. The objective of this phase is to build an explainable customer segmentation framework using transactional RFM metrics and non-RFM behavioral signals to optimize targeted marketing spend without relying on black-box machine learning models.

---

## 📋 Project Architecture & Artifacts

The repository is organized to follow an independently runnable structure:

* `notebooks/rfm_segmentation.ipynb` — The core Jupyter Notebook executing data intake, cleansing, RFM engineering, priority rule evaluation, and visual cohorts analysis.
* `notebooks/segments.csv` — The generated user matrix output containing `customer_id`, assigned `segment_name`, and vital metrics.
* `retention_strategy.md` — The detailed business strategic outline, prioritization mechanics under tight budgets, and financial rationale.
* `manual_review_cases.md` — An audit report reviewing 10 highly ambiguous/conflicting customer profiles with custom recovery blueprints.
* `pyproject.toml` — Project environment configuration detailing required Python boundaries and packages.

---

## 📊 Segmentation Framework Summary

Customers are evaluated through a strict priority-ordered logic tree into **exactly 5 segments**:

1.  **Dormant Customers (17.9% of base):** Cold leads with heavy inactivity (Recency $> 150$ days) and low trial engagement ($\le 1$ order).
2.  **At-Risk Customers (8.1% of base):** High historical advocates ($\ge 2$ orders) who have crossed into a $90\text{–}150$ days inactive window.
3.  **Discount-Sensitive Customers (20.1% of base):** Customers relying on deep promotional markdowns (average transaction discount $\ge 35\%$). **Note:** Evaluated before Champions, trapping high-spending deal seekers here to shield margins.
4.  **Champions (8.0% of base):** VIP organic core with high frequency ($\ge 3$ orders), high spend ($\ge$ ₹1,500), and short recency ($\le 45$ days) *without* relying on steep discounts.
5.  **Loyal Customers (45.8% of base):** The strategic operational backbone (catch-all for active or moderately engaged accounts not meeting boundaries above).

### 🔄 Multi-Signal Enhancements
Standard RFM indicators have been integrated with operational data pipelines:
* **Customer Care Friction:** Accounts with $> 2$ active support tickets (`ticket_count_90d`) bypass automated messaging flows and route to senior account callbacks.
* **Product Dissatisfaction:** Accounts exceeding a $30\%$ product return rate (`return_rate_180d`) have promotional vouchers auto-suppressed and replaced with user feedback loops and tutorial content.

---

## 🛠️ Environment Setup & Run Instructions

This project relies on `uv` or standard Python virtual environment tools and requires **Python $\ge 3.12$**.

### Prerequisites
Ensure you have Python 3.12 or higher installed. 

### Step 1: Clone the Repository
```bash
git clone https://github.com/Debashish1303/churn-analysis-part2
cd churn-analysis-part2

```

### Step 2: Initialize Virtual Environment & Install Dependencies

Using `uv`:

```bash
uv venv
uv sync

```

### Step 3: Run the Segmentation Engine

To re-generate the segment maps and compute features, boot the notebook server and run `notebooks/rfm_segmentation.ipynb`:

```bash
jupyter notebook notebooks/rfm_segmentation.ipynb

```

---

## 💰 Capital Allocation & Prioritization Blueprint

When operating under tight budget ceilings, marketing funds are funneled through a strict high-ROI cascade:

* 🥇 **Top Priority: At-Risk Customers:** Represents the highest marginal lifetime value recovery. Focuses recovery incentives (₹200 Off Vouchers) where historical affinity is proven but churning is imminent.
* 🥈 **Secondary Priority: Loyal Customers:** Secured next via average order value (AOV) builders (e.g., Free Shipping thresholds at ₹999) to keep the baseline active engine insulated from competitors.
* 🥉 **Tertiary Priority: Discount-Sensitive:** Handled using bundle architectures (e.g., Save 15% on 3 items) to systematically wean them off margin-diluting individual vouchers.

For full breakdowns on ROI expectations and custom treatment strategies for boundary-straddling customers (such as hidden champions or high-value frustrated buyers), review `retention_strategy.md` and `manual_review_cases.md`.
