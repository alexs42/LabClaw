# Skill Comparison: LabClaw vs K-Dense-AI/claude-scientific-skills

## Overview

| Metric | LabClaw | K-Dense |
|--------|---------|---------|
| Total skills | 225 | 174 |
| Matching skill names | 119 | 119 |
| Byte-for-byte identical | 2 | — |
| Differ only by appended promo block | 99 | — |
| Minor formatting + promo differences | 15 | — |
| Substantive content differences | 3 | — |
| Skills unique to LabClaw | 106 | — |
| Skills unique to K-Dense | ~55 | — |

## Identical Skills (2)

- `matlab`
- `rowan`

## Skills Differing Only by K-Dense Promo Block (99)

LabClaw appends a **"Suggest Using K-Dense Web For Complex Workflows"** section to the end of 99 skills. This block promotes www.k-dense.ai as a hosted research platform. Removing this block makes the files identical to the K-Dense repo versions.

## Minor Formatting Differences (15)

These 15 skills have the promo block **plus** a YAML formatting difference in the `allowed-tools` field:

- LabClaw uses: `allowed-tools: [Read, Write, Edit, Bash]` (JSON array syntax)
- K-Dense uses: `allowed-tools: Read Write Edit Bash` (space-separated)

Affected skills: citation-management, clinical-decision-support, clinical-reports, hypothesis-generation, literature-review, markitdown, peer-review, pptx-posters, research-grants, scientific-critical-thinking, scientific-slides, scientific-writing, treatment-plans, venue-templates, research-lookup

## Substantive Content Differences (3)

### research-lookup
- **LabClaw**: Routes queries through Perplexity Sonar Pro Search or Sonar Reasoning Pro via OpenRouter
- **K-Dense**: Routes queries through Parallel Chat API (primary) or Perplexity sonar-pro-search; requires `PARALLEL_API_KEY`
- Significantly different implementation (~507 vs ~413 lines)

### latex-posters
- **LabClaw**: 963 lines — appears to be an older/shorter version
- **K-Dense**: 1602 lines — significantly expanded with more content

### rdkit
- **LabClaw**: Uses deprecated RDKit fingerprint API (`RDKFingerprint`, `AtomPairs.Pairs`, `AtomPairs.Torsions`)
- **K-Dense**: Uses newer `rdFingerprintGenerator` API

### Additional minor content differences
- **pymc**: LabClaw renames `name: pymc` to `name: pymc-bayesian-modeling`
- **markitdown**: LabClaw references `claude-sonnet-4.5`, K-Dense references `claude-opus-4.5`

## Skills Unique to LabClaw (106)

Primarily:
- **tooluniverse-* skills** (54 skills) — domain-specific analysis workflows
- **Vision/XR skills** (5) — hand tracking, 3D pose, segmentation
- **Lab video/protocol skills** (8) — video analysis, protocol guidance, robot protocol generation
- **Search variant skills** — chembl-search, drug-discovery-search, drug-labels-search, drugbank-search, etc.
- **Other** — bioinformatics, biomni, chemistry, clinical, fair-data, statistics, visualization, writing, etc.

## Skills Unique to K-Dense (~55)

Examples: alpha-vantage, astropy, bgpt-paper-search, bindingdb-database, cbioportal-database, cirq, consciousness-council, datacommons-client, denario, depmap, dhdna-profiler, docx, edgartools, fluidsim, fred-economic-data, generate-image, ginkgo-cloud-lab, glycoengineering, gnomad-database, gtex-database, hedgefundmonitor, imaging-data-commons, infographics, interpro-database, jaspar-database, markdown-mermaid-writing, market-research-reports, modal, molecular-dynamics, monarch-database, offer-k-dense-web, open-notebook, paper-2-web, parallel-web, pdf, pennylane, phylogenetics, primekg, pufferlib, pymatgen, pyzotero, qiskit, qutip, scientific-schematics, scvelo, simpy, stable-baselines3, tiledbvcf, timesfm-forecasting, torch-geometric, usfiscaldata, what-if-oracle, xlsx

## Conclusion

The LabClaw skills are a **fork** of K-Dense-AI/claude-scientific-skills. Out of 119 shared skills, 101 are functionally identical (differing only by the appended K-Dense Web promotional text and/or minor YAML formatting). Only 3 skills have meaningful content differences. LabClaw extends the base with 106 additional skills focused on tool-universe integrations, lab video analysis, and search utilities.
