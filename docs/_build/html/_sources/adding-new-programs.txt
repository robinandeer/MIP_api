Adding a new program
=====================

1. DefineParameters - MIP input conversion

2. Add to `getoptions`

3. Supply if-block checking if the program should run

   a. Print to MIPLOGG + STDOUT
   b. For each family memeber call your subroutine with memberID + args.

4. Add a subroutine that submits your program script.

   a. Estimate runtime
   b. Write SBATCH headers
   c. Determine I/O directories
   d. Call FIDsubmit...

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