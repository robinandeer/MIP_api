Adding a new program
=====================

You need to perform a series of tasks to properly add a program to MIP. An overview of the steps can be found here:

1. Add a call to DefineParameters

2. Add relevant command line arguments to `getoptions`

3. Supply an if-block checking if the program is set to run

  a. Print program name to the MIPLOGG + STDOUT
  b. Call your custom subroutine (ses below) with relevant parameters

4. Write a custom subroutine that generates and submits your program script.

  a. Writes SBATCH headers
  b. Builds out the body of the SBATCH script
  c. Calls FIDsubmit

More details follow below. `chanjo, a program which is part of the coverage analysis, will be used as an example throught this guide.

1. DefineParameters
--------------------
This subroutine takes a number of input parameters. There are basically three parameter types: "program", "file", and "attribute".

[INSERT TABLE]

.. note::
  
  The second parameter "Parameter value" will be deprecated and removed in
  a future release of MIP.

.. note::

  A 10th parameter will be added and represent the actual program handle which is used to check if the program is installed before running MIP.

2. GetOptions
--------------
This is the method that parses the command line input and stores the options. To add your own defined parameters you need to add lines like this::

  '<short_option>|<long_option>:<s(tring)/n(umber)>' => \$parameter{'<long_option>'}{'value'},

You should replace anything that looks like ``<placeholder>``::

  'pCh|pChanjo:n' => \$parameter{'pChanjo'}{'value'},

Again, program options begin with a leading "p" by convention. Make sure you don't cause any naming conflicts.

.. note::

  MIP doesn't use True/False flags so you should always specify a following argument. This makes it possible to turned on (1), off (0) and run programs in dry mode (2). All program options should specify "n(umber)" as option type.

3. if-block
------------
The if-block has a number of uses. First it should check whether the program has been set to run::

  if ($scriptParameter{'pChanjo'} > 0) {
    # Body...
  }

Next (inside if-block) it should print an announcement to 2 file handles::

  my announcemnet = "\nChanjo\n"  # Keeping it dry :)
  print STDOUT announcemnet; print MIPLOGG announcemnet;

Lastly it should call the custom subroutine, e.g. for each individual sample::

  foreach my $sampleID (@sampleIDs) {
    chanjo(
      $sampleID,
      $scriptParameter{'familyID'},
      $scriptParameter{'chanjoStore'}
    );
  }

4. Custom subroutine
---------------------
To keep `mip.pl` clean it's helpful to write the custom subroutine as a separate Perl module/file and subsequently import it into `mip.pl`. Below follow basic instruction but for more details and explainations on how this is done you should check out this `blog post <http://www.perlmonks.org/?node_id=102347>`_.

The first few lines are mostly boilerplate code that makes Perl regonize the file as a proper module. In the following example you should only need to replace placeholders like "<placeholder>" to fit your program::

  use strict;
  use warnings;

  package <Coverage>;

  use Exporter;
  use vars qw($VERSION @ISA @EXPORT @EXPORT_OK);

  $VERSION     = 1.00;
  @ISA         = qw(Exporter);
  @EXPORT      = ();               # Auto export (not recommended)
  @EXPORT_OK   = qw(<chanjo>);     # Export on request 

Next up is the actual subroutine::

  sub chanjo {
    # Body...
  }

First off we should assign relevant local variables passed into the subroutine::

  my $sampleID = $_[0];
  my $familyID = $_[1];
  my $aligner = $_[2];

4a. SBATCH headers
~~~~~~~~~~~~~~~~~~~~
SBATCH headers are written by the `ProgramPreRequisites` subroutine. It takes a number of input arguments listed here:

[INSERT TABLE]

4b. Build SBATCH body
~~~~~~~~~~~~~~~~~~~~~~
This step is pretty much up to you. You simply do what you have to in order to print out what's required for running the program to the file handle you defined in "4a"::

  print CHANJO "
  # ------------------------------------------------------------
  #  Create a temp JSON file with exon coverage annotations
  # ------------------------------------------------------------\n";
  print CHANJO "chanjo annotate $storePath using $bamFile";
  print CHANJO "--cutoff $cutoff";
  print CHANJO "--sample $sampleID";
  print CHANJO "--group $familyID";
  print CHANJO "--json $jsonPath";

.. note::

  WAIT COMMAND???

That means we are done with the subroutine. Only one thing left; don't forget to end the *file* by returning 1 (or "True")::

  return 1;
  __end__

For your convinience a template program module can be found in the project folder hosted on GitHub. [ADD LINK TO TEMPLATE]

Program prerequisites
-----------------------
Determine SBATCH headers

1. SampleID/FamilyID

2. Program name

3. ...

4. ...

5. Program handle (CLI)

6. Cores

7. Runtime estimate