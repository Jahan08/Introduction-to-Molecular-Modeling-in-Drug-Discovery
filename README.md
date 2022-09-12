Hello and welcome to the Introduction to Molecular Modeling in Drug Discovery course, part of the Schrödinger online learning platform. In this course, we will discuss how to use molecular modeling in 

    * hit identification, 
    * hit-to-lead ideation, and 
    * compound property and potency optimization

# High-throughput virtual screens 

High-throughput virtual screens have suffered from quality issues, and because of this, the docking score that is output from a virtual screen should in no way be used as a metric to compare with ligand affinities. Recent findings from the Shoichet lab using ultra-large docking libraries suggest that some of the quality issues that have plagued high throughput virtual screening in the past may be partially resolved with the screening of more compounds that cover more of chemical space. This is because it is now possible to dock libraries of compounds with over 100 million ligands in a reasonable amount of time, and thus screen more of chemical space.

# Lead Optimzation
The optimization of primary hits from screening is another area where molecular modeling can be of service. Historically, lead optimization strategies have consisted of building up structure-activity relationships consisting of hundreds of compounds that take several years to synthesize and test the safety, metabolic stability, chemical stability, absorption, and solubility of these leads - all while maintaining favorable efficacy.


# This course includes the following:

1) An introduction to molecular modeling
2) Video tutorials to familiarize you with the Maestro interface
3) Virtual screening applications and analyses
4) Discussion of how to ideate new molecules in 3D
5) A hands-on project at the end of the course

In this course, we will be using Maestro and LiveDesign to introduce these concepts, but many of the concepts we cover will apply to other software packages as well.

We got access Maestro though Amazon Web Service or AWS

# Virtual Screening

Methods of virtual screening can be characterized as either structure-based or ligand-based, depending on what is the primary source of information. With structure-based virtual screening, the structure of the protein or target of interest is used to inform compound design. This approach takes into account three dimensions of data when trying to bind that structure. Some examples of structure-based methods including docking as well as pharmacophore screening. More recently, some QSAR methods are able to incorporate the binding site into the model. In virtual screening, which can be both structure-based and ligand-based, an array of compounds are screened based on some identified 2D or 3D properties.

* Module 4 : Discuss the Structure Based Virual Screening

Docking works by placing different conformations of a compound of interest in a defined binding site. The orientation of the ligand relative to the target’s residues is then optimized resulting in what we call a ligand “pose.” These are the general steps used by Glide, Schrӧdinger’s docking application. The first step is docking, which is when the computer attempts to pose a ligand in a binding site. The next step is scoring the docked poses to give us an idea of which poses are more favorable than others. The last step of virtual screens is filtering the compounds based on additional criteria, such as having an interaction with certain residue.

Docking - The type of docking that we are going to be performing in this module will use a grid representation for the binding site. This makes the docking process a lot faster by essentially converting the atomic-level structure of a protein binding site, shown here as cyan ribbons, to a series of grid points. There are different values at each grid point to signify the presence or absence of protein versus empty space. You can think of these different grids as a series of consecutive sieves with the mesh becoming more fine. Poses are, in a sense, filtered out as they clash with the grid points, or the mesh in our sieve illustration. This allows the docking algorithm to quickly evaluate a ligand library. The grid space is defined within the magenta box. The green box around the ligand signifies where the ligand centroid must reside to reduce the amount of computation done in the docking and not evaluate extraneous parts of the receptor. We’d recommend checking out resources on Schrodinger.com, including publications that have deployed virtual screening with Glide.

Scoring - Once the ligand conformations have been docked into the protein, the poses are then scored based on shape complementarity, electrostatic interactions, pi-pi stacking interactions, and more. With Glide, the more negative the score, the better - similar to the change in relative free energy. Glide scores are specific to a particular receptor system, so they cannot be compared across different proteins. For instance, here, a Glide score of -11 represents a good binder and -5 represents a bad binder. But a score of -11 will not always represent a good binder. Depending on your structures, a score -11 might be associated with mediocre binders one protein while a score of -8 might indicate a great binder for another protein.

An important thing to know about scoring functions, is that they ​do not​ correlate with any binding affinity measurements. While this may seem disheartening, it doesn’t mean docking scores aren’t useful. By using a rigid receptor, we are deviating too much from how this protein would behave in a wet-lab assay to provide a rank-ordering of the compounds or exact agreement with experimental binding affinities. However, docking can achieve much higher throughput than a wet-lab assay, especially if you factor in the time it takes to purify a protein, synthesize compounds, and develop an assay. Docking results can allow you to quickly triage a large compound library by allowing you to take a subset of those compounds with good docking scores and evaluate them further with more computationally expensive, but more scientifically rigorous calculations. Docking is best used to give good enrichment of a compound library


   * A simple workflow of virtual Screening

First, it is critically important to prepare the files of the target and hit molecules. While you have been provided with a few prepared files in this course, this is something that needs to be done before starting any modeling work. Using our prepared protein, we generate a receptor grid and perform a docking experiment on a test case. For us in this module, our test case will be to dock the cognate ligand back into the crystal structure. If the RMSD compared to the original pose is low (such as less than 2.5 angstrom or less, depending on the size of the ligand), then you can feel confident in the docking set up and proceed to screening a larger database. If the RMSD is high, it may behoove you to return to the generate the grid stage and input new or different constraints or details of the ligand box. 
   
   Prepare the protein and ligand(s) (set constraint) -> Generate a grid (docking) -> Reality check with test case (with co-crystalized ligand) (RMSD is          low) -> Screen a larger database (otherwise repeat from constraint setting) -> Analyze the results
   
Once you have screened a larger database, you can analyze the results using some statistical analyses such as receiver operating curve, or ROC plot

# How do you know your docking model is good to apply for larger ligand libaray

   * Enrichment - 
   
   Enrichment is essentially a high true positive rate in the top docked compound set. What we are looking for is the ability of the docking model to score known actives better than decoy compounds. In these graphs, we are evaluating how much of the docking results do we have to go through to recover all the known actives combined with decoy ligands in a compound set.
   
   * ROC plot - 
   
   An ROC curve, or Receiver Operator Characteristic curve, is the false positive rate on the x-axis versus the true positive rate on the y-axis. In a good docking experiment, performed on a retrospective set of known hits and supposed non-binders. A metric that is often used to quantify the quality of the ROC curve is the area under the curve, which is just as it sounds the area under the ROC curve. The closer to 1 this value is, the better the docking experiment was at enriching for known hits, and the more confidence you can have at taking this docking experiment and applying it to a larger series of unknowns.
   
*It is important to note that calculating enrichment is helpful during retrospective analyses - including model validation - and prospectively once you already have experimentally confirmed actives or inactives. Enrichment analyses cannot be done on compound libraries with no experimental data. While you could calculate the enrichment of some known actives that you docked along with your library, that is more of a retrospective validation of the quality of the model, than a prospective analysis of the quality of the virtual screen*

         # Important to remember
         * docking is helpful in determining whether a molecule fits in a binding site and can be used for enriching ligand libraries with actives, but     docking scores are not designed to correlate with any measure of binding affinity and thus should not be used for rank-ordering compounds

* Module 5 : Discuss the Ligand Based Virtual Screening


