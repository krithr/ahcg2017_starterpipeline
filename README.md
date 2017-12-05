Variant calling pipeline for genomic data analysis.
> Krithika Ravindran Naidu, MS Bioinformatics, Georgia Institute of Technology.

# About
* This pipeline is a variant calling pipeline. 
* The expected output is a VCF file containing potential variants (/data2/AHCG2017FALL/output). 
* The test dataset is located here: https://www.ncbi.nlm.nih.gov/sra/SRX332536%5Baccn%5D.
* Looking for specific liquid biopsy scientific papers and finding the best practice methods to optimize the variant calling pipeline.

## Mission Statement

The primary aim of the pipeline is to detect cancer early by identifying the rare variants from the liquid biopsy samples and eventually combine the wet-lab and bioinformatic characteristics of the project.

## Requirements

1. [Python3 - version 3.4.1](https://www.python.org/download/releases/3.4.1/)
2. [Trimmomatic - version 0.36](http://www.usadellab.org/cms/uploads/supplementary/Trimmomatic/Trimmomatic-0.36.zip)
3. [Bowtie2 - version 2.2.9](https://sourceforge.net/projects/bowtie-bio/files/bowtie2/2.2.9/)
4. [Picard tools - version 2.12.1](https://github.com/broadinstitute/picard/releases/tag/2.12.1/picard.jar)
5. [GATK - version 3.8.0](https://software.broadinstitute.org/gatk/download/)
6. [Control-FREEC](http://boevalab.com/FREEC/tutorial.html)

## Reference genome

Reference genomes can be downloaded from [Illumina iGenomes](http://support.illumina.com/sequencing/sequencing_software/igenome.html)

* Command
```
wget ftp://igenome:G3nom3s4u@ussd-ftp.illumina.com/Homo_sapiens/NCBI/GRCh38/Homo_sapiens_NCBI_GRCh38.tar.gz
```

## Data

1. [Development and validation of a clinical cancer genomic profiling test based on massively parallel DNA sequencing.- Frampton et al](https://www.ncbi.nlm.nih.gov/pubmed/24142049)
2. SRR948994_1.fastq  SRR948994_2.fastq, [SRA SRP028580](https://www.ncbi.nlm.nih.gov/sra/SRX332536[accn])

* Downloading the sample from SRA database :

```
fastq-dump --split-files SRR948994
```
## Virtual Machine Installation

* [Instructions](https://github.com/krithr/ahcg2017_starterpipeline/blob/master/VM%20Installation)

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

## Directory structure
```
mkdir -p data/reads data/reference data/adapters output
```

## Updates : Merging the wet lab technique with the bioinformatic pipeline

From the ahcg_pipeline_v1.0.4.py pipeline, a few changes were made and the version was updated to v1.0.5. The data samples used are found in /data2/AHCG2017FALL/data3 as MenCo002DNA and MenPa004DNA. The DNA samples were collected from the nano-vescicles of the patients' blood. An Illumina HiSeq2500 was performed for tumor profiling. It is done through exome sequencing and 150-200X coverage is obtained. The pipeline captures bed files to coverage out. The version of pipeline that is used in the virtual box right now is v1.0.5. This can be verified using a test data. 

## Final version of the script

```
ahcg_pipeline.py 1.0.8
```
Location
```
/data2/AHCG2017/bin/pipeline/ahcg_pipeline.py
```
Command
```
./ahcg_pipeline.v1.0.7.py -c config_file.txt
```
