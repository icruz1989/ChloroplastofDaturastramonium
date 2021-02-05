# ChloroplastofDaturastramonium

This repository contains the pipeline and supplementary data of the manuscript The complete chloroplast genomes of two Mexican plants of the annual herb Datura stramonium (Solanaceae)


Paper
https://www.tandfonline.com/doi/full/10.1080/23802359.2020.1789516

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

An example of a Configuration file is provided in the tutorial of NOVOPlasty https://github.com/ndierckx/NOVOPlasty 
This program has the option to set a Max memory in order to subsample the nuber of sequences from the whole genome sequencing project

## Output files

Log output:

1. log_project.txt
This is a basic log file with the information that shows up on your terminal.

2. log_extented_project.txt
This file will only be generated when the "Extended log" option in the config file is set to "1".
It is a elaborate log file that can be send to me for troubleshooting, it won't provide the user additional info.

Assembly output:
1. Contigs_project.txt
This file contains all the assembled contigs.

2a. Circularized_assembly_project.fasta
When NOVOPlasty is able to circularize one contig, without any additional contigs being produced, it will just output this circularized fasta file.

OR

2b1. Merged_contigs_project.txt
When there are multiple contigs, NOVOPlasty will try to combine all contigs in to a complete circular genome, all the different possibilities can be found in this file.

2b2. Option_nr_project.txt
All possible contig combinations will have a seperate fasta file.

3. contigs_tmp_project.txt
If non of the above files are outputted or are empty, you can retrieve some contigs from this file.
