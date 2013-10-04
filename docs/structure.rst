Structure
=======================================

mip.pl
---------------------------------------
Central hub and likely the only script most users will ever interact directly with.

.. code-block:: console
  
  echo "Running MIP on Uppmax, analyzing all samples in family 10"
  $ perl mip.pl -env_up 1 -f 10

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

covplots_exome.R / covplots_genome.R
---------------------------------------
Plots coverage across chromosomes.
