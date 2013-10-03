Setup
=======

Moving files from INBOX
-------------------------
FASTQ-files should be moved from `/INBOX` to a backed up directory.

1. Check the pedigree file and move to a backed up directory ("exomes")
2. Move and rename gzipped FASTQ-files into ``{SEQ TYPE}/{IDN}/fastq``, where IDN is your sample ID.

Filename convention
~~~~~~~~~~~~~~~~~~~~~
The permanent filename should follow the following format::

  {LANE}_{DATE}_{FLOW CELL}_{IDN}_index{BARCODE SEQ}_{DIRECTION 1/2}.fastq.qz

Dependencies
~~~~~~~~~~~~~~
Make sure you have loaded/installed all dependencies and that they are in your PATH. You only need to load the dependencies that are required for the modules that you want to run. If you fail to install dependencies for a module MIP will tell you what dependencies you need to install and exit.

On UPPMAX::

  module load java/sun_jdk1.7.0_25 FastQC mosaik-aligner bwa BEDTools plink vcftools annovar

You do best installing both GATK and PicardTools yourself. Make sure to load the correct Java environment to run these tools.

.. note::
  N.B. `plink` needs to be loaded *before* `PicardTools`.

The current version of FASTQC is only tested under Java 1.6. Therefore we can't use the latest version of GATK which requires Java 1.7!

I installed
~~~~~~~~~~~~~
bedtools#2.17.0
bwa#0.7.5a
fastqc#0.10.1
gatk#2.5.2 (Java 1.6)
mosaik#2.1.73
plink#1.07-x86_64
qaTools#master
samtools#0.1.18
vcftools#0.1.11
picard#1.98