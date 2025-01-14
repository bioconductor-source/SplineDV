# Spline-DV
A spline-based scRNA-seq method for identifying differentially variable (DV) genes across two experimental conditions.

# Why to use Spline-DV?
One of the most intuitive ways to evaluate a gene expression change is using Differential Expression (DE) analysis. Traditionally, DE analysis focuses on identifying genes that are up- or down-regulated (increased or decreased expression) between conditions, typically employing a basic mean-difference approach. We propose a paradigm shift that acknowledges the central role of gene expression variability in cellular function and challenges the current dominance of mean-based DE analysis in single-cell studies. We suggest that scRNA-seq data analysis should embrace the role of inherent gene expression variability in defining cellular function and move beyond mean-based approaches. 

# Installation 
```R
if (!require("devtools")) install.packages("devtools")
devtools::install_github("Xenon8778/SplineDV")
```
# Tutorial - Spline-DV
## Loading scRNAseq count example data
The example data is borrowed from an experimental *Nkx2-1* Gene knockout scRNA-seq study by Liebler *et al.* [1]
```R
# Load Data
library(SplineDV)
WT_count <- get(data("WT_count", package = 'SplineDV')) # WT Sample
KO_count <- get(data("KO_count", package = 'SplineDV')) # KO Sample
```
## Running Spline-DV
For the analysis, the test data (X) is always use in contrast with the control data (Y).
```R
DV_res <- DV_splinefit(X = KO_count, Y = WT_count, ncells = 3, ncounts = 200)
head(DV_res)
```

# Tutorial - Spline-HVG

```R
## Loading Data
WT_count <- get(data("WT_count", package = 'SplineDV')) # WT Sample

## Running Spline-HVG
HVG_res <- HVG_splinefit(WT_count, nHVGs = 100, ncells = 3, ncounts = 200)
head(HVG_res)
```

# References
1. Liebler JM, Marconett CN, Juul N, et al. Combinations of differentiation markers distinguish subpopulations of alveolar epithelial cells in adult lung. Am J Physiol Lung Cell Mol Physiol. 2016;310(2):L114-L120. doi:10.1152/ajplung.00337.2015
