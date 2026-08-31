---
title: Payer Rate Audit
date: 2026-08-30T15:30:00-07:00
draft: false
projects: dataengineering
featuredImage: /images/payer-rate-audit.svg
---
## Comparing insurance contracts on rate alone using public CMS data

**Abstract**

Payer Rate Audit answers a question every medical practice has: which insurer actually pays best? Dollar totals cannot answer it, because different payers cover different patients getting different services. The tool divides what each payer pays by relative value units (RVUs), Medicare's public per-code work weights. Every payer becomes one number: dollars per unit of work, as a multiple of Medicare.

Both inputs are public. Every US hospital must publish its payer-negotiated rates, and CMS publishes the RVU table. Run against one rural hospital's file, the spread was 2.2x between the best and worst contract for the same procedures. One excision code ranged from $318 to $4,977 across payers.

The tool also reprices a practice's own service mix from the X12 835 remittance files a clearinghouse already delivers, turning a contract negotiation into a dollar figure. I built the scaffold with Devin and corrected it with Claude Code. The corrections were billing domain judgment.

To run locally:

```
git clone https://github.com/asaraog/payer-rate-audit.git
cd payer-rate-audit
pip install -e .
python scripts/fetch_rvu.py
payer-rate-audit your_hospital_file.csv
```

See my [Github repository](https://github.com/asaraog/payer-rate-audit) for all code. No PHI is used anywhere: inputs are public files and synthetic fixtures.
