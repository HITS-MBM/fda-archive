fda-archive
===========

Background
----------

Calculations of internal forces and stress distributions have long been used by mechanical engineers in designing strong structures, from tall sky-scrapers and kilometer-long bridges to Formula 1 cars and aircraft wings. The same kind of analysis, but applied to atomic and molecular level, could shed light onto the mechanical stability of (bio)molecules, allosteric mechanisms and signal propagation in cells or mechanically induced processes such as blood coagulation.

Molecular dynamics (MD) simulations apply Newton's equations of motion to atomic systems. During each integration time step, atoms interact with each other through pairwise forces. All pairwise forces acting on an atom are summed up and the resulting force determines the displacement of the atom in the next time step. These displacements are then typically used to analyze MD simulations.

The analysis of individual atomic pairwise forces, which we call Force Distribution Analysis, can offer a much more sensitive view of a (bio)molecular system, be it in a stable state or during a transition between states. Such analysis would be able to explain, for example, the functioning of an atomic level Newton's cradle, where the application of force on an atom does not translate directly into a displacement of all spheres but only of the outer ones. Similarly, atoms can propagate forces in the absence of any significant atomic displacements, for example through a protein's rigid core.

Under the generic name of Force Distribution Analysis, you can find here both the initial implementation, simply called FDA, and the newest development, called Time-resolved FDA or TRFDA. In addition to tracking changes in pairwise forces, the implementation of TRFDA fixes several shortcomings of FDA and extends it to a unified treatment of atomic- and residue-level pairwise forces as well as stress calculations. Both implementations are based on the GROMACS MD package.

Stable states versus dynamic processes
--------------------------------------

FDA focuses on the analysis of averaged dynamical data. This makes sense only for simulations at quasi-equilibrium, i.e. for MD simulations sampling a single energy well. There should be no significant structural changes during the simulation and, therefore, pairwise forces are supposed to be relatively constant apart from thermal fluctuations. Such an MD simulation could be the equilibration of a protein, in the presence or absence of a ligand or a constant force. FDA can also be used to find differences in the distribution of internal forces between two or more stable states, like those between an apo and a ligand-bound state, which could be associated with an allosteric mechanism. Likewise, differences in force distribution between a molecule under high and low external force can give insight into structural motifs involved in bearing the external load.

In contrast, TRFDA focuses on the analysis of changes in pairwise forces over time. Such changes appear e.g. during MD simulations of protein unfolding or other conformational transitions, in atomic level signal propagation or upon molecular association. Starting from pairwise forces, TRFDA can also calculate an atomic level stress, which we call punctual stress; changes in the stress distribution offer a view of the mechanical stability of the simulated molecular system.

Citations
---------

If you use the TRFDA code, please cite: http://dx.doi.org/10.1186/2046-1682-6-5
If you use the FDA code, please cite: http://dx.doi.org/10.1186/1471-2105-12-101 

Download, installation and documentation
----------------------------------------

Although TRFDA offers a super-set of FDA functionality, the FDA code and R library remain available.

The C code for obtaining pairwise forces is integrated with GROMACS. The typical GROMACS installation instructions apply.

Note: Although the method is called FDA, the code dealing with pairwise force was historically called "pf" (from Pairwise Forces). TRFDA maintained this convention, the code being called "pf2" (from Pairwise Forces version 2).
TRFDA

Source packages containing the TRFDA code integrated into GROMACS 4.5.3 and the VMD plugins:

    [gromacs-4.5.3_pf2_20130323.tar.gz](gromacs-4.5.3_pf2_20130323.tar.gz)
    [vmd-plugins_pf2_20120829.tar.gz](vmd-plugins_pf2_20120829.tar.gz) 

TRFDA manual containing installation instructions, user documentation and description of the file formats:

    [PF2-manual_20120829.pdf](PF2-manual_20120829.pdf) 

TRFDA tutorial for obtaining and visualizing changes in pairwise forces and punctual stress (edit paths then execute the included run.sh script):

    [tutorial_pf2.tar.gz](tutorial_pf2.tar.gz) 

FDA

Source packages containing the FDA code integrated into GROMACS 4.0.5 and the R package (called FDAtools) which provides functionality to import and analyze pair-wise forces directly in R:

    [gmx_4_0_5_fda.tar.gz](gmx_4_0_5_fda.tar.gz)
    [FDAtools_1.0.tar.gz](FDAtools_1.0.tar.gz) 

FDA manual containing user documentation and description of the file formats:

    [fda_manual.pdf](fda_manual.pdf)

File needed for the FDA tutorial:

    [fda_tutorial.zip](fda_tutorial.zip) 

Installing the FDAtools package
-------------------------------

FDAtools depends on [bio3d](http://mccammon.ucsd.edu/%7Ebgrant/bio3d) and SparseM. Please download the bio3d package.

Mac / Linux user, check that your R_LIBS variable points to the folder in which packages should be installed (insert an export R_LIBS="..." in your .profile / .bashrc if not previously done).

Install bio3d by executing 'R CMD INSTALL bio3d_1.0-6.tar.gz'.

Install SparseM by executing 'install.packages("SparseM")' in an R console.

Now we are ready to install FDAtools, just type 'R CMD INSTALL FDAtools_1.0.tar.gz' (exchange version number to the version you want to install) on the command line.
