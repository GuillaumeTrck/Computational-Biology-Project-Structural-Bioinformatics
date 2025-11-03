# Computational Biology Project — Structural Bioinformatics

This repository contains a structural bioinformatics project carried out during my 2nd year of a master's degree at the Haute école en Hainaut in 2024. It covers: assessment of experimental structures, enzyme–ligand analysis, domain classification, secondary-structure prediction benchmarking, and comparative 3D modeling workflows.

## Overview
- Scope: analyze biomolecular structures, classify domains, predict secondary structure, and build/evaluate comparative models (manual, semi-automatic, automatic), with fold recognition and AlphaFold comparisons.
- Deliverables: PDF reports (final report + practicals brief), plus optional exported figures to quickly preview insights.
- Skills: PyMOL workflows, sequence/structure alignment, Modeller pipelines, model quality assessment (QMEAN/QMEANDisCo, Ramachandran/validation), critical analysis.

## Repository layout
- `docs/Report_Final.pdf` — final report (figures, methods, results, discussion).
- `docs/Project_Specs.pdf` — practicals/assignment brief.

## Part 1 — Structure analysis
- Compared X-ray vs NMR structures (e.g., 1N0S vs 1T0V): resolution, R-factors, validation plots, Ramachandran outliers, conformer variability.
- Enzyme–ligand case (e.g., 1DG5 + trimethoprim): identified interacting residues, inspected binding pocket, and measured contact distances in PyMOL.
- Protein core compactness: mutagenesis to Phe at a core position showed steric clashes, illustrating packing constraints.

## Part 2 — Domain classification and alignment
- Long multi-domain protein (e.g., Uniprot Q12923): PDZ domain mapping; no full experimental structure, but AlphaFold available.
- Classification: CATH and family annotations confirm PDZ domains (beta-rich “roll” architecture) and protein–protein binding function.
- Alignments:
  - MSA (Clustal Omega) and global/local alignments (Needle/Matcher) to quantify identity/similarity and gap patterns.
  - Structural superposition (PDBeFold) with Z-score/RMSD interpretation; local alignments capture domain-level similarity better than global full-length comparisons.

## Part 3 — Secondary structure prediction
- Tools summarized:
  - GOR IV: information-theoretic, windowed statistics.
  - HNN: neural network-based.
  - Sympred: consensus across predictors.
- Benchmark on PDB target (e.g., 1E2F): clarified why PDBSum vs PDB annotations differ (criteria/thresholds).
- Two “unknown” sequences (identified via BLAST): Sympred typically closest to native, but all methods show limitations in divergent regions.

## Part 4 — 3D structure prediction and evaluation
- Manual comparative modeling: BLAST template selection, Needle alignment (high identity, few gaps), Modeller build, QMEAN/QMEANDisCo near native-like for best cases.
- Semi-automatic: HHPred → Modeller; rapid pipeline, moderate quality, plausible global fold with weaker regions.
- Automatic: SWISS-MODEL using close templates; strong GMQE/QMEANDisCo indicating reliable models.
- Fold recognition: GenThreader converged on templates similar to manual/automatic picks.
- AlphaFold: global confidence moderate; pairwise RMSDs show automatic vs AlphaFold are the closest pairing.

## Minimal reproduction guide
- Structure validation/visualization:
  - Download PDB entries; in PyMOL reproduce: cartoon/sticks, electron density overlay (for X-ray), selections, surface views, measurement tool for distances, basic mutagenesis to illustrate clashes.
- Alignments:
  - MSA: Clustal Omega (FASTA inputs).
  - Global: EMBOSS Needle.
  - Local: EMBOSS Matcher.
  - Structure: PDBeFold for Z-score/RMSD; use PyMOL `super` to inspect regions with largest deviations.
- Modeling:
  - Manual: BLAST → Needle → PIR → Modeller → QMEAN/QMEANDisCo.
  - Semi-auto: HHPred → Modeller.
  - Automatic: SWISS-MODEL.
  - Compare models by RMSD (PyMOL `super`) and summarize in a small table.

## Notes and limitations
- Exact numbers may vary due to database/tool versions and parameters.
- Figures in `docs/Report_Final.pdf` are authoritative; consider exporting 3–5 key PNGs into `figures/` and embedding them here for quick scanning.
- If data or server outputs cannot be redistributed, keep the pipeline steps and parameters documented for transparent reproduction.
