---
layout: default
title: Case Study - GEO & Schema
---

# Case Study: GEO & Schema
## The Challenge
A B2B SaaS provider wanted to move beyond tradition blue ink rankings and secure “primary answer” status within AI-driven search environments (Google SGE, Gemini, and ChatGPT). The existing site lacked a machinereadable data layer, making it difficult for LLMs to accurately cite the brand’s specific services and expertise.

## The Zero Waste Solution
1. **Entity Relationship Mapping:** Conducted a gap analysis between site entities and the Google Knowledge Graph to identify missing semantic connections.
2. **Nested Schema Architecture:** Implemented advanced JSON-LD nesting (Organization > Product > Review) to provide explicit context for LLM crawlers and Answer Engines.
3. **Machine-Readable Layering:** Optimized site-wide microdata to ensure search bots can extract mission-critical facts without relying on heavy text-parsing resources.

## Tools Used
* JSON-LD Generator (Custom Schema Nesting)
* Classy Schema (Visualization & Validation)
* Google Rich Results Test
* Schema.org Vocabulary

## The Business Impact
* **AI Entity Recognition:** Improved the "confidence score" for the brand's primary service category in Google’s Knowledge Graph.
* **Rich Snippet Dominance:** Achieved a 100% "Review Snippet" capture rate on the top 20 high-intent service pages.
* **Conversion Lift:** Secured a 22% increase in qualified organic leads by surfacing pricing and ratings directly in the search results.

## The Deep Dive
* **Entity Relationship Mapping**
I began by performing a semantic audit to identify the "Primary Entities" (Organization, Service, and Offer) and their relationships to ensure that Answer Engines could map the brand's authority within the Knowledge Graph.
* **Master JSON-LD Architecture**
I engineered a nested "Graph" script that explicitly connected the B2B Service to the parent Organization, using ```@id``` references to eliminate ambiguity for search crawlers.

```
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "Organization",
      "@id": "https://site.com/#corp",
      "name": "B2B Tech Solutions",
      "logo": "https://site.com/logo.png"
    },
    {
      "@type": "Service",
      "name": "Inventory Management SaaS",
      "provider": {"@id": "https://site.com/#corp"},
      "aggregateRating": {
        "@type": "AggregateRating",
        "ratingValue": "4.9",
        "reviewCount": "215"
      }
    }
  ]
}
```

* **Hybrid Microdata Strategy**
To support legacy environment constraints, I deployed a secondary layer of inline Microdata, ensuring that critical data points like ```aggregateRating``` were surfaced even if the main script was deferred.

```
<div itemscope itemtype="https://schema.org/Service">
  <meta itemprop="serviceType" content="Inventory Management SaaS" />
  
  <div itemprop="aggregateRating" itemscope itemtype="https://schema.org/AggregateRating">
    <span itemprop="ratingValue">4.9</span> stars based on 
    <span itemprop="reviewCount">215</span> reviews.
  </div>

  <div itemprop="offers" itemscope itemtype="https://schema.org/Offer">
    <meta itemprop="priceCurrency" content="USD" />
    <link itemprop="availability" href="https://schema.org/InStock" />
  </div>
</div>
```

* **Visual Prominence Validation**
By securing rich snippets through schema nesting, I transformed standard blue-link search results into high-visibility modules, increasing the site's "Real Estate" on the SERP without requiring new content.

<div style="max-width: 800px; margin: 30px auto; background-color: #FFFFFF; border: 1px solid #E2E8F0; border-radius: 12px; padding: 25px; box-shadow: 0 4px 15px rgba(0,0,0,0.05); text-align: center;">
  <img src="/assets/images/case-studies/geo-schema/schema-comparison.png" 
       alt="SERP Snippet Comparison: No Schema vs. Nested JSON-LD" 
       style="width: 100%; height: auto; display: block; border-radius: 4px;">
  <p style="font-size: 0.8rem; color: #64748B; margin-top: 15px; font-style: italic;">
    <strong>SERP Transformation:</strong> Transitioning from standard text to 4.9-star Rich Snippets resulted in a measurable 20-30% increase in CTR.
  </p>
</div>

<div class="sticky-download-container">
    <a href="/assets/pdfs/geo-schema.pdf" 
       class="sticky-btn-base sticky-view-blue" 
       target="_blank">
        <i class="fas fa-file-pdf"></i>
        <span class="sticky-label">View<br>PDF</span>
    </a>
    <a href="/assets/pdfs/geo-schema.pdf"
          class="sticky-btn-base sticky-download-gray"
          download="Lichtenwald_GEO_Schema_PoC">
               <i class="fas fa-download"></i>
               <span class="sticky-label">Download</span>
     </a>
</div>