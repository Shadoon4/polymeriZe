# polymeriZe
construct polyacrylate polymers from properly formatted input monomer files
To create a random polymer, run the script "mass_strand_production"
This will iterate to create 16 17-mer strands, using the script "grow_poly.py"
A description of how "grow_poly.py" can be used, and how it works, can be found in the comments of the script itself, and is recopied here
2 of the monomers are cap groups, and then 15 are the random monomers to be used in the final strand

Here, fragments of a random copolymer with 20% benzyl acrylate is created
Other monomers can be found in the directory "extra_monomers"


instructions for "grow_poly.py"
#USER INSTRUCTIONS
# You can run the script using "python grow_poly.py"
# Edit the user parameters to change the main monomers, the "extra" monomers, the desired polymer length, and the proportion of monomers that will be "extra"
# Prior to doing so, make sure you have all of the required files, listed below
# For the "extra" monomers used in the copolymerization, you should ensure you have both enantiomers of monomer, and also have those files listed in "extra_poly" (see user parameters)
#END USER INSTRUCTIONS

#REQUIREMENTS:
  #The packmol executible (compiled at ~mrobo/packmol/)
  #The packmol script "packmol_center.inp"
  #Fomatted pdb files for the monomer units:
    #main 2-ethyl-hexyl monomers: "r1_2-ehx.pdb", "r1_2-ehx.pdb", "s1_2-ehx.pdb", "s2_2-ehx.pdb",
    #(optional) alt 2-ethyl-hexyl monomers: "alt_r1_2-ehx.pdb", "alt_r1_2-ehx.pdb", "alt_s1_2-ehx.pdb", "alt_s2_2-ehx.pdb"
    #monomers associated with the copolymer: (In this example) "benzyl-1.pdb", "benzyl-2.pdb"
  #Formatted pdb files for the start and end monomers:
    #seed.pdb
    #cap.pdb
#END REQUIREMENTS

In this directory, we take the fragments generated in step 1, and optimize them using CHARMM. Additionally, the fragments are stretched out using the AFM module in CHARMM. This makes combining the individual fragments into one big fragment much easier.

The final optimized strands are located in the directory "pdbout".

Note that this requires the generation of CHARMM parameters and topologies for each individual monomer, if you have not already done so. The parameters used in this example are in universal.prm, and the topologies are in poly_residue.rtf.

In this directory, we take the fragments generated in step 1, and optimize them using CHARMM. Additionally, the fragments are stretched out using the AFM module in CHARMM. This makes combining the individual fragments into one big fragment much easier.

The final optimized strands are located in the directory "pdbout".

Note that this requires the generation of CHARMM parameters and topologies for each individual monomer, if you have not already done so. The parameters used in this example are in universal.prm, and the topologies are in poly_residue.rtf.
[tjugovic@athena:~/CHARMMheader/Microplastics/Construction_Water/polymer_construction/1.frag_construction] cat ../3.final_construction/README 
In this directory, we take the optimized 17mer strands and turn them into big (242mer) strands.
A simplified procedure is given below
1. Copy the strand_??.out.pdb files from the "pdbout/" directory from the previous step
2. Run the script "setup_splicing". This will cut off the first and last residues from each strand.
3. Run the script "mass_splicing". This script uses the "splice_poly.py" python script to create new big strands.

The process of creating a 242mer (16 15mer strands, plus first and last capping residues) is handled by the "splice_poly.py" script. It uses the same strategy as the "grow_poly.py" script in the first step. The instructions and requirements for its use are commented in the script, and are reprinted here.

The big strands created in the previous step can then be copied here, and optimized using the charmm scripts provided here.

PDB snapshots of the optimized systems are provided in the pdbout directory
