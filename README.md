Krithika Ravindran Naidu, MS Bioinformatics, Georgia Institute of Technology.

# ahcg_pipeline
Variant calling pipeline for genomic data analysis

## Requirements

1. [Python3 - version 3.4.1](https://www.python.org/download/releases/3.4.1/)
2. [Trimmomatic - version 0.36](http://www.usadellab.org/cms/uploads/supplementary/Trimmomatic/Trimmomatic-0.36.zip)
3. [Bowtie2 - version 2.2.9](https://sourceforge.net/projects/bowtie-bio/files/bowtie2/2.2.9/)
4. [Picard tools - version 2.12.1](https://github.com/broadinstitute/picard/releases/tag/2.12.1/picard.jar)
5. [GATK - version 3.8.0](https://software.broadinstitute.org/gatk/download/)

## Reference genome

Reference genomes can be downloaded from [Illumina iGenomes](http://support.illumina.com/sequencing/sequencing_software/igenome.html)

## Data

1. [Development and validation of a clinical cancer genomic profiling test based on massively parallel DNA sequencing.- Frampton et al](https://www.ncbi.nlm.nih.gov/pubmed/24142049)
2. SRR948994_1.fastq  SRR948994_2.fastq [SRA SRP028580](https://www.ncbi.nlm.nih.gov/sra/SRX332536[accn])

## Virtual Machine Installation

* [Instructions](ahcg2017_starterpipeline/lib/VM_setup.pdf)

## Running the pipeline

#/data2/AHCG2017FALL/bin/samtools-1.5/samtools faidx genome.fa
```
python ahcg_pipeline_v1.0.1Cai.py \
-t /data2/AHCG2017FALL/bin/Trimmomatic-0.36/trimmomatic-0.36.jar \
-b /data2/AHCG2017FALL/bin/bowtie2-2.2.9/bowtie2 \
-p /data2/AHCG2017FALL/bin/picard/picard.jar \
-g /data2/AHCG2017FALL/bin/GenomeAnalysisTK-3.8-0-ge9d806836/GenomeAnalysisTK.jar \
-i /data2/AHCG2017FALL/data/SRR948994_1.fastq /data2/AHCG2017FALL/data/SRR948994_2.fastq \
-w /data2/AHCG2017FALL/reference_genome/Bowtie2Index/genome \
-r /data2/AHCG2017FALL/reference_genome/genome.fa \
-a /data2/AHCG2017FALL/bin/Trimmomatic-0.36/adapters/NexteraPE-PE.fa \
-o /data2/AHCG2017FALL/output \
-d /data2/AHCG2017FALL/reference_genome/GATKResourceBundle/dbsnp_146.hg38.vcf.gz
```
