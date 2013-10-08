Structure
=======================================

mip.pl
---------------------------------------
Central hub and likely the only script most users will ever interact directly with.

.. code-block:: console
  
  echo "Running MIP on Uppmax, analyzing all samples in family 10"
  $ perl mip.pl -env_up 1 -f 10

Sequence QC
-----------
Raw sequence quality control: `FastQC`_

Alignment
---------
Currently MIP supports these aligners:

#. `Mosaik`_ (WES, WGS)
#. `BWA`_ (WES, WGS, Rapid WGS)

BAM file manipulation
---------------------

- Sorting and indexing: `SAMTools`_ (sort & index)
- Duplicate marking: `PicardTools`_ (MarkDuplicates)
- Realignment and base recalibration: `GATK`_ (Realigner & BaseRecalibration)

Coverage QC
-----------

- Coverage Report and QC metrics: `Chanjo`_
- QC metrics: `PicardTools`_ (MultipleMetrics & HSmetrics)

Variant calling
---------------

- Variant discovery and recalibration: `GATK`_ (HaploTypeCaller & VariantRecalibration)

Variant QC
----------

- All variants: `GATK`_ (VariantEval)
- Exonic variants: `GATK`_ (VariantEval)

Variant annotation
------------------
Collect transcript and amino acid information as well as information from external databases: `ANNOVAR`_

intersectCollect.pl
---------------------------------------
Intersects and collects information from external databases and merges all to one annotated variant file. (see :doc:`intersectCollect`). 


rank_list_filter.pl
---------------------------------------
Scores and ranks each variant using weighted sums according to disease causing potential. 
  
collect_info.pl
---------------------------------------
Collects QC data from the MPS analysis. Outputs in tab-sep format. 

add_depth.pl
---------------------------------------
Adds the read depth (DP=X) at chromosomal postions for individual lacking a genotype call where at least one 
individual in the analysis has a genotype call. 

covplots_exome.R / covplots_genome.R
---------------------------------------
Plots coverage across chromosomes.

.. _FastQC: http://www.bioinformatics.babraham.ac.uk/projects/fastqc/
.. _Mosaik: https://github.com/wanpinglee/MOSAIK
.. _BWA: http://bio-bwa.sourceforge.net/
.. _SAMtools: http://samtools.sourceforge.net/
.. _PicardTools: http://picard.sourceforge.net/
.. _Chanjo: https://chanjo.readthedocs.org/en/latest/
.. _GATK: http://www.broadinstitute.org/gatk/
.. _ANNOVAR: http://www.openbioinformatics.org/annovar/