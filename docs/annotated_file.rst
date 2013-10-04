.. _annotated_file:

Annotated File
===============================
The Annotated file contains meta-information lines, a header line and then data lines each 
containing information on a position in the genome. 

Meta-information
----------------

Format::

##{COLUMN NAME}={String},{VERSION}={String},{DESCRIPTION}={String},{dDBNAME}={String}

File meta-information is included after the ``##`` string and must be *key=value* pairs.

Header lines
------------

Format::

#{COLUMN NAME}\t{COLUMN NAME}\t...{COLUMN NAME}

Below is a description of the current data line annotation information used at CMMS. 

Short description
~~~~~~~~~~~~~~~~~
.. csv-table::
  :header-rows: 1
  :widths: 1, 4
  :file: mip-output.csv


Clinical List Additional Entries
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+--------------------------------------------------+---------------------------------------------------------------------------+
|   COLUMN_NAME                                    |     Example value                                                         |
+==================================================+===========================================================================+
|Disease_group                                     |Peroxisomal metabolism                                                     |                                          
+--------------------------------------------------+---------------------------------------------------------------------------+
|Clinical_db_genome_build                          |GRCh37.p8                                                                  |
+--------------------------------------------------+---------------------------------------------------------------------------+
|Disease_gene_model                                |AR_hom:AR_Compound:AD:                                                     |
+--------------------------------------------------+---------------------------------------------------------------------------+
                                                                                                                               
Longer description
~~~~~~~~~~~~~~~~~~
.. csv-table::
  :header-rows: 1
  :widths: 1, 1, 2, 4
  :file: mip-output-long.csv


Clinical List Additional Entries
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+-------------------+-----------+----------------------------+----------------------------------------------------------------------------+
|   COLUMN_NAME     |     TYPE  |          VALUE             |     DESCRIPTION                                                            |
+===================+===========+============================+============================================================================+
|Disease group      | String    |Peroxisomal metabolism      |Information on the type of disease                                          |
|                   |           |                            |                                                                            |
+-------------------+-----------+----------------------------+----------------------------------------------------------------------------+
|Clinical db genome | String    |GRCh37.p8                   |Genome version used in clinical Db                                          |
|build              |           |                            |                                                                            |
+-------------------+-----------+----------------------------+----------------------------------------------------------------------------+
|Disease_gene_model | String    |AR_hom:AR_Compound:AD       |Known Disease Inheritance Model                                             |
|                   |           |                            |                                                                            |
+-------------------+-----------+----------------------------+----------------------------------------------------------------------------+

.. _HGNC: http://www.genenames.org/
.. _OMIM: http://www.omim.org/
.. _HGMD: http://www.hgmd.org/
.. _GERP: http://mendel.stanford.edu/sidowlab/downloads/gerp/index.html
.. _SuperDups: http://varianttools.sourceforge.net/Annotation/GenomicSuperDups
.. _1000G: http://www.1000genomes.org/
.. _dbsnp: https://www.ncbi.nlm.nih.gov/projects/SNP/
.. _Esp6500: http://evs.gs.washington.edu/EVS/
.. _SIFT: http://sift.jcvi.org/
.. _PolyPhen 2: http://genetics.bwh.harvard.edu/pph2/
.. _MutationTaster: http://mutationtaster.org
.. _LRT: http://www.ncbi.nlm.nih.gov/pmc/articles/PMC2752137/
.. _PhyloP: http://bioinformatics.oxfordjournals.org/content/27/13/i266.full
.. _HPA: http://www.proteinatlas.org/
.. _gwas: http://www.genome.gov/gwastudies/
.. _Transfac: http://www.biobase-international.com/product/transcription-factor-binding-sites
