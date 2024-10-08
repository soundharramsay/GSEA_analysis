-# GSEA_analysis
GSEA_analaysis

# Gene_expression_matrix
  RNA-seq data. 
  GSEA does not normalize RNA-seq data.
  RNA-seq data must be normalized for between-sample comparisons using an external normalization procedure (e.g. those in DESeq2 or Voom).


## nfcore/diffabundance output two tables 
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
soundhar@MAC308219 GSEA_4.3.2 % bash gsea-cli.sh GSEA -res ./IN_GSEA_inputs/IN_cont_vs_treated.normalised_count_nfcore_diffabundance.txt -cls ./IN_GSEA_inputs/iN.cls -gmx ./msigdb_v2023.1.Hs_GMTs/c2.cp.reactome.v2023.1.Hs.symbols.gmt -collapse false -rpt_label run6_c2.cp.reactome.v2023.1.Hs

########################################################################################################################
########################################################################################################################
########################################################################################################################
########################################################################################################################
########################################################################################################################

########################################################################################################################
########################################################################################################################
########################################################################################################################
########################################################################################################################  second option

GSEA 

Input – DESEQ normalized  text format (works only with text format)
## use excel 
###  split and keep on gene name ENSG00000244171.4|PBX2P1
### save in .tab delimited txt format 

.cls file 

6 2 1
# e13z8ko nontag           
0 0 0 1 1 1                           --- follow identical order of expression data colnames

Explanation
https://software.broadinstitute.org/cancer/software/gsea/wiki/index.php/Data_formats#CLS:_Categorical_.28e.g_tumor_vs_normal.29_class_file_format_.28.2A.cls.29

 
(base) soundhar@MAC308219 4.GSEA % /Users/soundhar/Desktop/GSEA_4.3.2/gsea-cli.sh \
    GSEA \
    -gmx /Users/soundhar/Desktop/GSEA_4.3.2/msigdb_v2023.1.Hs_GMTs/c2.cp.biocarta.v2023.1.Hs.symbols.gmt \
    -cls ./k562.e10.cls \
    -res ./e10.all.normalised_counts.txt \  ## only txt format 
    -rpt_label e10.c2.cp.biocarta.v20 \
    -collapse false \
  -metric Diff_of_Classes ---default requires 3 reps per condition






![image](https://github.com/soundharramsay/GSEA_analysis/assets/32353704/701722fa-d59c-41d8-a571-ab67a079cd69)




BASH script 
#!/bin/bash

# Base path for GMT files
base_path="/Users/soundhar/Desktop/GSEA_4.3.2/msigdb_v2023.1.Hs_GMTs"

# List of GMT files
gmt_files=(
    "c2.cp.kegg.v2023.1.Hs.symbols.gmt"
    "h.all.v2023.1.Hs.symbols.gmt"
    "c3.mir.mir_legacy.v2023.1.Hs.symbols.gmt"
    "c3.mir.v2023.1.Hs.symbols.gmt"
    "c3.tft.gtrd.v2023.1.Hs.symbols.gmt"
    "c5.go.bp.v2023.1.Hs.symbols.gmt"
    "c5.go.cc.v2023.1.Hs.symbols.gmt"
    "c5.go.mf.v2023.1.Hs.symbols.gmt"
    # Add more GMT file paths as needed
)

# Loop through each GMT file
for gmt in "${gmt_files[@]}"
do
    # Construct the full GMT file path
    gmt_path="${base_path}/${gmt}"

    # Extract the GMT file name without the path and extension for labeling
    gmt_name=$(basename "$gmt" .gmt)

    # Construct the report label using the GMT file name
    rpt_label="e10_vs_nt_${gmt_name}"

    # Run the GSEA command
    /Users/soundhar/Desktop/GSEA_4.3.2/gsea-cli.sh GSEA \
        -gmx "$gmt_path" \
        -res e10_vs_nt_all_normalised_counts.txt \
        -rpt_label "$rpt_label" \
        -metric Diff_of_Classes \
        -cls ./nt_Vs_e10.cls
done

####### result 

look for idex.html file 


############################################################################################# gene-set option

#!/bin/bash

# Base path for GMT files
base_path="/Users/soundhar/Desktop/GSEA_4.3.2/msigdb_v2023.1.Hs_GMTs"

# List of GMT files
gmt_files=(
    "c2.cp.kegg.v2023.1.Hs.symbols.gmt"
    "h.all.v2023.1.Hs.symbols.gmt"
    "c3.mir.mir_legacy.v2023.1.Hs.symbols.gmt"
    "c3.mir.v2023.1.Hs.symbols.gmt"
    "c3.tft.gtrd.v2023.1.Hs.symbols.gmt"
    "c5.go.bp.v2023.1.Hs.symbols.gmt"
    "c5.go.cc.v2023.1.Hs.symbols.gmt"
    "c5.go.mf.v2023.1.Hs.symbols.gmt"
    # Add more GMT file paths as needed
)

# Loop through each GMT file
for gmt in "${gmt_files[@]}"
do
    # Construct the full GMT file path
    gmt_path="${base_path}/${gmt}"

    # Extract the GMT file name without the path and extension for labeling
    gmt_name=$(basename "$gmt" .gmt)

    # Construct the report label using the GMT file name
    rpt_label="e13_vs_nt_${gmt_name}"

    # Run the GSEA command
    /Users/soundhar/Desktop/GSEA_4.3.2/gsea-cli.sh GSEA \
        -res e13_vs_nt_all.normalised_counts.txt \
        -cls nt_Vs_e13.cls \
        -gmx "$gmt_path" \
        -rpt_label "$rpt_label" \
        -metric Signal2Noise \
        -permute gene_set \
        -nperm 1000
done
