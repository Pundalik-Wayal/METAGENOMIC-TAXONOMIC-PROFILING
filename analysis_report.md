# Metagenomics Taxonomic Profiling — Analysis Report
Generated: 2026-05-12 16:22:08.29653

## Dataset
- **Study**: Cuatro Ciénegas oasis, Mexican desert (Okie et al. 2020)
- **Samples**: JC1A (control mesocosm) | JP4D (fertilized pond)
- **Read type**: Paired-end shotgun metagenomics (pre-trimmed with cutadapt)

## Pipeline Overview
| Step | Tool (R equivalent) | Purpose |
|------|--------------------|---------| 
| 1 | Data loading | Import Kraken2 reports, MetaPhlAn profiles, metadata |
| 2 | QC Summary | Classification rates, read counts |
| 3 | Kraken2 analysis | Domain/Phylum/Class/Species taxonomy extraction |
| 4 | Bracken re-estimation | Redistribute reads to species level |
| 5 | Visualizations | Stacked bars, Sankey, Krona sunburst, heatmaps |
| 6 | MetaPhlAn profiles | Marker gene-based profiling |
| 7 | Alpha diversity | Shannon, Simpson, Richness, Evenness (vegan) |
| 8 | Beta diversity | Bray-Curtis dissimilarity (vegan) |
| 9 | Rarefaction | Species richness vs depth curves |
| 10 | Differential abundance | DESeq2 — JP4D vs JC1A |
| 11 | Phyloseq | Unified microbiome data object |

## Key Findings (Tutorial-Expected Results)

### Classification Rates (Kraken2)
- **JC1A**: ~23% classified reads (77% unclassified)
- **JP4D**: ~10% classified reads (90% unclassified)

### Domain Composition
- **JC1A**: ~13% Bacteria, ~9% Eukaryota (mostly human contamination), ~0.03% Viruses
- **JP4D**: ~9% Bacteria, ~0.7% Eukaryota

### Class-level Diversity
- **JC1A**: High diversity — Alphaproteobacteria, Betaproteobacteria, Gammaproteobacteria, Flavobacteria
- **JP4D**: Dominated by Alphaproteobacteria (survival advantage under nutrient enrichment)

### MetaPhlAn (Marker Gene)
- **JC1A**: 0 classified taxa (too few reads to cover marker genes)
- **JP4D**: Bacteroidetes (94%) + Proteobacteria/Alphaproteobacteria (6%)

### Biological Interpretation
Alphaproteobacteria dominates the fertilized pond (JP4D), consistent with
Okie et al. (2020): specific genomic traits enable Alphaproteobacteria to
cope better with high nutrient availability — a trait-mediated ecological
response rather than microevolution (32-day experiment).

## Output Files
| File | Description |
|------|-------------|
| 01_classification_overview.{pdf,png} | Domain-level stacked bar chart |
| 02_phylum_composition.{pdf,png} | Phylum composition |
| 03_class_comparison.{pdf,png} | Class diversity comparison |
| 04_sankey_taxonomy.{pdf,png} | Sankey/alluvial taxonomy flow |
| 05a_krona_JC1A.html | Interactive Krona sunburst — JC1A |
| 05b_krona_JP4D.html | Interactive Krona sunburst — JP4D |
| 06_bracken_species.{pdf,png} | Bracken-adjusted species abundance |
| 07_metaphlan_species.{pdf,png} | MetaPhlAn species profiles |
| 08_tool_comparison.{pdf,png} | Kraken2 vs MetaPhlAn classification |
| 09_alpha_diversity.{pdf,png} | Alpha diversity metrics |
| 10_beta_diversity_heatmap.pdf | Bray-Curtis dissimilarity heatmap |
| 11_rarefaction_curves.{pdf,png} | Rarefaction curves |
| 12_differential_abundance.{pdf,png} | DESeq2 volcano plot |
| deseq2_results.csv | Full DESeq2 results table |
| phyloseq_object.rds | R phyloseq object for downstream analysis |

## References
1. Wood & Salzberg (2014) — Kraken. Genome Biology.
2. Wood et al. (2019) — Kraken2. Genome Biology.
3. Lu et al. (2017) — Bracken. PeerJ Comp Sci.
4. Truong et al. (2015) — MetaPhlAn2. Nature Methods.
5. Blanco-Miguez et al. (2023) — MetaPhlAn4. Nature Biotechnology.
6. Ondov et al. (2011) — Krona. BMC Bioinformatics.
7. Breitwieser & Salzberg (2020) — Pavian. Bioinformatics.
8. Okie et al. (2020) — Cuatro Ciénegas dataset. eLife.
9. McMurdie & Holmes (2013) — phyloseq. PLoS ONE.
10. Oksanen et al. — vegan. R package.
11. Love et al. (2014) — DESeq2. Genome Biology.
