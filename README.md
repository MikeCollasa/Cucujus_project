# _Cucujus_ microbiome project
## Description of the pipeline created in the Symbiosis Evolution Research Group and used to generate data used for the analysis of _Cucujus_ V4 16S rRNA amplicon sequencing data.

### [Amplicon processing](https://github.com/MikeCollasa/Cucujus_project/blob/main/Amplicon%20processing):
- Analyses each library (sample) separately,
- Merges R1 and R2 reads, passes only high-quality reads,
- Converts fastq to fasta files,
- Dereplicates and denoises samples,
- Assigns taxonomy affiliation to reads,
- Produces zOTU/OTU tables used by other scripts.

This is the core amplicon analysis workflow. 
This script joins F and R (R1 and R2) reads, passing only high-quality ones (phred score >=30). 
Next, it converts fastq to fasta files and dereplicates and denoise sequences in each library separately to avoid losing biologically relevant signals.
Joins all the libraries into one table and assigns all the sequences to taxonomy.
**This is the first step of analysis of bacterial 16S!** 

### [Decontamination](https://github.com/MikeCollasa/QUACK/blob/main/QUACK.py):
- Uses as an input:
  - 16S zotu table (produced by Amplicon processing),
  - otus.tax (produced by Amplicon processing),
  - list of blanks (various negative controls),
- Decontaminates 16S data based on negative controls,
- Creates:
  - Table with zotus assigned as: symbiont or contaminants,
  - Decontaminated zotu and otu tables,
  - Statistics table.

