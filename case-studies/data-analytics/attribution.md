---
layout: default
title: Case Study - Multi-Touch Attribution Modeling
---
# Case Study: Multi-Touch Attribution Modeling
## The Challenge
A SaaS company was over investing in paid search because it appeared to be the primary driver of leads. However, the last-click model was ignoring the role of organic content in the early research phases of the 6-month sales cycle.

## The Zero Waste Solution
1. **Cross-Channel Data Stitching:** Integrated GA4 BigQuery exports with CRM data to map the complete user journey, moving beyond fragmented "session-only" views.
2. **Attribution Logic Overhaul:** Deconstructed the "Last Click" bias by implementing a data-driven model that correctly assigns value to top-of-funnel educational content.
3. **Budget Rationalization:** Visualized the SEO-to-Revenue pipeline in a custom dashboard, providing stakeholders with clear evidence of organic search’s multi-touch impact.

## Tools Used
* GA4 BigQuery Export (Raw Data Interrogation)
* SQL (User-Stitching & Data Joining)
* Looker Studio (Attribution Comparison Dashboards)
* Microsoft Excel (Assisted/Last Click Ratio Modeling)

## The Business Impact
* **Revenue Discovery:** Identified an additional $65,000/month in organic value previously misattributed to paid search.
* **Strategic Expansion:** Secured budget approval for a 40% increase in content production by proving long-term assisted conversion value.
* **Lead Accuracy:** Verified that 65% of converted leads originated from Organic Search, correcting a significant under-reporting error.

## The Deep Dive
* **The "Last Click" Fallacy**
I audited the existing reporting structure and found that Paid Search was receiving 100% of the credit for conversions that actually started with a Day 1 Organic discovery.

<div style="max-width: 800px; margin: 20px auto; background-color: #FFFFFF; border: 1px solid #E2E8F0; border-radius: 12px; padding: 25px; box-shadow: 0 4px 15px rgba(0,0,0,0.05); text-align: center;">
<img src="/assets/images/case-studies/attribution/attribution-touchpoints.jpg"
alt="Multi-Touch Attribution Journey Visualization"
style="width: 100%; height: auto; display: block; border-radius: 4px;">
<p style="font-size: 0.8rem; color: #64748B; margin-top: 15px; font-style: italic;">
<strong>Visualization:</strong> Mapping the 16-day journey from Organic discovery to Paid conversion.
</p>
</div>

* **Data Modeling & Interrogation**
Using SQL to join touchpoints, I compared the traditional "Last Click" revenue against a "Data-Driven" model. The results showed that Organic Search was functioning as the primary "Opener" for the entire ecosystem.

<div style="display: flex; flex-wrap: wrap; justify-content: center; gap: 30px; margin: 30px 0;">

  <div style="flex: 1; min-width: 320px; max-width: 480px; background-color: #FFFFFF; border: 1px solid #E2E8F0; border-radius: 12px; padding: 20px; box-shadow: 0 4px 15px rgba(0,0,0,0.05); text-align: center;">
    <h4 style="margin-top: 0; color: #1e293b; font-size: 0.9rem; text-transform: uppercase; letter-spacing: 1px;">Model A: Last Click</h4>
    <img src="/assets/images/case-studies/attribution/attribution-comparison1.png" 
         alt="Last Click Attribution Model - Unbalanced Revenue" 
         style="width: 100%; height: auto; display: block; border-radius: 4px; border: 1px solid #F1F5F9;">
    <p style="font-size: 0.75rem; color: #64748B; margin-top: 10px; font-style: italic;">
      Organic Search undervalued at $25k. Paid Search claims 100% credit.
    </p>
  </div>

  <div style="flex: 1; min-width: 320px; max-width: 480px; background-color: #FFFFFF; border: 1px solid #E2E8F0; border-radius: 12px; padding: 20px; box-shadow: 0 4px 15px rgba(0,0,0,0.05); text-align: center; border-left: 4px solid #2563EB;">
    <h4 style="margin-top: 0; color: #1e293b; font-size: 0.9rem; text-transform: uppercase; letter-spacing: 1px;">Model B: Data-Driven</h4>
    <img src="/assets/images/case-studies/attribution/attribution-comparison2.png" 
         alt="Data-Driven Attribution Model - Balanced Revenue" 
         style="width: 100%; height: auto; display: block; border-radius: 4px; border: 1px solid #F1F5F9;">
    <p style="font-size: 0.75rem; color: #64748B; margin-top: 10px; font-style: italic;">
      True organic value of $90k revealed by tracing the full path.
    </p>
  </div>

</div>

* **Assisted/Last Click Ratio**
I calculated the "Assisted Ratio" for every channel. A ratio of 2.58 for Organic Search confirmed that for every 1 direct conversion, it assisted 2.5 others—proving it was the "engine" of the site.

```
/* SQL: Calculating Assisted Conversion Ratios */
SELECT 
    channel_grouping,
    last_click_conversions,
    assisted_conversions,
    ROUND(SAFE_DIVIDE(assisted_conversions, last_click_conversions), 2) AS assisted_ratio
FROM `analytics_data.attribution_summary`
WHERE conversions > 0
ORDER BY assisted_ratio DESC;
```

* **Strategic Re-Alignment**
Based on these insights, I transitioned the SEO strategy from a "defensive" posture to an "expansion" model, focusing on the informational topics that drove the highest assisted ROI.

<div class="sticky-download-container">
    <a href="/assets/pdfs/multi-touch-attribution.pdf" 
       class="sticky-btn-base sticky-view-blue" 
       target="_blank">
        <i class="fas fa-file-pdf"></i>
        <span class="sticky-label">View<br>PDF</span>
    </a>
    <a href="/assets/pdfs/multi-touch-attribution.pdf"
          class="sticky-btn-base sticky-download-gray"
          download="Lichtenwald_Multi_Touch_Attribution_PoC">
               <i class="fas fa-download"></i>
               <span class="sticky-label">Download</span>
     </a>
</div>