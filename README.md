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
# e13z8ko nontag
0 0 0 1 1 1


This content follows the structure of a .cls file as described in the previous responses. Here's how this content can be interpreted based on the .cls file format:

The first line 6 2 1 indicates:

6: The total number of samples in your dataset.
2: The number of different classes or phenotypes you are comparing.
1: A constant value indicating that this is a single dataset analysis.
The second line # cnt z8ko seems to be a comment providing some context or information about the file.

The third line 0 0 0 1 1 1 specifies the class labels for each of the 6 samples. In this case, it appears that you have two classes. The class labels are as follows:

Sample 1, 2, and 3 belong to Class 0 (labeled as "0").
Sample 4, 5, and 6 belong to Class 1 (labeled as "1").

########################################################################################################################

always look at the index file 
