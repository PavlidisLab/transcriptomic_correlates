# transcriptomic_correlates

This is where you'll find the code (and some of the output data) from our manuscript ["Transcriptomic correlates of electrophysiological and morphological diversity within and across excitatory and inhibitory neuron classes"][manuscript]

[manuscript]: https://journals.plos.org/ploscompbiol/article/related?id=10.1371/journal.pcbi.1007113

## Plotting Tools 
 
This notebook contains code for making some basic plots of our processed data. **If you've never done any coding before, please don't be scared! We made this for you!** You can get started by just plugging your favorite gene into the pre-written examples. The easiest way to run the notebook is [using Binder][binder]. It will run in your web browser without you having to install anything.

[binder]: https://mybinder.org/v2/gh/PavlidisLab/transcriptomic_correlates/master?filepath=Plotting%20Tools.ipynb

The notebook has 4 main sections: 

- Make scatter plots of a single gene versus all ephys and morphology properties, color coded by cell class and with a linear fit to each class and to all cells. 
- Select data based on gene, property, or slope/significance in one or more models. You can ask questions like "What properties is my favorite gene significantly correlated with in a certain model?" or "What are gene/property relationships that are only identified by the class-conditional model?"
- Make scatter plots of one or more gene-property pairs. These are the same plots as in the first section, but we show a few different examples of how you can either specify exactly which genes and properties to plot, or or pick gene-property pairs by filtering as in the section above.  
- Run the full set of models for a given gene/property pair. We've saved some of the most relevant bits of the models (slopes, p-values, AIC, etc.) in Online Tables 1 and 2, but if you need more details this is how you can get them.

## Analysis Code 
 
Code used to generate the data and figures in the manuscript. There are two analysis notebooks, one each for ephys and morphology, and one for generating figures and tables. All 3 notebooks use Python 2.7. The ephys and morphology analyses take a couple hours to run on my laptop; if this is a concern you can run just a subset of genes and/or properties.

The code used for the Patch-seq analysis (written in R) will be added later.

## Data  

This folder contains online tables 1-4, which are required for the plotting tools notebook.

**Online Table 1**: All 51,091 gene/property pairs (9,780 unique genes) with a significant result (FDR < 0.1) in the class-conditional and/or interaction models.

**Online Table 2**: All gene/property pairs regardless of significance (286,032 pairs and 12,225 unique genes).

**Online Table 3**: Mean values of ephys properties and gene expression values (rows) for each cell type (columns) in the combined dataset. Ephys measures include both un-transformed values (for all properties) as well as log10-transformed for a subset (see manuscript). Contains 48 cell types.

**Online Table 4**: Same as 3, but for morphology properties. Contains 43 cell types.

### Description of columns in Online Tables 1 and 2

- property: Ephys or morphology property  
- gene\_entrez\_id: Entrez Gene ID  
- gene_symbol : Gene symbol  
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
- beta\_gene\_inh_only: beta from a version of the class-independent model in which we included only inhibitory cell types. We tested this as an alternative method to the class-conditional model for avoiding class-driven effects. We didn't end up including this in the paper, but our overall impression was that that we get somewhat similar results using both approaches. We suspect that this is largely a result of the much larger number of inhibitory compared to excitatory cell types in the AIBS dataset.  
- pval\_gene\_inh_only: uncorrected p-value for the inhibitory type-only model  
- inh\_only\_aic: AIC, property ~gene with inhibitory cell types only  
- FDR\_gene\_inh_only: FDR-corrected p-value, inhibitory cell types only  
- n\_significant\_0.1\_g|c: Total number of properties for which this gene shows FDR < 0.1 in the class-conditional model  (Online Table 1 only)  
- n\_significant\_0.1\_int: Total number of properties for which this gene shows FDR < 0.1 in the interaction model (Online Table 1 only)  
