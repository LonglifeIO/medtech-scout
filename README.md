# MedTech Scout — FDA 510(k) Intelligence Extractor

A proof-of-concept tool that demonstrates how public regulatory data can be
transformed into actionable sales intelligence for MedTech service providers.

Built as a data source gap analysis for **Zapyrus by Lumerate**.

## What It Does

1. **Fetches** recent FDA 510(k) device clearances from the openFDA API
2. **Enriches** each clearance with LLM-powered classification:
   - Therapeutic area mapping
   - Device category classification
   - Technology keyword extraction
   - Commercial stage assessment (early/growth/established)
   - Service opportunity identification (CRO, CDMO, regulatory, etc.)
   - Actionable sales trigger summaries
   - Urgency scoring (1-5)
3. **Outputs** a polished spreadsheet with three tabs:
   - **Sales Intelligence** — the enriched, actionable report
   - **Data Source Gaps** — 8 data sources Zapyrus could integrate
   - **Raw 510(k) Data** — unprocessed FDA data for reference

## Quick Start

```bash
# Install dependencies
pip install -r requirements.txt

# Set your API key
export ANTHROPIC_API_KEY="sk-ant-..."

# Run with built-in data (real FDA clearances, no API needed)
python medtech_scout.py

# Run live against the FDA API
python medtech_scout.py --live

# Customize: last 60 days, up to 50 results
python medtech_scout.py --live --days 60 --limit 50
```

**Don't want to run it?** Check [`sample_output/`](sample_output/) for pre-generated results from real FDA 510(k) clearances (Feb 2026).

## Why This Matters for Zapyrus

Zapyrus currently tracks press releases, funding, clinical milestones, M&A,
conferences, and device approvals. But the raw FDA submission databases contain
**earlier and more granular signals** than press coverage:

- Submission dates reveal regulatory intent months before clearance
- Predicate device references map competitive positioning
- Clearance types (Traditional / Special / De Novo) indicate novelty
- Expedited review flags signal clinical urgency
- Third-party review flags suggest smaller companies needing external partners

Combined with LLM classification, this turns a regulatory database into a
**predictive sales intelligence feed** — exactly what Zapyrus does for other
data sources.

## Data Source Gap Summary

| Source | Signal Type | Integration Difficulty |
|--------|------------|----------------------|
| EUDAMED (EU Device Database) | Regulatory | Medium |
| USPTO / EPO / WIPO Patents | IP / R&D | Medium |
| SEC EDGAR / SEDAR+ Filings | Financial / Strategic | Low-Medium |
| WHO ICTRP (Intl Clinical Trials) | Clinical | Low |
| SAM.gov / MERX / TED Procurement | Intent / Budget | Medium |
| Accelerator Cohort Announcements | Company Discovery | Low |
| FDA 510(k) / PMA Raw Databases | Regulatory / Predictive | Low |
| Job Posting Data as Lifecycle Signal | Intent / Lifecycle | Medium-High |

---

*Built by Gordon — [github.com/LonglifeIO](https://github.com/LonglifeIO)*
