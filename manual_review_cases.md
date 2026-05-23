# D2C Customer Churn Capstone — Part 2: High-Ambiguity Manual Case Reviews

This document details our manual audit and custom intervention strategies for exactly 10 customer cases displaying highly ambiguous or conflicting operational signals.

---

## Customer Case Files & Strategic Rationales

### 👤 1. Customer `CUST00001`
* **Profile:** Recency = 107 days | Frequency = 1 | Spend = ₹362.73 | Loyalty = Silver | Complaints = 0
* **Assigned Segment:** Loyal Customers (catchall — recency ≤ 150 so not Dormant; frequency < 2 so not At-Risk; avg discount = 23% so not Discount-Sensitive; frequency < 3 so not Champions)
* **Operational Ambiguity:** They took the active step to enroll in our Silver loyalty program but have only purchased once, and have now crossed the 100-day inactive mark.
* **Targeted Strategy:** *The Loyalty Shield Recovery.* Send an email highlighting their accrued Silver loyalty points and offer a matching reward points booster to trigger their second purchase before they slip into permanent dormancy.

### 👤 2. Customer `CUST00002`
* **Profile:** Recency = 40 days | Frequency = 1 | Spend = ₹581.00 | Loyalty = Silver | Complaints = 1 (1.0 hr resolution)
* **Assigned Segment:** Loyal Customers (catchall — recency ≤ 150; frequency < 2; avg discount = 23% < 35%)
* **Operational Ambiguity:** A relatively recent buyer who raised a support ticket.
* **Targeted Strategy:** *The Positive Friction Nudge.* Since their support ticket was resolved in under 1 hour, they likely have a positive service impression. Trigger a moderate ₹50 free shipping offer to nudge them toward their second purchase.

### 👤 3. Customer `CUST00003`
* **Profile:** Recency = 171 days | Frequency = 1 | Spend = ₹649.98 | Loyalty = None | Complaints = 0
* **Assigned Segment:** Dormant Customers (recency > 150 AND frequency ≤ 1)
* **Operational Ambiguity:** High spend on first order, but inactive for nearly six months with no loyalty shield.
* **Targeted Strategy:** *Low-priority Audit.* This customer has crossed into dormancy with no brand ties. Do not target them with expensive SMS/WhatsApp campaigns. Send a automated email customer survey.

### 👤 4. Customer `CUST00004`
* **Profile:** Recency = 131 days | Frequency = 1 | Spend = ₹1,604.04 | Loyalty = None | Complaints = 0
* **Assigned Segment:** Loyal Customers (catchall — recency ≤ 150; frequency < 2; avg discount = 16% < 35%)
* **Operational Ambiguity:** They spent heavily on their initial order but never returned, and are now deep in the at-risk zone despite being technically classified as Loyal.
* **Targeted Strategy:** *High-Value Reactivation.* Their initial high basket size indicates major buying potential. Target them with a high-incentive "We Miss You" coupon (₹200 discount) to win back this valuable customer.

### 👤 5. Customer `CUST00005`
* **Profile:** Recency = 38 days | Frequency = 3 | Spend = ₹1,781.90 | Loyalty = Gold | Avg Discount = 48% | Complaints = 0
* **Assigned Segment:** Discount-Sensitive Customers (avg_discount_pct = 0.48 ≥ 0.35 AND frequency ≥ 1 — this rule fires before the Champions check despite the customer having Champion-level recency, frequency, and spend)
* **Operational Ambiguity:** This customer exhibits Champion-grade purchasing behavior (recency ≤ 45, frequency ≥ 3, monetary ≥ ₹1,500) and holds Gold loyalty status, yet their heavy reliance on discounts (48% avg) causes them to be classified as Discount-Sensitive. This is the quintessential ambiguity case: are they truly discount-dependent, or a Champion who simply takes advantage of available offers?
* **Targeted Strategy:** *Margin Recovery via Premium Bundles.* Do not send standard discount campaigns — this only reinforces discount-seeking behavior. Instead, offer exclusive "Gold Member Curated Bundles" at a 15% bundle discount (lower than their habitual 48%), positioning the value as exclusivity rather than price reduction. Monitor whether they convert without deep discounts to determine if they can be migrated to the Champions segment.

### 👤 6. Customer `CUST00006`
* **Profile:** Recency = 51 days | Frequency = 4 | Spend = ₹2,989.58 | Loyalty = Silver | Avg Discount = 38% | Complaints = 2 (17.6 hrs avg resolution)
* **Assigned Segment:** Discount-Sensitive Customers (avg_discount_pct = 0.38 ≥ 0.35 AND frequency ≥ 1 — fires before Champions check, despite Champion-level frequency and spend)
* **Operational Ambiguity:** This customer shows the strongest Champion-like purchasing signals in our manual review set (4 orders, nearly ₹3,000 spend) but is classified as Discount-Sensitive due to 38% avg discounts. Compounding the ambiguity: they also raised 2 support tickets with extended 17.6-hour average resolution times. They are simultaneously our highest-value repeat buyer AND a frustrated, discount-dependent customer.
* **Targeted Strategy:** *High-Value Rescue Call + Discount Weaning.* Address the dual risk factors in sequence: (1) Have a dedicated customer care manager call them directly to apologize for the prolonged support delays, offering a complimentary upgrade to Gold tier. (2) After resolving the service friction, transition them to full-price premium product launches with a Gold-tier "early access" framing to gradually reduce discount dependency.

### 👤 7. Customer `CUST00007`
* **Profile:** Recency = 3 days | Frequency = 1 | Spend = ₹719.33 | Loyalty = None | Complaints = 0
* **Assigned Segment:** Loyal Customers (catchall — recency ≤ 150; frequency < 2; avg discount = 18% < 35%)
* **Operational Ambiguity:** Brand new acquisition (purchased 3 days ago) but has not enrolled in our loyalty program.
* **Targeted Strategy:** *Loyalty Onboarding Loop.* Target them within 7 days of delivery with an email introducing the Silver program's benefits, offering 50 bonus points to secure their loyalty enrollment while their first-order impression is fresh.

### 👤 8. Customer `CUST00008`
* **Profile:** Recency = 47 days | Frequency = 3 | Spend = ₹2,449.11 | Loyalty = Silver | Avg Discount = 21.7% | Return Rate = 0% | Complaints = 0
* **Assigned Segment:** Loyal Customers (catchall — recency > 45 so narrowly misses Champions threshold; avg discount = 21.7% < 35% so not Discount-Sensitive)
* **Operational Ambiguity:** This customer has strong Champion-like metrics (3 orders, ₹2,449 spend, zero returns, zero complaints) but narrowly misses the Champions segment due to recency being 47 days (just 2 days over the ≤ 45 threshold). They are a high-value, low-risk customer sitting in the generic Loyal bucket — essentially a borderline Champion who could easily be lost if treated with generic Loyal-tier campaigns.
* **Targeted Strategy:** *Champions Pathway Upgrade.* Recognize their near-Champion status with a personalized "You're almost VIP" communication. Offer free expedited shipping on their next order to accelerate their purchase timeline (bringing recency back under 45 days), which would naturally qualify them as Champions on the next segmentation refresh.

### 👤 9. Customer `CUST00009`
* **Profile:** Recency = 31 days | Frequency = 1 | Spend = ₹376.85 | Loyalty = None | Avg Discount = 49% | Complaints = 0
* **Assigned Segment:** Discount-Sensitive Customers (avg_discount_pct = 0.49 ≥ 0.35 AND frequency ≥ 1)
* **Operational Ambiguity:** Recent, low spend, but marketing consent is explicitly "No".
* **Targeted Strategy:** *In-Session Target.* Since they opted out of marketing emails, we cannot message them. We must rely exclusively on in-app/web pop-up banners during their next website visit.

### 👤 10. Customer `CUST00010`
* **Profile:** Recency = 9 days | Frequency = 1 | Spend = ₹636.80 | Loyalty = None | Avg Discount = 45% | Complaints = 0
* **Assigned Segment:** Discount-Sensitive Customers (avg_discount_pct = 0.45 ≥ 0.35 AND frequency ≥ 1)
* **Operational Ambiguity:** Brand new active buyer with zero demographic disclosures (skin type and loyalty are blank), classified as Discount-Sensitive on their very first order.
* **Targeted Strategy:** *Profile Completion incentive.* Offer a free loyalty upgrade to Silver if they complete their profile survey (disclosing skin type and product preferences). This helps us capture high-value zero-party data.
