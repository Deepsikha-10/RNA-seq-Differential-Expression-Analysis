# Commands
# STEP 1: Download of Data
•	fastq-dump --split-files --gzip DRR514092

# STEP 2a: Quality Control
•	/home/Desktop/SDA1/RNA/tools/FastQC/fastqc /home/Desktop/SDA1/RNA/raw_reads/DRR514092_1.fastq.gz -o /home/Desktop/SDA1/RNA/fastqc/before

•	java -jar /home/rgitbt/Desktop/SDA1/RNA/tools/Trimmomatic-0.39/trimmomatic-0.39.jar PE /home/rgitbt/Desktop/SDA1/RNA/raw_reads/DRR514092_1.fastq.gz /home/rgitbt/Desktop/SDA1/RNA/raw_reads/DRR514092_2.fastq.gz DRR514092_1_paired.fastq.gz DRR514092_1_unpaired.fastq.gz DRR514092_2_paired.fastq.gz DRR514092_2_unpaired.fastq.gz ILLUMINACLIP:/home/rgitbt/Desktop/SDA1/RNA/tools/Trimmomatic-0.39/adapters/NexteraPE-PE.fa: 2:30:10 LEADING:3 TRAILING:3 SLIDINGWINDOW: 4:15 MINLEN:50

•	/home/rgitbt/Desktop/SDA1/RNA/tools/FastQC/fastqc /home/rgitbt/Desktop/SDA1/RNA/trim/DRR514092_1_paired.fastq.gz -o /home/rgitbt/Desktop/SDA1/RNA/fastqc/after/

# Step 3a: Preparation of reference genome using RSEM
/home/rgitbt/Desktop/SDA/RNA_seq/tools/RSEM-1.3.1/rsem-prepare-reference --gtf /home/rgitbt/Desktop/SDA/RNA_seq/whole_genome/Drosophila_melanogaster.BDGP6.54.114.gtf --star --star-path /home/rgitbt/Desktop/SDA1/RNA/tools/STAR-STAR_2.7.10b_alpha_23-06-09/source/ Drosophila_melanogaster.BDGP6.54.dna.toplevel.fa Reference_genome

# Step 3b: Alignment along with expression quantification
/home/rgitbt/Desktop/SDA/RNA_seq/tools/RSEM-1.3.1/rsem-calculate-expression --star --star-path /home/rgitbt/Desktop/SDA/RNA_seq/tools/STAR-STAR_2.7.10b_alpha_23-06-09/source/ --star-gzipped-read-file --paired-end /home/rgitbt/Desktop/SDA/RNA_seq/trim/DRR514092_1_paried.fastq.gz /home/rgitbt/Desktop/SDA/RNA_seq/trim/DRR514092_2_paried.fastq.gz Reference_genome DRR51409

# Step 4: Differential Gene Expression
•	/home/rgitbt/Desktop/SDA/RNA/tools/trinityrnaseq-2.13.0/util/abundance_estimates_to_matrix.pl --est_method RSEM --gene_trans_map none /home/rgitbt/Desktop/SDA1/RNA/gene_result/DRR514*.genes.results

•	cat > samples_file
control DRR514092
control DRR514093
control DRR514094
treatment DRR514098
treatment DRR514099
treatment DRR514100

•	/home/rgitbt/Desktop/SDA/RNA/tools/trinityrnaseq-2.13.0/Analysis/DifferentialExpression/run_DE_analysis.pl --matrix /home/rgitbt/Desktop/SDA1/RNA/trinity/RSEM.isoform.counts.matrix --method DESeq2 --samples_file samples_file


