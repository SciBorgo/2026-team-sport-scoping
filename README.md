# 2026-team-sport-scoping

Data and R code for the scoping review:

> Sankey C, Sheehan W, Caperchione CM, Wood LM, Menaspà P, Borg DN. **The measurement of sport-specific skill and collective behaviour in team invasion sport: A scoping review.** *Sports Medicine* (under review).

Protocol registered on the Open Science Framework: <https://osf.io/2wu46/files/5cdfq>

## Contents

| File | Description |
|---|---|
| `Team_sport_review_extraction_final.xlsx` | Final, reconciled data extraction (Supplemental File 2). The `Data Extraction` sheet has one row per included study. The `Multiple SSKs` sheet lists the individual skills within multi-skill test batteries (Supplemental File 4). |
| `upset_figures.R` | Generates Figures 2–7 from the final extraction. Figs 2 and 4 are bar charts; Figs 3, 5, 6 and 7 are UpSet plots. |
| `data_validation_reviewer_1.csv`<br>`data_validation_reviewer_2.csv` | Independent extractions by two reviewers, used to assess extraction agreement. |
| `Team_sport_agreement.qmd` | Quarto report that calculates raw agreement and Gwet's AC1 (95% CI) for each extraction field. |
| `Team_sport_agreement.pdf` | Rendered agreement report. |

Figure 1 (PRISMA flow diagram) was not produced in R, so no code for it is included here.

## Reproducing the analysis

Clone the repository and run everything from the repository root.

**Figures 2–7**

```r
source("upset_figures.R")
```

Figures are saved to `figures/` as 600 dpi PNGs and as vector PDFs. To also write Figure 7 in alternative colour palettes, set `make_palette_previews <- TRUE` near the end of the script.

**Extraction agreement**

```bash
quarto render Team_sport_agreement.qmd
```

This renders the PDF report. It also writes `agreement_summary.csv`, `agreement_disagreements.csv` and `agreement_paragraph.docx`, which holds the results text used in the manuscript.

## Requirements

- R 4.4.1
- Quarto (with a LaTeX installation for PDF output)
- R packages: `readxl`, `dplyr`, `tidyr`, `stringr`, `ggplot2`, `patchwork`, `viridisLite`, `knitr`, `kableExtra`, `officer`

```r
install.packages(c("readxl", "dplyr", "tidyr", "stringr", "ggplot2",
                   "patchwork", "viridisLite", "knitr", "kableExtra", "officer"))
```

## Notes

- For free-text fields (aim, procedure, outcome measure, and similar), agreement is based on exact string matching, so it understates true agreement. These fields were checked manually.
- Missing data were not imputed.

## Funding

This work was supported by an Australian Sports Commission Collaborative Research Grant (#22130).

## Contact

- Caitlin Sankey (corresponding author): caitlin.sankey@uts.edu.au
- David Borg (code and analysis)
