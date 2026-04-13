# Sensory Evaluation Analysis

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![R](https://img.shields.io/badge/R-4.0%2B-blue.svg)](https://www.r-project.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Publication-style technical sensory evaluation analysis for carbonated lemon beverages (Best Beverages PLC).

## Overview

This project performs comprehensive sensory evaluation analysis including:
- Panel performance assessment (discrimination, repeatability)
- Sample discrimination testing (two-way ANOVA with interaction)
- Product sensory profiling (PCA, spider plots)
- Assessor-level diagnostics

**Report Style**: Publication-style technical sensory report

## Data Description

| Parameter | Value |
|-----------|-------|
| Data Source | `data/lemondata.csv` |
| Experimental Design | Randomized Complete Block Design (RCBD) |
| Samples | 6 products |
| Assessors | 9 trained panelists |
| Replicates | 3 per assessor per sample |
| Total Observations | 162 |
| Attributes | 7 (0-15 point scale) |

**Attributes Evaluated**:
- Colour intensity
- Fizziness
- Tingliness
- Sweetness
- Phenolic taint
- Sourness
- Lemon flavour intensity

## Quick Start

```bash
# Clone the repository
git clone https://github.com/yourusername/sensory-evaluation-analysis.git
cd sensory-evaluation-analysis

# Install Python dependencies
pip install -r requirements.txt

# Run analysis (generates tables and figures)
python scripts/run_analysis.py

# Generate DOCX report
python scripts/generate_report.py

# (Optional) Run R analysis
Rscript scripts/sensory_analysis.R
```

## Directory Structure

```
sensory-evaluation-analysis/
├── README.md                 # Project overview
├── LICENSE                   # MIT License
├── requirements.txt          # Python dependencies
├── data/
│   └── lemondata.csv         # Raw sensory data (162 observations)
├── scripts/
│   ├── run_analysis.py       # Main analysis script
│   ├── generate_report.py    # DOCX report generator
│   ├── sensory_analysis.R    # R analysis script
│   └── verify_data.py        # Data verification utility
├── results/
│   ├── tables/               # Statistical output (11 CSV files)
│   └── figures/              # Figures for report
├── report/
│   └── Sensory_Report.docx   # Final report
└── docs/
    └── statistical_notes.md  # Methodological explanations
```

## Key Findings

### Panel Performance
- **Discrimination**: 6/7 attributes discriminate samples (Colour fails, p=0.256)
- **Good Agreement**: Fizziness, Tingliness, Sweetness, Sourness
- **Poor Agreement**: Colour, Phenolic, Lemon (significant interaction)

### Assessor Performance Summary

| Assessor | Discrimination Rate | Notes |
|----------|--------------------:|-------|
| 3, 6, 7, 8, 9 | 100% (7/7) | Excellent |
| 1, 2, 5 | 85.7% (6/7) | Good |
| 4 | 71.4% (5/7) | Moderate |

### Product Profiles
- **Product 4**: Elevated Phenolic taint (3.58 vs ~0.07) - flagged as sensory outlier
- **Product 3**: Highest Fizziness (10.91)
- **Product 5**: Highest Tingliness (13.05)
- **Products 1, 2, 6**: Similar profiles

### PCA Summary
| Component | Variance | Cumulative |
|-----------|---------:|-----------:|
| PC1 | 53.8% | 53.8% |
| PC2 | 30.8% | 84.6% |

## Output Files

### Tables (`results/tables/`)

| File | Description |
|------|-------------|
| `anova_summary.csv` | Two-way ANOVA results |
| `sample_means.csv` | Mean ratings by sample |
| `sample_statistics.csv` | Detailed sample statistics |
| `assessor_discrimination_summary.csv` | Assessor discrimination rates |
| `assessor_discrimination_detail.csv` | Per-attribute F and p values |
| `repeatability_summary.csv` | Within-sample SD summary |
| `repeatability_detail.csv` | Detailed repeatability data |
| `pca_eigenvalues.csv` | PCA variance explained |
| `pca_loadings.csv` | PCA attribute loadings |
| `pca_scores.csv` | PCA sample scores |
| `attribute_correlation.csv` | Attribute correlations |

### Figures (`results/figures/`)

**Report Figures**:
- `figure_1_sensory_profile.png` - Sensory profile spider plot
- `figure_2_pca_biplot.png` - PCA biplot
- `figure_3_interaction_phenolic.png` - Assessor × Sample interaction
- `figure_4_interaction_lemon.png` - Assessor × Sample interaction
- `figure_5_interaction_colour.png` - Assessor × Sample interaction
- `figure_6_repeatability_heatmap.png` - Repeatability heatmap

**Supplementary**:
- `interaction_*.png` - All attribute interaction plots (7 files)
- `assessor_discrimination.png` - Discrimination rates by assessor
- `agreement_summary.png` - Panel agreement summary
- `effect_size_summary.png` - Effect sizes by attribute

## Statistical Methods

See `docs/statistical_notes.md` for detailed explanations of:
- Two-way ANOVA with interaction
- Tukey HSD post-hoc test
- PCA (standardized)
- Repeatability calculation (within-sample SD)
- Effect size interpretation (partial η²)

## Notes on Interpretation

This project is for **panel evaluation + sample profiling**, not consumer testing or manufacturing root cause diagnosis.

- **Sensory outlier** ≠ **defective product**
- **Panel useful for several attributes** ≠ **fully validated panel**
- Findings suggest follow-up investigation, not confirmed cause

## Dependencies

### Python
```
pandas>=1.5.0
numpy>=1.23.0
scipy>=1.9.0
statsmodels>=0.13.0
scikit-learn>=1.1.0
matplotlib>=3.6.0
seaborn>=0.12.0
python-docx>=0.8.11
```

### R (optional)
```r
tidyverse
car
emmeans
factoextra
```

## Course Information

**Course**: 141.312 Food Characterisation  
**Date**: April 2026

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.