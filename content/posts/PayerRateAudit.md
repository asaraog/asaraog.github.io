---
title: Payer Rate Audit
date: 2026-08-30T15:30:00-07:00
draft: false
projects: dataengineering
featuredImage: /images/payer-rate-audit.svg
---
## Comparing insurance contracts on rate alone using public CMS data

**Abstract**

Payer Rate Audit is a healthcare finance tool that answers a question every medical practice has: which insurer actually pays best? Dollar totals cannot answer it, because different payers cover different patients getting different services. The tool divides what each payer pays by the relative value units (RVUs) of the work, Medicare's public per-code work weights, so every payer becomes one comparable number: dollars per unit of work, as a multiple of Medicare.

It reads two public inputs. Every US hospital is legally required to publish a machine-readable file of its payer-negotiated rates, and CMS publishes the RVU table for every billing code. Joining the two on HCPCS gives each payer's effective conversion factor with the case mix normalized out.

Run against one rural hospital's published file, the spread was 2.2x between the best and worst contract for the same procedures. One skin-lesion excision code ranged from $318 to $4,977 across payers.

The tool also reprices a practice's own service mix. An X12 835 reader takes the remittance files a clearinghouse already delivers and shows what the practice's actual services would have paid at each payer's posted rates, turning a contract negotiation into a dollar figure. A FHIR ExplanationOfBenefit reader does the same for institutions.

I built the scaffold with Devin, then reviewed and corrected it with Claude Code. The corrections were domain judgment from my billing work: which RVU column applies to which billing class, which modifiers carry their own RVU rows, and why percentage-based charges must be excluded rather than converted to invented dollars. Every judgment call is documented in the repository, each one overturnable in a single pass.

To run locally:

```
git clone https://github.com/asaraog/payer-rate-audit.git
cd payer-rate-audit
pip install -e .
python scripts/fetch_rvu.py
payer-rate-audit your_hospital_file.csv
```

See my [Github repository](https://github.com/asaraog/payer-rate-audit) for all code. No PHI is used anywhere: inputs are public files and synthetic fixtures.
