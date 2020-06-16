# ChloroplastofDaturastramonium

This repository contains the pipeline and supplementary data of the manuscript The complete chloroplast genomes of two Mexican plants of the annual herb Datura stramonium (Solanaceae)

## Programs

1. Trimommatic
2. Fastqc
3. NOVOPlasty

## Firts step is the quality filtering using Trimmomatic for raw Illumina paired-end sequences

    java -jar trimmomatic-0.33.jar PE -phred30 Tic23_S155_L006_R1_001.fastq Tic23_S155_L006_R2_001.fastq output_Tic23_S155_L006_R1_001_paired.fastq output_Tic23_S155_L006_R1_001_unpaired.fastq output_Tic23_S155_L006_R2_001_paired.fastq output_Tic23_S156_L006_R2_001_unpaired.fastq SLIDINGWINDOW:4:15 MINLEN:36

## Fastqc program was used to visualize the quality of the sequences

    fastqc output_Tic23_S155_L006_R1_001_paired.fastq output_Tic23_S155_L006_R2_001_paired.fastq

## Running NOVOPlasty for chlroplast assembly

    perl NOVOPlasty3.2.pl -c config.txt

