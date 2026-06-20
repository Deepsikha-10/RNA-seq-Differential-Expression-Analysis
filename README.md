# RNA-seq-Differential-Expression-Analysis
RNA sequencing (RNA-Seq) is a cutting-edge next-generation sequencing (NGS) technique used in transcriptomics to analyze the complete set of RNA transcripts present in a cell or tissue at a specific time and condition. 
RNA-Seq and transcriptomics are widely applied in gene expression profiling, alternative splicing and isoform discovery, and biomarker identification for disease diagnosis and prognosis. They support pathway analysis, drug discovery, and toxicogenomics by revealing molecular responses to treatments.Advanced uses include single-cell transcriptomics for studying cellular heterogeneity and agricultural research to investigate stress responses and host–pathogen interactions.
In summary, RNA-Seq is a powerful tool in transcriptomics that transforms raw RNA data into detailed insights about gene expression, contributing to diverse applications including biological research, medical diagnostics, and drug development.

# Workflow 
Download (FASTQ)
 ⬇
 Quality Check & Control
 → Quality Check (FastQC)
 → Quality Control (Trimmomatic)
 Output: Filtered FASTQ
 ⬇
 Reference Genome Preparation using RSEM
 Tools: RSEM, STAR 
Output:.tab, .ti, .idx.fa, .seq, .transcripts.fa  
 ⬇
Alignment and Expression Quantification
Output:.isoforms.results, .genes.results, .transcript.bam
 ⬇
Differential Gene Expression
Tools: Trinity RNA-seq utility scripts, DESeq2 (statistical tool for DGE)
Ouput: Expression count matrices, MA plot, Volcano Plot 


