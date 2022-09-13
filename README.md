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

# How do you know your docking model is good to apply for larger ligand library

   * Enrichment - 
   
   Enrichment is essentially a high true positive rate in the top docked compound set. What we are looking for is the ability of the docking model to score known actives better than decoy compounds. In these graphs, we are evaluating how much of the docking results do we have to go through to recover all the known actives combined with decoy ligands in a compound set.
   
   * ROC plot - 
   
   An ROC curve, or Receiver Operator Characteristic curve, is the false positive rate on the x-axis versus the true positive rate on the y-axis. In a good docking experiment, performed on a retrospective set of known hits and supposed non-binders. A metric that is often used to quantify the quality of the ROC curve is the area under the curve, which is just as it sounds the area under the ROC curve. The closer to 1 this value is, the better the docking experiment was at enriching for known hits, and the more confidence you can have at taking this docking experiment and applying it to a larger series of unknowns.
   
*It is important to note that calculating enrichment is helpful during retrospective analyses - including model validation - and prospectively once you already have experimentally confirmed actives or inactives. Enrichment analyses cannot be done on compound libraries with no experimental data. While you could calculate the enrichment of some known actives that you docked along with your library, that is more of a retrospective validation of the quality of the model, than a prospective analysis of the quality of the virtual screen*

# Important to remember
         
  * docking is helpful in determining whether a molecule fits in a binding site and can be used for enriching ligand libraries with actives, but     docking scores are not designed to correlate with any measure of binding affinity and thus should not be used for rank-ordering compounds
        
  * it is always helpful to validate your receptor grid and overall docking model by docking known active ligands that have known poses, such as from a crystal structure of the ligand bound to a protein
         
  * Just as you perform positive controls in the laboratory, it is important to perform similar positive controls computationally to check that your calculation set up works well for the system or target molecule of interest. If you are unable to re-generate a pose sufficiently close to the co-crystallized ligand pose, then that is a sign that your docking model may not be not set up well for prospective use. Ideally, you would want to validate a docking model with several ligands that are known to bind to the target and that are known or expected to have the same binding mode.


# Ligand Pose Inspection Recommendations

   * Just because a compound docked doesn’t mean it will bind
   * Docking scores can be used/interpreted categorically
      * Look for trends between docked/active compounds (from the SAR) and docked/inactive compounds. A cutoff can be selected in the docking score between active and inactive compounds. Ideally, this cutoff will be based on a ROC plot constructed using docking scores for known actives and inactives (decoys). This will help to evaluate larger collections of compounds to dock.
      
      * For more read them : https://pubs.acs.org/doi/pdf/10.1021/acs.jmedchem.0c02227  and Pose+Inspection+Best+Practices.pdf
   

* Module 5 : Discuss the Ligand Based Virtual Screening

Ligand based screening does not include the receptor or target structure, on the other hand it only look into the known hit structure to identify the new hit (2D structure and 3D structure)
 
   * 2D  - Fingerprint searching, 2D QSAR, 2D pharmacophore 
   * 3D  - Shape-based, 3D QSAR , 3D pharmacophore 
   
   * Shape screening: hard sphere volume overlaps between active molecules and unknown HIT to assess the similarit
   Shape screening relies on hard sphere volumes overlaps to determine shape similarity, but it also allows you to project additional property information onto the spheres. 
   
   * Pharmacophore: A pharmacophore is an abstract representation of interactions that usually can be seen in structure-based screening. There six types representation. And four ways to develop pharmacophore hypotheses.

A pharmacophore is the ensemble of steric and electric features that is necessary to ensure the optimal supramolecular interactions with a specific biological target and to trigger or block its biological response.


# Here we completed a project of Shape-based screening of 15000 lignad database

Here we ran a CPU Shape screen to screen a database of over 15,000 ligands. This workflow can be used as a filter for more compute-intensive in silico predictions, or as part of a consensus scoring workflow along with other virtual screening methods.

Here we used probe ligand from 1OIT (Cyclin-dependent kinases (CDK2)) co-crystalized ligand (imidazo[1,2-a]pyridine), it is in its active conformation and has an IC50 of 3nM

   # Something about Cyclin-dependent Kinases
   
   Cancer has long been recognized as a disease of aberrant cellular proliferation. It is now known that proteins that regulate proliferation are frequently mutated, deleted or over-expressed in cancer cell lines, and that this leads to the deregulated growth of the tumour cell. Such proteins therefore represent potential targets for therapeutic intervention.

The cyclin-dependent kinases (CDKs) are a family of serine/threonine kinases that are important in controlling entry into and transition through each phase of the cell cycle.1 Their cellular activity is tightly regulated through a number of mechanisms:2 phosphorylation by kinases and dephosphorylation by phosphatases; the binding of specific activating proteins called cyclins; and the binding of inhibitory peptides such as members of the p16INK4A and p21CIP/p27KIP families. These inhibitory peptides must be either sequestered or destroyed, and the CDK appropriately phosphorylated and bound to its cyclin, before the enzyme is fully active. The synthesis and degradation of the activating cyclins is tightly controlled; this, together with their specificity for a particular CDK partner, causes first one, and then another member of the CDK family to become active and drive progression through the cell cycle.

The cyclin D1-CDK4/6-pRb signalling axis is a key mediator of growth control in normal cells and a frequent target for mutation in tumours, implicating CDK4 as an important biochemical target for small molecule inhibition of cell cycling. However, since cyclin D-dependent kinases are dispensable in cells lacking functional Rb, some tumours may be refractory to specific inhibition of CDK4. Recently, CDK2 has become an attractive target with the hypothesis that pharmacological inhibition of CDK2 might selectively kill tumour cells in which inactivation or loss of pRB serves to deregulate E2F activity.3 The development of CDK inhibitors with different selectivity profiles therefore potentially offers the opportunity to treat a wide range of tumour types. (for more: see the attached article)

Here we used Maestro to conduct shape screening. See the uploaded file: Module 5B - Shape-Based Screening of a 15,000 Ligand Database


# Module 6 - Ideation for Drug Discovery Projects with LiveDesign

This tutorial consists of eight sections:

* Creating LiveReports and Adding Compounds

* Adding, sorting, filtering anf coloring data

* Adding a SAR analysis: 
Structure Activity Relationship (SAR) analysis is a powerful tool to identify trends in activity and to identify gaps in the chemical space of your lead series. To perform a SAR analysis a scaffold (i.e. a minimal common substructure) and the location R-group substituents need to be defined. The LiveReport then populates with new columns, one for each R-group position, as well as one for the scaffold. We will use this information to see if we can identify different chemotypes within our compounds and how the various R-groups attached to them impact the IC50 values.

* Plotting and visualization data

* Adding Computed models

* creating a multi-prarameter profile (MPP):
At its heart, drug discovery is a multi-optimization problem that requires a balance among many parameters, such as potency, solubility, ADMET properties, etc. Multi-parameter profiles (MPPs) condense values for a collection of parameters into a single numeric value, i.e. the MPP score, allowing for rapid compound prioritization. The MPP score, which ranges from 0 (worst) to 1 (best), is based on the geometric mean of the parameters that comprise the MPP profile. Parameters can be computed properties (such as predicted solubility, docking scores, etc.), assay values (such as in vitro or in vivo potency, solubility, etc.) or a combination of the two. To create an MPP, you must define the following: (1) the parameters, (2) the value distribution type for each parameter and (3) the range of acceptable values for each parameter. In this section, we will create a simple “drug-likeness” MPP based on three calculated properties. This can help quickly triage new ligand ideas and condense the amount of properties to look at for a compound.

* Using freeform columns (FFC) for compound progression

* Creating a form for data drilldown

For more detail see the attached file : Module 6C - Ideation for Drug Discovery Projects 

# Module 7 - In this case study we tried to maintain or even improve potency of hit molecules against VEGFR-2 (responsible for glioblastoma multiforme) while improving physicochemical properties

VEGFR2 represents one of the first tragets of structure-based drug design. We improved potency of compounds starting from a hit series against VEGFR2 while optimizing predicted and measured drug properties. For that we created a new LiveReport in LiveDesign and used prepared VEGFR2 protein strcutures and grid files to perform various analyses.

* Kinases: Kinases coordinate the transfer of a phosphate, from a high energy molecule, like ATP to a substrate to affect a downstream change in the cell. Kinases are typically categorized based on what their substrates are. There are protein kinases, lipid kinases, carbohydrate kinases, and even small molecule kinases which help regulate the storage of energy in our cells. The majority of kinase drug targets fall under the category of protein kinases. 

* Protein Kinases:  Protein kinases can be further broken down into tyrosine, threonine, and serine kinases. These
categories refer to the residues of the protein that, once phosphorylated, confers a conformational change in the protein structure that activates the kinase. Often times, these residues are located in what is known as the activation loop. This is a loop between the
N-terminal lobe in gray and the C-terminal lobe in green that is phosphorylated. Once phosphorylated, this loop changes conformation and alters the structure slightly of the binding site.


On the N-terminal side of the activation loop is what is known as the DFG motif. The orientation of the motif is extremely important in kinase drug discovery and is something we will come back to later in this video. During the binding of ATP, the space between the N-terminal lobe and C-terminal lobe decreases, protecting ATP’s gamma phosphate from water and increasing the chance that the substrate is phosphorylated. Let’s take a closer look at the mechanism of a receptor tyrosine protein kinase, as this is the type of protein kinase we will be studying and targeting with molecular modeling approaches in this case study.

In the beginning of what is known as a cell-signalling cascade, VEGF binds to the N-terminal extracellular domain of the VEGFR, which consists of seven immunoglobin-like motifs. A single transmembrane alpha helix traverses the membrane and right on the intracellular side of the membrane is known as the juxtamembrane domain. This is then followed in sequence by the kinase domain and C-terminus.

Once VEGF binds to the extracellular domain...

...VEGFRs dimerize, leading to a conformational change that is transmitted across the membrane. This conformational change leads to activation.

Here, activation means phosphorylation of tyrosines in the juxtamembrane domain,...
Slide 11
...the activation loop of the kinase domain,...
Slide 12
...and the c-terminal domain. We will come back to why this phosphorylation leads to activation in a moment.
       
 Interestingly, this activation leads to different effects between VEGFR1 and VEGFR2. This is in part because VEGFR2 is kinase activating, whereas VEGFR1 is kinase impaired, which means it cannot catalyze the transfer of phosphate from ATP to a target. Instead, VEGFR1 undergoes a conformational change which leads to binding of adaptor proteins which then phosphorylates other downstream molecules.
In contrast, for VEGFR2, activity starts on the paired monomer of the dimer, leading to what is known as transphosphorylation. In VEGFR2, phosphorylation that occurs in the activation loop between the N-terminal domain and C-terminal domain of the protein, orients the loop away from the active site,...
Slide 13
...enabling the kinase domain to bind ATP and magnesium and efficiently phosphorylate substrates.
Phosphorylation of residues in the juxtamembrane domain and carboxyl terminus also plays a role, as shown by studies that have mutated tyrosine to phenylalanine.
Slide 14
Let’s zoom in one step further to the chemistry behind this signalling and take a look at the Sn2 mechanism of phosphate transfer. In the kinase active site, amino acids coordinate the alpha, beta, and gamma phosphates either directly or via magnesium.
Slide 15
The substrate to be phosphorylated complexes in the active site so a nucleophilic attack occurs at the gamma phosphate, leading to the formation of ADP and the phosphorylated substrate.
Slide 16
For VEGFR2, an example of a substrate is phosphoinositide 3-kinase, which is a lipid kinase important in angiogenesis. This is just one example in a web of kinase interactions that proceed after VEGFR2 activation. Let’s head over to Maestro to take a closer look at a VEGFR2 structure.
Maestro
Let’s load two VEGFR2 structures into Maestro. Go to File > Get PDB and load in 3B8R and 2QU5. Under Chain, type A. We won’t worry about preparing these structures as we will only be using them for visualization. Our reasons for loading these two structures has to do with their conformations, specifically the DFG-in versus DFG-out conformation. It can be confusing to understand what this means unless you see for yourself and interact with the structures in your Workspace. So, follow along with me and open a new Maestro project if you haven’t done so already. Don’t forget to save this as a new project!
     
 Now before we do anything we can align these structures so that we can easily compare the conformational differences between the structures. Make sure both structures are included, then go to Tasks and search for align. Select the Protein Structure Alignment option. This is a tool we are going to use in the case study to identify the best structures of our target to proceed within structure-based drug discovery. For now, let’s set the reference residues to ‘all’ and click Align. Fantastic, except the Workspace looks pretty cluttered. Let’s show the protein structure as ribbons and the ligand as tubes by going to Presets and selecting BioLuminate Default. That is much better! So we are going to do a few things to further modify the view of our proteins in the workspace: (1) color the N-terminal and C-terminal lobes white and green respectively, (2) color the activation loops of the kinase in yellow, (3) then will show the DFG residues for VEGFR kinase, and (4) finally we will look at the bound molecules to see where they are positioned relative to DFG motif.
With the N-terminal and C-terminal lobes we are going to use the sequence viewer to identify the domains. Let’s start with 3B8R so include 3B8R in the Workspace. If your sequence viewer is not below your Workspace, click on the plus sign in the bottom right corner of Maestro. Then toggle on the sequence viewer. The N-terminal lobe ends with lysine 920. If you hover your mouse over the residues in the sequence viewer, the residue numbers are shown in the tooltip. Click and drag from K920 all the way to the beginning of the sequence. This will select the N-terminal lobe of the kinase domain in the 3D Workspace as well as in the sequence viewer. Now that these residues are selected, edit the color of these residues by coming up to style, clicking on ribbons, and selecting a constant color of white for these residues. Pause the video to try the same thing on your own for 2QU5.
Let’s apply similar steps to more easily identify the activation loop and C-terminal lobe. Go back to the sequence viewer and find cysteine 1045. This time, click and drag to select through glutamate 1075. Change the color of the ribbon of these residues to yellow. Pause here and repeat this for 2QU5. We will leave the C-terminal lobe green. Now we have the different portions of our structures visually highlighted.
The last visual adjustment we are going to make to our proteins is the representation of the DFG motif. For the last time in this module, let’s come back to the sequence viewer and identify the DFG motif, which lies in sequence just N-terminal to the activation loop and contains residues numbered 1046 to 1048. Let’s show the residues of the DFG motif and color the carbons of the 3B8R DFG motif in cyan and the carbons of the 2QU5 DFG motif in orange. Pause the video here until you are caught up.
Let’s inspect our work. Change the view to tile, and then zoom out to inspect the differences in protein structure. 3B8R is missing the activation loop and what is known as the C-helix is oriented slightly differently compared to 2QU5.
Let’s zoom into the ligand to see what this DFG-in and DFG out really means. You can see that in 3B8R, the DFG motif has the phenylalanine facing in towards the center of the pocket between the N-lobe and C-lobe. In contrast, 2QU5 has the phenylalanine of the DFG motif facing much closer to the surface of the active site. So we can determine that 2QU5 is in the inactive DFG-out state while 3B8R is in the active DFG-in state. In any modeling task, it is important to make sure you are using a structure that is appropriate for the research question

you are asking. For example, make sure you are using the correct conformational state of a protein to dock ligands into for a virtual screen.
Slide 17
Great job! You learned about the different categories of kinases,...
Slide 18
...the mechanism of kinases,...
Slide 19
...and key structural motifs in the target we are going to study in this chapter and the next, VEGFR. In the next modules you will read a short publication on the Ins and Outs of Kinase DFG motifs and then read about the discovery of pazopanib against VEGFR kinases. Enjoy!



