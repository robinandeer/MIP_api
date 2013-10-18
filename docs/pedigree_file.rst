Pedigree File
=============

Family meta data file. Records important metrics for tracking samples and find biases in 
isolation of DNA or subsequent sequence analysis.

Among other things, the file enables:

1. automatic coverage calculation (correct target file(s))

2. application of mendelian filtering models, e.g. `autosomal dominant`, based on pedigree, sex and disease status

3. collection of analysis info for the sequence analysis pipeline 

The pedigree file format is defined by `PLINK`_, although we currently only support tab-sep pedigree files. 

The first row should start with a "#" (hash) and contain relevant headers separated by tabs describing each column.
The first six columns are mandatory. The name and order of the headers should follow:

.. csv-table:: Mandatory Columns
  :header-rows: 1
  :widths: 1 1 4
  :file: pedigree_file_mandatory_columns.csv

In addition to these mandatory columns we use the pedigree file to record meta data on each individual.
Entries within each column should be separated with ";" (semi-colon) and entered in consecutive order.  
Each individual recorded in the pedigree file is written on one line and a tab should 
separate each entry. No individual should be recorded twice. The order of individuals below
the header line does not matter.

If there is no information on the parents or the grandparents they should be encoded as “0”. 

On UPPMAX
---------
.. note::
 Changes to the pedigree file format will be recorded in this document.

The pedigree file should named: ``<FDN>_pedigree.txt``.

.. csv-table:: Additional columns in the pedigree file
  :header-rows: 1
  :widths: 1 1 4
  :file: pedigree_file_optional_columns.csv


Supported capture kits
^^^^^^^^^^^^^^^^^^^^^^^

* Agilent Sure Select

  * SureSelect_All_Exon_G3362_with_annotation_hg19_bed => Agilent_SureSelect.V2
  * SureSelect_All_Exon_50mb_with_annotation_hg19_bed => Agilent_SureSelect.V3
  * SureSelect_XT_Human_All_Exon_V4_targets.bed => Agilent_SureSelect.V4

* NimbleGen

  * SeqCap_EZ_Exome_v2.bed => Nimblegen_SeqCap.V2

Example
------------------
.. csv-table:: Example
  :header-rows: 1
  :file: pedigree_file_example.csv

Abbrevations
--------------
.. csv-table:: 
  :header-rows: 1
  :file: pedigree_file_abbreviations.csv


.. _PLINK: http://pngu.mgh.harvard.edu/~purcell/plink/data.shtml