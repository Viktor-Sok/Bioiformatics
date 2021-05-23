# Stages of MD simulation of small organic molecules using the *CHARMM36* force field (http://mackerell.umaryland.edu/charmm_ff.shtml).
## Preparing data
 1. Downloading the structure of a molecule in PDB/SDF formats from online databanks like the *Protein Data Bank*, *Pubchem*, etc., or building molecule manually in the software like *Avogadro*
2. Converting molecule to .mol2 format, for example, by using *Avogadro*.
3. Editing .mol2 file: replace line with stars by the  name of the molecule.
4. Using Perl script *correct_bond_order.pl* from the folder *Scripts_for_ pre-processing_data* to correct the bond order which is accepted by  *CHARMM36* force field. Command looks like <*$ perl correct_bond_order.pl asc.mol2 asc_clean.mol2*>
5. Generating topology of the molecule from .mol2 file by using the CGenff web server: https://cgenff.umaryland.edu/. It gives .str output file.
6. Converting .str to .itp and .prm files, which can be used by Gromacs for simulation.
   The python script  *cgenff_charmm2gmx_py3_nx1.py* from the *Scripts_for_ pre-processing_data* folder can be used like this: <*$ python cgenff_charmm2gmx.py asc asc_clean.mol2 asc_clean.str charmm36-jul2020.ff*>. 
  All the files and the force field folder *charmm36-jul2020.ff* should be in the same working directory.
   
      


## Defining system configuration in *GROMACS*
Defining the box 3x3x3 nm and solvating the molecule in water (using some king of water model, for instance, default spc216.gro from *GROMACS*)
The result will look like:
![Solvated ascorbic acid]( https://github.com/Viktor-Sok/Bioinformatics/blob/main/MD%20Simulation%20of%20small%20organic%20molecule%20(Ascorbic%20acid)/Pictures/asc_solvated..png?raw=true)
## Minimization of potential energy 
 In order to get rid of some steric problems after randomly placed water molecules from previous stage.
 It's not necessary to perform NVT and NPT ensembles equilibration for small organic molecules.
![Energy minimization](https://github.com/Viktor-Sok/Bioinformatics/blob/main/MD%20Simulation%20of%20small%20organic%20molecule%20(Ascorbic%20acid)/Pictures/em.png?raw=true)
## Simulation run
Result of 1ns simulation is shown below, trajectory coordinates are stored in .trr and .xtc files. 
![MD animation](https://github.com/Viktor-Sok/Bioinformatics/blob/main/MD%20Simulation%20of%20small%20organic%20molecule%20(Ascorbic%20acid)/Pictures/asc_animation.gif?raw=true)
## Performing the necessary analysis 
For example, Root Mean Square Deviation of the molecule's atoms along the trajectory can be colculated.
![Root Mean Square Deviation](https://github.com/Viktor-Sok/Bioinformatics/blob/main/MD%20Simulation%20of%20small%20organic%20molecule%20(Ascorbic%20acid)/Pictures/rmsd.png?raw=true)

