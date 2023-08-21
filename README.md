# GSEA_analysis
GSEA_analaysis

# Gene_expression_matrix
  RNA-seq data. GSEA does not normalize RNA-seq data. RNA-seq data must be normalized for between-sample comparisons using an external normalization procedure (e.g. those in DESeq2 or Voom).
nfcore/diffabundance output two tables 
nomralized_counts.tsv
VST.tsv 

I am using normalized_count.tsv in first attempt 


### .cls phenotype file 
6-total sample, 2-condition,1 - default 
cnt-0
z8ko-1
1 1 1 0 0 0 - order of samples in normalized matrix 
#######################################
6 2 1
# cnt z8ko
1 1 1 0 0 0
