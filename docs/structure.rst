Stucture
=======================================

mip.pl
---------------------------------------
Central hub and likely the only script users will ever interact directly with.

.. code-block:: console
  
  echo "Running MIP on Uppmax, analyzing all samples in family 10"
  $ perl mip.pl -env_up 1 -f 10

intersectCollect.pl
---------------------------------------
Intersects and collects information based on 1-4 keys present (mandatory) in each file to be investigated...


mip_align.pl
---------------------------------------

mip_variation.pl
---------------------------------------

rank_list_filter.pl
---------------------------------------

collect_info.pl
---------------------------------------

add_depth.pl
---------------------------------------

covplots_exome.R / covplots_genome.R
---------------------------------------
Plots coverage across chromosomes.
