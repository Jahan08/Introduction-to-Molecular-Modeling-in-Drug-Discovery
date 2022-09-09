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

   * A simple workflow of virtual Screening
   
   Prepare the protein and ligand(s) (set constraint) -> Generate a grid (docking) -> Reality check with test case (with co-crystalized ligand) (RMSD is          low) -> Screen a larger database (otherwise repeat from constraint setting) -> Analyze the results

* Module 5 : Discuss the Ligand Based Virtual Screening


