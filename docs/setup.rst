Setup
=====

Filename convention
~~~~~~~~~~~~~~~~~~~~~
The permanent filename should follow the following format::

  {LANE}_{DATE}_{FLOW CELL}_{IDN}_index{BARCODE SEQ}_{DIRECTION 1/2}.fastq.qz

Dependencies
~~~~~~~~~~~~~~
Make sure you have loaded/installed all dependencies and that they are in your PATH. You only need to load the dependencies that are required for the modules that you want to run. If you fail to install dependencies for a module MIP will tell you what dependencies you need to install and exit.

**Program/Modules**

- Perl `YAML.pm`_ module, since this is not included in the perl standard
  distribution (if you want to supply config files to MIP)
- Simple Linux Utility for Resource Management (`SLURM`_)
- `FastQC`_
- `Mosaik`_
- `BWA`_
- `SAMTools`_
- `BedTools`_
- `PicardTools`_
- `Chanjo`_
- `GATK`_
- `ANNOVAR`_
- intersectCollect.pl (Supplied with MIP)
- add_depth.pl (Supplied with MIP)
- rank_list_filter.pl (Supplied with MIP)
- `VcfTools`_
- `PLINK`_

Depending on what programs you include in the MIP analysis you also need to add
these programs to your ``PATH``:

- FastQC
- Mosaik
- BWA
- Chanjo
- SAMTools
- BedTools
- PicardTools
- VcfTools
- PLINK


On UPPMAX
---------
Add modules::

  module load java/sun_jdk1.7.0_25 FastQC mosaik-aligner bwa BEDTools plink vcftools annovar

You do best installing both GATK and PicardTools yourself. Make sure to load the correct Java environment to run these tools.

.. note::
  N.B. `plink` needs to be loaded *before* `PicardTools`.

The current version of FASTQC is only tested under Java 1.6. Therefore we can't use the latest version of GATK which requires Java 1.7!

Moving files from INBOX
~~~~~~~~~~~~~~~~~~~~~~~
FASTQ-files should be moved from `/INBOX` to a backed up directory.

1. Check the :doc:`pedigree_file` and move to a backed up directory ("exomes")
2. Move and rename gzipped FASTQ-files into ``{SEQ TYPE}/{IDN}/fastq``, where :doc:`IDN` is your sample ID.


EnvironmentUppmax flag
~~~~~~~~~~~~~~~~~~~~~~
The ``-environmentUppmax`` flag is used to cut down on the number of flags that you have to specify when lacking a config.yaml file. 
It sets the standard defaults used at CMMS. Thus you can start an analysis for a whole family with::

  perl mip.pl -env_up 1 -f 1 


.. _YAML.pm: http://search.cpan.org/~mstrout/YAML-0.84/lib/YAML.pm
.. _Mosaik: https://github.com/wanpinglee/MOSAIK
.. _BWA: http://bio-bwa.sourceforge.net/
.. _FastQC: http://www.bioinformatics.babraham.ac.uk/projects/fastqc/
.. _SAMtools: http://samtools.sourceforge.net/
.. _BedTools: http://bedtools.readthedocs.org/en/latest/
.. _SLURM: http://slurm.schedmd.com/
.. _PicardTools: http://picard.sourceforge.net/
.. _Chanjo: https://chanjo.readthedocs.org/en/latest/
.. _GATK: http://www.broadinstitute.org/gatk/
.. _ANNOVAR: http://www.openbioinformatics.org/annovar/
.. _VcfTools: http://vcftools.sourceforge.net/
.. _PLINK: http://pngu.mgh.harvard.edu/~purcell/plink/data.shtml