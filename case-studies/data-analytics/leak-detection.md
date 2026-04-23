---
layout: default
title: Case Study - The Leak Detection
---
# Case Study: The Leak Detection
## The Challenge
A B2B landing page was receiving high quality organic traffic, but the “Free Trial” sign-up rate was stagnating at 0.5%. The marketing team suspected the copy was the issue, but the data suggested a deeper technical friction point.

## The Zero Waste Solution
1. **Pathing Forensic Audit:** Analyzed GA4 behavioral flow data to identify specific landing pages where high-intent traffic was exiting the funnel during the mobile "Free Trial" signup process.
2. **Technical Root Cause Diagnosis:** Identified a CSS Z-index conflict where the "sticky" header navigation overlapped the form fields specifically during mobile keyboard activation, obstructing the "Submit" button.
3. **Viewport Stability Optimization:** Rectified a viewport shift bug that was displacing the conversion CTA, turning informational traffic back into a qualified revenue stream without increasing acquisition spend.

## Tools Used
* GA4 Exploration Reports (Funnel Visualization)
* Chrome DevTools (Mobile Emulation & CSS Debugging)
* Hotjar / Microsoft Clarity (Session Recording)
* Google Tag Manager (Custom Form Tracking)

## The Business Impact
* **Revenue Restoration:** Recovered an immediate $11,000 MRR increase by fixing the broken mobile conversion path.
* **Friction Elimination:** Reduced the mobile abandonment rate from a critical 98% to industry-standard levels at the final conversion step.
* **Operational Efficiency:** Proved that low conversions were a technical failure rather than a content issue, saving the editorial team from unnecessary rewrites.

## The Deep Dive
* **Friction Discovery**
Using GA4 Funnel Analysis, I identified a catastrophic 98% abandonment rate specifically at the final "Submit" stage of the mobile lead form.

<div style="max-width: 800px; margin: 20px auto; background-color: #FFFFFF; border: 1px solid #E2E8F0; border-radius: 12px; padding: 15px; box-shadow: 0 4px 15px rgba(0,0,0,0.05); text-align: center;">
<img src="/assets/images/case-studies/leak-detection/leak-funnel.png"
alt="GA4 Funnel Analysis showing 98% mobile abandonment"
style="width: 100%; height: auto; display: block; border-radius: 4px;">
<p style="font-size: 0.75rem; color: #64748B; margin-top: 10px; font-style: italic;">
<strong>Image 1:</strong> GA4 data interrogation proving the conversion leak was concentrated on the mobile journey.
</p>
</div>

* **UI/UX Conflict Identification**
Session recordings revealed that when users tapped a form field, the mobile keyboard pushed the "Submit" button behind a fixed header, making it impossible to click.

<div style="max-width: 300px; margin: 20px auto; background-color: #FFFFFF; border: 1px solid #E2E8F0; border-radius: 12px; padding: 15px; box-shadow: 0 4px 15px rgba(0,0,0,0.05); text-align: center;">
<img src="/assets/images/case-studies/leak-detection/mobile-ui-leak.png"
alt="Mobile UI Keyboard Conflict Visualization"
style="width: 100%; height: auto; display: block; border-radius: 4px;">
<p style="font-size: 0.75rem; color: #64748B; margin-top: 10px; font-style: italic;">
<strong>Image 2:</strong> Visualizing the CSS Z-index conflict causing mobile form abandonment.
</p>
</div>

* **Technical Resolution**
I standardized the element layering and viewport logic via CSS to ensure the CTA remains prominent and accessible regardless of keyboard state.

```
/* Fixing the Mobile Z-Index & Header Conflict */

.sticky-header {
    z-index: 10; /* Lowered from 9999 to allow form prominence */
}

.mobile-form-container {
    position: relative;
    z-index: 50;
    padding-bottom: env(safe-area-inset-bottom); /* Fix for iOS viewport shifts */
}

@media screen and (max-height: 500px) {
    .sticky-header {
        position: static; /* Removes stickiness when keyboard is active to save screen space */
    }
}
```

* **Economic Validation**
Post-resolution data confirmed an immediate 22% lift in lead volume, effectively salvaging $132k in annual recurring revenue (ARR) with zero additional marketing spend.

<div class="sticky-download-container">
    <a href="/assets/pdfs/leak-detection.pdf" 
       class="sticky-btn-base sticky-view-blue" 
       target="_blank">
        <i class="fas fa-file-pdf"></i>
        <span class="sticky-label">View<br>PDF</span>
    </a>
    <a href="/assets/pdfs/leak-detection.pdf"
          class="sticky-btn-base sticky-download-gray"
          download="Lichtenwald_Leak_Detection_PoC">
               <i class="fas fa-download"></i>
               <span class="sticky-label">Download</span>
     </a>
</div>