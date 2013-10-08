Installation
==============

1. On UNIX, install Perl5 by following these `instructions <http://learn.perl.org/installing/unix_linux.html>`_. It uses `Perlbrew <http://perlbrew.pl/>`_.

2. To switch to the new Perl installation, you might need to run

::
  
  INSTALLER_PERL_VERSION=5.16.0
  perlbrew switch perl-$INSTALLER_PERL_VERSION

3. To install the dependencies you can now run (``cpanm Module::Name``)

::
  
  cpanm YAML

4. You need to make sure all depedencies are installed and loaded (See :doc:`setup`). The most obscure program is: `qaTools <https://github.com/CosteaPaul/qaTools>`_. Start by downloading `samtools` v.0.1.18. qaTools needs this to build. Therefore you need to edit the `Makefile` in the qaTools directory to point to the `samtools`directory before running ``make``.