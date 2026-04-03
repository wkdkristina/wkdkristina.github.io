---
layout: default
title: Case Study - SQL Powered Content Decay Dashboard
---
# Case Study: SQL Powered Content Decay Dashboard
## The Challenge
A large scale blog with 500+ articles was losing 10% of its total traffic month-over-month, but the team couldn’t identify which specific posts were failing until it was too late.

## The Zero Waste Solution
1. **Algorithmic Decay Detection:** Engineered a BigQuery SQL script to programmatically detect "content decay" by correlating stable impressions with declining CTR and average position.
2. **Automated Governance:** Built a Looker Studio pipeline to deliver weekly "Traffic Health" reports, eliminating manual auditing and editorial guesswork.
3. **Strategic Pivot:** Transitioned the team to a 70/30 production model (70% new, 30% data-backed refreshes) to stabilize the "leaky bucket" of legacy traffic.

## Tools Used
* Google BigQuery (SQL Data Engineering)
* Google Search Console API
* Looker Studio (Automated Reporting)
* Google Sheets (Priority Action Mapping)

## The Business Impact
* **Quantifiable Growth:** Reversed a year-long plateau to achieve 14% net organic growth within one quarter by protecting high-value legacy assets.
* **Operational Scalability:** Engineered a "set-and-forget" system capable of managing 100 to 100,000+ URLs with zero additional overhead.
* **Revenue Protection:** Moved from reactive "intuition" to proactive "Pre-emptive Revenue Protection," saving hundreds of manual hours per year.

## The Deep Dive
* **Bypassing UI Limitations**
Standard SEO tools often truncate historical data or make year-over-year URL-level comparisons difficult. By exporting raw performance data into BigQuery, I was able to identify the exact moment a high-ranking article began to "cool off."
* **The Decay Query**
I developed a custom SQL workflow to calculate the percentage change in clicks over a 90-day rolling window, filtering for pages that still had high impressions but failing engagement.

```
/* SQL: Identifying Content Decay */
SELECT 
    page_url,
    clicks_last_90_days,
    clicks_previous_90_days,
    ((clicks_last_90_days - clicks_previous_90_days) / NULLIF(clicks_previous_90_days, 0)) * 100 AS pct_change
FROM `search_console_data`
WHERE clicks_last_90_days < clicks_previous_90_days
  AND clicks_previous_90_days > 100
ORDER BY pct_change ASC
LIMIT 10;
```

* **Priority Action Mapping**
Rather than a generic list, the data was categorized by "Trend Severity." This allowed the editorial team to focus on "Critical" updates (rank 7 was rank 2) where the ROI of a refresh was highest.

<div style="max-width: 800px; margin: 20px auto; background-color: #FFFFFF; border: 1px solid #E2E8F0; border-radius: 12px; padding: 20px; box-shadow: 0 4px 15px rgba(0,0,0,0.05); text-align: center;">
<img src="/assets/images/case-studies/decay-dashboard/decay-priority.png"
alt="Content Decay Priority Matrix"
style="width: 100%; height: auto; display: block; border-radius: 4px;">
<p style="font-size: 0.75rem; color: #64748B; margin-top: 10px; font-style: italic;">
<strong>Evidence:</strong> Automated trend tracking that separates "Stable" assets from "Critical" revenue risks.
</p>
</div>

* **Engineered vs. Manual Workflow**
By moving from a reactive "intuition" model to a proactive "Engineered Pipeline," we reduced time spent on audits by nearly 90%, allowing the team to spend their energy on high-impact updates.

<div style="max-width: 800px; margin: 20px auto; background-color: #FFFFFF; border: 1px solid #E2E8F0; border-radius: 12px; padding: 20px; box-shadow: 0 4px 15px rgba(0,0,0,0.05); text-align: center;">
<img src="/assets/images/decay-workflow.png"
alt="Manual vs Engineered Workflow Comparison"
style="width: 100%; height: auto; display: block; border-radius: 4px;">
<p style="font-size: 0.75rem; color: #64748B; margin-top: 10px; font-style: italic;">
<strong>Strategic Shift:</strong> Transitioning from reactive "Intuition" to automated "Revenue Protection."
</p>
</div>

