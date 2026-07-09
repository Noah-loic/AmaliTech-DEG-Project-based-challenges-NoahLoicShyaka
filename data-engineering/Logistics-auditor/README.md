# The Last Mile Logistics Auditor — Submission

---

## A. Executive Summary

This audit of Veridi Logistics' delivery data reveals that approximately 6.8% of the 96,470 delivered orders arrived late, with 3,764 orders classified as "Super Late" (more than 5 days past the estimated date). The problem is not evenly distributed — states in Brazil's North and Northeast, particularly AL (~21%), MA (~17%), and SE (~15%), show disproportionately high late delivery rates, confirming that remote regions far from distribution centers are most affected. Late deliveries have a measurable and severe impact on customer satisfaction: On Time orders average a review score of ~4.2 out of 5, while Super Late orders average just ~1.6. Monthly trend analysis shows the late delivery rate was broadly stable between 5–15% throughout 2017 and most of 2018, with an anomalous spike in the final months of the dataset likely caused by very low order volume in that period.

---

## B. Project Links

- **Link to Notebook:** *([Jupyter notebook](https://github.com/Noah-loic/AmaliTech-DEG-Project-based-challenges-NoahLoicShyaka/blob/main/data-engineering/Logistics-auditor/olist_logistics_audit.ipynb))*
- **Link to Dashboard:** *([Tabeau public](https://public.tableau.com/views/VeridiLogisticsAudit_17836095616720/VeridiLogisticsDeliveryPerformanceAudit?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link))*
- **Link to Presentation:** *([googlesheet presentation ](https://docs.google.com/presentation/d/17fV26TTqNRVwJLZ7MB1ioIOpU1IefR5_/edit?usp=sharing&ouid=118418320706272983328&rtpof=true&sd=true))*

---

## C. Technical Explanation

**Data Cleaning:**
The reviews table contained duplicate `order_id` entries (multiple reviews per order), so it was deduplicated using `drop_duplicates(subset='order_id', keep='last')` before joining to orders. All joins were performed as left joins to preserve all orders even where review or customer data was missing. Orders with `order_status` of `canceled` or `unavailable` were excluded before calculating delivery delay. Rows missing either the actual or estimated delivery date were dropped before computing `days_difference` to avoid NaN propagation.

**Candidate's Choice — Monthly Trend of Late Deliveries:**
I added a monthly trend line showing the percentage of late deliveries over time. This answers the CEO's key question: *"Is the problem getting better or worse?"* By grouping delivered orders by month and calculating the proportion that were not On Time, the chart reveals whether the late delivery rate is improving, worsening, or holding steady — information that is essential for deciding whether an intervention is working.

---

## 🛑 CRITICAL: Pre-Submission Checklist

**Before you submit your form, you MUST complete this checklist.**

> ⚠️ **WARNING:** If you miss any of these items, your submission will be flagged as "Incomplete" and you will **NOT** be invited to an interview.
>
> **We do not accept "permission error" excuses. Test your links in Incognito Mode.**

### 1. Repository & Code Checks

- [✅ ] **My GitHub Repo is Public.** (Open the link in a Private/Incognito window to verify).
- [✅ ] **I have uploaded the `.ipynb` notebook file.**
- [✅ ] **I have ALSO uploaded an HTML or PDF export** of the notebook.
- [ ✅] **I have NOT uploaded the massive raw dataset.** (Use `.gitignore` or just don't commit the CSV).
- [ ✅] **My code uses Relative Paths.**

### 2. Deliverable Checks

- [✅ ] **My Dashboard link is publicly accessible.** (No login required).
- [✅ ] **My Presentation link is publicly accessible.** (Permissions set to "Anyone with the link can view").
- [✅ ] **I have updated this `README.md` file** with my Executive Summary and technical notes.

### 3. Completeness

- [✅ ] I have completed **User Stories 1-4**.
- [✅ ] I have completed the **"Candidate's Choice"** challenge and explained it in the README.

**✅ Only when you have checked every box above, proceed to the submission form.**

---
