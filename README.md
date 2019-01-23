# transcriptomic_correlates

This is where you'll find the code (and some of the output data) from our manuscript ["Transcriptomic correlates of electrophysiological and morphological diversity within and across neuron types"][manuscript]

[manuscript]: https://www.biorxiv.org/content/early/2019/01/18/524561

## Plotting Tools 
 
This notebook contains code for making some basic plots of our processed data. **If you've never done any coding before, please don't be scared! We made this for you!** You can get started by just plugging your favorite gene into the pre-written examples. The easiest way to run the notebook is [using Binder][binder]. It will run in your web browser without you having to install anything.

[binder]: https://mybinder.org/v2/gh/PavlidisLab/transcriptomic_correlates/master?filepath=Plotting%20Tools.ipynb

The notebook has 3 main sections: 
 
- Select data based on gene, property, or slope/significance in one or more models. You can ask questions like "What properties is my favorite gene significantly correlated with in a certain model?" or "What are gene/property relationships that are only identified by the class-conditional model?"
- Make scatter plots of a gene and an ephys or morphology property, color coded by cell class and with a linear fit to each class and to all cells.
- Run the full set of models for a given gene/property pair. We've saved some of the most relevant bits of the models (slopes, p-values, AIC, etc.) in Table S5, but if you need more details this is how you can get them.

## Analysis Code 
 
Code used to generate the data and figures in the manuscript. There are two analysis notebooks, one each for ephys and morphology, and one for generating figures and tables. All 3 notebooks use Python 2.7. The ephys and morphology analyses take a couple hours to run on my laptop; if this is a concern you can run just a subset of genes and/or properties.

The code used for the Patch-seq analysis (written in R) will be added later.

## Data  

This folder contains supplementary tables S4-S7, which are required for the plotting tool notebook.

**S4**: All 51,091 gene/property pairs (9,780 unique genes) with a significant result (FDR < 0.1) in the class-conditional and/or interaction models.

**S5**: All gene/property pairs regardless of significance (286,032 pairs and 12,225 unique genes).

**S6**: Mean values of ephys properties and gene expression values (rows) for each cell type (columns) in the combined dataset. Ephys measures include both un-transformed values (for all properties) as well as log10-transformed for a subset (see manuscript). Contains 48 cell types.

**S7**: Same as S6, but for morphology properties. Contains 43 cell types.

### Description of columns in Tables S4 and S5  

- property: Ephys or morphology property  
- gene\_entrez\_id: Entrez Gene ID  
- gene_symbol : Official gene symbol  
- beta_gene: beta (slope) from the class-independent model  
- beta_gene|class: beta from the class-conditional model  
- slope_exc: excitatory cell type-specific slope from the interaction model  
- slope_inh: inhibitory cell type-specific slope from the interaction model  
- pval_gene: uncorrected p-value from the class-independent model       
- pval\_gene|class\_anova: uncorrected p-value from the class-conditional model  
- pval\_int\_anova: uncorrected p-value from the class-independent model    
- model1_aic: AIC (Akaike information criterion) goodness-of-fit measure, property ~ gene     
- model2_aic: AIC, property ~ cell class  
- model3_aic: AIC, property ~ gene + cell class  
- model4_aic: AIC, property ~ gene + cell class + gene * cell class interaction  
- FDR\_gene: FDR-corrected p-value, class-independent (corresponds to pval_gene)  
- FDR\_gene|class\_anova: FDR-corrected p-value, class-conditional
- FDR\_int\_anova: FDR-corrected p-value, class-independent  
- n\_significant\_0.1\_g|c: Total number of properties for which this gene shows FDR < 0.1 in the class-conditional model  (S4 only)  
- n\_significant\_0.1\_int: Total number of properties for which this gene shows FDR < 0.1 in the interaction model (S4 only) 