# D2C Customer Churn Capstone — Part 2: Segment-Targeted Retention Strategy

This document details our strategic segment definitions, behavioral signal integrations, and targeted campaign proposals designed to maximize marketing ROI under strict budget constraints.

---

## 1. Segment Definitions & Justification

Using pre-snapshot RFM variables and behavioral indicators, we segmented the customer cohort into exactly five distinct groups. The segmentation is applied in priority order — a customer is assigned to the **first** segment whose criteria they satisfy:

### 1. Champions (191 customers — 8.0%)
* **Profile:** Customers with short recency ($\le 45$ days), high transaction frequency ($\ge 3$ orders in 180 days), and high overall spend ($\ge$ ₹1,500).
* **Segmentation Priority:** 4th in rule evaluation order. Because Discount-Sensitive fires first (priority 3), customers who meet Champion thresholds but also have avg discount $\ge 35\%$ are captured as Discount-Sensitive instead.
* **Business Justification:** These are our most active brand advocates who buy frequently, recently, and at high spend — *without* relying on heavy discounts. They represent the highest contribution margin and have near-zero baseline churn.
* **Targeting Objective:** Nurture advocacy, introduce new high-margin launches, and leverage their loyalty through referral rewards.

### 2. Loyal Customers (1,100 customers — 45.8%)
* **Profile:** The catchall segment — customers who do not meet the criteria for any of the four specific segments above. This includes a broad range of behaviors: single-purchase recent buyers, moderate-frequency buyers with recency between 45–150 days, and low-discount customers who narrowly miss Champions thresholds.
* **Business Justification:** This is the largest segment and represents our core operational backbone. While heterogeneous, these customers are neither dormant nor acutely at-risk. They buy with moderate consistency and can be nudged to increase order values or frequency.
* **Targeting Objective:** Increase average order value (AOV), drive repeat purchases, and shield them from competitor promotions.

### 3. At-Risk Customers (195 customers — 8.1%)
* **Profile:** Past frequent buyers ($\ge 2$ orders in 180 days) who have not made a single transaction in the last 90 days (recency $> 90$ days), but whose recency has not yet exceeded 150 days (otherwise they would be Dormant if frequency $\le 1$).
* **Segmentation Priority:** 2nd in rule evaluation order, immediately after Dormant.
* **Business Justification:** These were highly active advocates who are actively slipping away. Because their historic spend is high, letting them churn is a major financial loss.
* **Targeting Objective:** Prompt re-engagement, uncover service complaints, and save their lifetime value.

### 4. Discount-Sensitive Customers (483 customers — 20.1%)
* **Profile:** Customers whose average transaction discount exceeds 35% ($\ge 0.35$) and have at least 1 order in the 180-day window. Importantly, this rule fires **before** the Champions check — so even customers with Champion-level recency, frequency, and spend are classified here if their average discount is high.
* **Segmentation Priority:** 3rd in rule evaluation order.
* **Business Justification:** While they generate transaction volume, their heavy discount reliance produces low direct margins. Blindly giving them standard discounts dilutes profit. Some customers in this segment may exhibit Champion-grade purchasing behavior but are driven primarily by promotional pricing.
* **Targeting Objective:** Nudge them into margin-efficient bundle purchases and gradually wean them off deep discounts.

### 5. Dormant Customers (431 customers — 17.9%)
* **Profile:** Inactive customers (recency $> 150$ days) who had very low purchase volumes ($\le 1$ order) in the 180-day window.
* **Segmentation Priority:** 1st in rule evaluation order (checked first).
* **Business Justification:** These are cold leads. They had poor initial activation. Winning them back has a very low conversion rate.
* **Targeting Objective:** Minimal spend. Use low-cost email updates.

---

## 2. Integration of Non-RFM Signals

We enhanced standard RFM segmentation by incorporating support tickets and return rate logs:

1. **Service Complaint Bottlenecks (`ticket_count_90d`):** 
   * Regardless of whether a customer is a Champion or Loyal, a high ticket count (especially negative sentiment) acts as a multiplier of churn risk.
   * **Strategy:** Customers with $> 2$ tickets are automatically routed to our priority customer care queue with dedicated manager callbacks.
2. **Product Return Rates (`return_rate_180d`):**
   * High returns show fit/satisfaction issues.
   * **Strategy:** If a customer's return rate exceeds 30%, we suppress standard discount emails and instead send usage tutorials or size-fit surveys to address product dissatisfaction.

---

## 3. Targeted Campaigns & Financial Rationale

| Segment | Size | Targeted Campaign | Cost per Customer | Expected Lift | Financial Rationale |
| :--- | :---: | :--- | :---: | :---: | :--- |
| **Champions** | 191 | VIP Launch Preview + Referral Code | ₹10 | +5% | High baseline retention. Redundant to send large discounts; prioritize new launch advocacy. |
| **Loyal Customers** | 1,100 | Free Shipping on Orders > ₹999 | ₹15 | +8% | Nudge customers to bundle products, boosting Average Order Value (AOV). |
| **At-Risk** | 195 | High-Incentive Recovery Voucher (₹200 Off) | ₹30 | +15% | High historic spend makes them the most valuable group to save; justifies high campaign cost. |
| **Discount-Sensitive** | 483 | Bundle Discount (Save 15% on 3 items) | ₹25 | +12% | Shifts discount seekers to high-margin bundles, keeping transactions profitable. |
| **Dormant** | 431 | Inactive / Low-priority Email Push | ₹0 | 0% | High acquisition/win-back costs make them a low priority. |

---

## 4. Limited Campaign Budget & Prioritization Guide

If our brand is facing a **limited marketing budget**, we must prioritize capital allocation:

### 🥇 Top Priority: At-Risk Customers
* **Why:** The marginal revenue of saving an At-Risk customer is the highest. Champions are highly active and will buy regardless of campaigns (high dilution risk). Dormant customers are very difficult to activate. 
* By focusing our budget on **At-Risk Customers** first, we prevent high historic spenders from permanently leaving the brand, providing the **highest Net Saved Value per rupee spent**.

### 🥈 Secondary Priority: Loyal Customers
* **Why:** Shielding our active core from competitive pressures secures our baseline revenue.

### 🥉 Tertiary Priority: Discount-Sensitive Customers
* **Why:** With 483 customers (20.1% of the base), this is the second-largest segment. Many exhibit high purchasing potential but are eroding margins through discount dependency. Budget-efficient bundle offers (15% on 3+ items) can shift them toward profitable purchasing patterns without the cost of deep individual discounts.

### ⚠️ Key Segmentation Caveat
* The Discount-Sensitive rule (avg discount $\ge 35\%$) is evaluated **before** the Champions rule in our segmentation logic. This means some customers with Champion-level recency, frequency, and spend are classified as Discount-Sensitive. When designing campaigns for this segment, teams should identify and separately treat these "hidden Champions" — they may respond better to exclusivity-based offers than to bundle discounts.
