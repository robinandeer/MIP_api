IntersectCollect
================
Intersects and collects information (in any order) based on 1-4 keys present (mandatory) in each database file to be investigated.
The set of elements to be interrogated are decided by the first db file elements unless the merge option is used.
The db files are supplied using the ``-db`` flag, which should point to a database master file (tab-sep) with the format:

``{DATABASE PATH}\t{SEPARATOR}\t{COLUMN KEYS}\t{CHROMOSOME COLUMN}\t{MATCHING}\t{COLUMNS TO COLLECT}\t{FILE SIZE}``

NOTE: that matching should be either range or exact. Currently the range option only supports 3-4 keys i.e. only 3 keys are used to define the range look up (preferbly chromosome,start,stop). 
Range db file should be sorted -k1,1 -k2,2n if it contains chromosome information. If the merge option is used then all overlapping and unique elements are added to the final list. 
Beware that this option is memory demanding.

IntersectCollect requires a tab-separated plain text file (the database master file) describing:

1. The headers and columns to collect from the databases. 


2. The path to the database that holds the elements that subsequent database elements are to be merged to (if the keys match). 


3. The subsequent database(s) to match keys and merge elements from. 


Usage
-----
``perl intersectCollect.pl -db [DatabaseMasterFilePath] -o [Outfile]`` 

Installation
------------
IntersectCollect is written in Perl, so naturally you need to have Perl installed.

SetUp
-----

Database Master File
~~~~~~~~~~~~~~~~~~~~
* Line 1: ``outinfo:Header1=>{DATABASE NR IN FILE}_{COLUMN IN DATABASE},..,HeaderN``
* Line 2: ``{DATABASE PATH}\t{SEPARATOR}\t{COLUMN KEYS}\t{CHROMOSOME COLUMN}\t{MATCHING}\t{COLUMNS TO COLLECT}\t{FILE SIZE}``
	\.
	
	\.
* Line N: ``{DATABASE PATH}\t{SEPARATOR}\t{COLUMN KEYS}\t{CHROMOSOME COLUMN}\t{MATCHING}\t{COLUMNS TO COLLECT}\t{FILE SIZE}``

Explanation
~~~~~~~~~~~
#. Separator = Any separator that can be handled by Perls split function. 
#. Column keys = 1-4 column numbers designating the keys to be used in matching. Entry is comma-separated.
#. Chromosome column = The column number of the chromosome element.
#. Matching = range (3-4 keys) or exact (1-4 keys).
#. Columns to collect = The columns number that are to be collected (1..N). Entry is comma-separated.
#. File size = Small (read whole database to RAM) or large (handle database one chromosome at a time). 
