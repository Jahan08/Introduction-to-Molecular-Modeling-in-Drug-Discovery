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

![Alt text](https://github.com/Jahan08/Introduction-to-Molecular-Modeling-in-Drug-Discovery-Maestro-LiveDesign-/blob/main/Pic2.png "Kinase Mechanism")

![Alt text](https://github.com/Jahan08/Introduction-to-Molecular-Modeling-in-Drug-Discovery-Maestro-LiveDesign-/blob/main/Pic1.png "VEGFR2")

* Kinases: Kinases coordinate the transfer of a phosphate, from a high energy molecule, like ATP to a substrate to affect a downstream change in the cell. Kinases are typically categorized based on what their substrates are. There are protein kinases, lipid kinases, carbohydrate kinases, and even small molecule kinases which help regulate the storage of energy in our cells. The majority of kinase drug targets fall under the category of protein kinases. 

* Mechanism of Protein Kinases:  Protein kinases can be further broken down into tyrosine, threonine, and serine kinases. These categories refer to the residues of the protein that, once phosphorylated, confers a conformational change in the protein structure that activates the kinase. Often times, these residues are located in what is known as the activation loop. This is a loop between the N-terminal lobe in gray and the C-terminal lobe in green that is phosphorylated. Once phosphorylated, this loop changes conformation and alters the structure slightly of the binding site.

On the N-terminal side of the activation loop is what is known as the DFG motif. The orientation of the motif is extremely important in kinase drug discovery. During the binding of ATP, the space between the N-terminal lobe and C-terminal lobe decreases, protecting ATP’s gamma phosphate from water and increasing the chance that the substrate is phosphorylated.

In the beginning of what is known as a cell-signalling cascade, VEGF binds to the N-terminal extracellular domain of the VEGFR, which consists of seven immunoglobin-like motifs. A single transmembrane alpha helix traverses the membrane and right on the intracellular side of the membrane is known as the juxtamembrane domain. This is then followed in sequence by the kinase domain and C-terminus.

Once VEGF binds to the extracellular domain ...VEGFRs dimerize, leading to a conformational change that is transmitted across the membrane. This conformational change leads to activation.Here, activation means phosphorylation of tyrosines in the juxtamembrane domain,....the activation loop of the kinase domain,...and the c-terminal domain.

this activation leads to different effects between VEGFR1 and VEGFR2. This is in part because VEGFR2 is kinase activating, whereas VEGFR1 is kinase impaired, which means it cannot catalyze the transfer of phosphate from ATP to a target. Instead, VEGFR1 undergoes a conformational change which leads to binding of adaptor proteins which then phosphorylates other downstream molecules. In contrast, for VEGFR-2, activity starts on the paired monomer of the dimer, leading to what is known as transphosphorylation. In VEGFR-2, phosphorylation that occurs in the activation loop between the N-terminal domain and C-terminal domain of the protein, orients the loop away from the active site,...

..enabling the kinase domain to bind ATP and magnesium and efficiently phosphorylate substrates. Phosphorylation of residues in the juxtamembrane domain and carboxyl terminus also plays a role, as shown by studies that have mutated tyrosine to phenylalanine.

Let’s zoom in one step further to the chemistry behind this signalling and take a look at the Sn2 mechanism of phosphate transfer. In the kinase active site, amino acids coordinate the alpha, beta, and gamma phosphates either directly or via magnesium. The substrate to be phosphorylated complexes in the active site so a nucleophilic attack occurs at the gamma phosphate, leading to the formation of ADP and the phosphorylated substrate. For VEGFR-2, an example of a substrate is phosphoinositide 3-kinase, which is a lipid kinase important in angiogenesis. This is just one example in a web of kinase interactions that proceed after VEGFR2 activation. 

# Important Terms to Understand Kinases Better

* Activation loop: The loop of a kinase that lies between the N-terminal and C-terminal lobes of the kinase and, when phosphorylated, enables a conformational change in the loop to activate the kinase.

* ATP: Adenosine triphosphate. ATP is an adenosine molecule bound to three phosphates that drive many of the energetic pathways of cells.

* C-terminal lobe: The region in kinases that is most C-terminal and consists of approximately 180 amino acids on average. The cleft between this lobe and the N-terminal lobe is where the ATP binding cleft sits.

* DFG motif: The aspartic acid, phenylalanine, and glycine that are found in sequence on the N-terminal end of the activation loop in kinases. The phenylalanine of this motif can assume either the DFG-in or DFG-out structure in the active or inactive states of the kinase, respectively.

* Dimer: A molecular complex consisting of two molecules of the same type (e.g. two proteins) that interact in quaternary structure.
Immunoglobulin domain: A type of protein domain that consists of a 2-layer sandwich of 7-9 antiparallel β-strands arranged in two β-sheets with a Greek key topology, consisting of about 125 amino acids. These domains are commonly found in antibodies.

* Juxtamembrane domain: A disordered domain in receptor tyrosine kinases that lies in sequence between the transmembrane helix and the kinase domain.

* Kinase: An enzyme that transfers a phosphate group from a high energy metabolite, like ATP, to a target structure. These types of enzymes represent one of the most researched protein classes in drug design.

* N-terminal lobe: The region in kinases that is nearest the N-terminus and consists of approximately 80 amino acids. The cleft between this lobe and the C-terminal lobe is where the ATP binding site is located.

* P-loop: The beta-loop-beta domain in the N-terminal lobe that borders the active-site of kinases.
Sequence Viewer: A region in the Maestro interface below the Workspace that contains the sequence of a protein within the Workspace in one-letter code. This can be toggled on and off by clicking the + in the Workspace Configuration Toolbar in the bottom right corner.

* Serine: An amino acid with a hydroxyl moiety attached to the beta carbon in the side chain. This is the site of phosphorylation in serine kinases.
Threonine: An amino acid with a methyl and hydroxyl moiety attached to the beta carbon in the side chain. This is the site of phosphorylation in threonine kinases.

* Transautophosphorylation: When another kinase of the same type (in our case, one of the monomers in the VEGFR2 kinase dimer) provides the active site that carries out the kinase chemistry.

* Tyrosine: An amino acid with a phenol side chain attached to the beta carbon. This is the site of phosphorylation in tyrosine kinases.
Vascular Endothelial Growth Factor Receptor 2 (VEGFR2): A receptor tyrosine protein kinase that was one of the first kinase drug targets. To learn more about VEGFR2 (https://en.wikipedia.org/wiki/VEGF_receptor), check out the UniProt page (https://www.uniprot.org/uniprotkb/P35968/entry). 

* Angiogenesis: Angiogenesis, the formation of new blood vessels from existing vasculature, is a normal physiological event that occurs
during embryonic growth, wound healing and the menstrual cycle. Abnormal regulation of angiogenesis has been implicated in the pathogenesis of several disorders including diabetic retinopathy,1 rheumatoid arthritis,2 age-related macular degeneration,3 and cancer.4,5 As angiogenesis is required for tumor
growth and metastasis, the concept of limiting the growth of a solid tumor by restricting the blood supply has been evaluated in human cancer and has proven successful.

Vascular endothelial growth factor (VEGFa) is a known promoter of angiogenesis, and the increased expression of VEGF has been implicated in tumor growth and metastasis.4,5 VEGF signaling through its receptor tyrosine kinase VEGFR-2 (or KDR, kinase insert domain receptor) promotes several events
required for the formation of new blood vessels, such as endothelial cell survival, proliferation, migration, and vascular permeability. Inhibition of the VEGF signaling pathway has become a valuable approach in the treatment of cancers.


# Hands-on works

Here we used 3B8R, 4ASD, 6GQQ and 2QU5 (Chain A) as our target VEGFR-2 kinases

* 3B8R is in DFG-in conformation (inactive) and 2QU5 is in DFG-out conformation (active)
* DFG motif, which lies in sequence just N-terminal to the activation loop and contains residues numbered 1046 to 1048
* 3B8R is missing the activation loop and what is known as the C-helix is oriented slightly differently compared to 2QU5
* In 3B8R, the DFG motif has the phenylalanine facing in towards the center of the pocket between the N-lobe and C-lobe. In contrast, 2QU5 has the phenylalanine of the DFG motif facing much closer to the surface of the active site. So we can determine that 2QU5 is in the inactive DFG-out state while 3B8R is in the active DFG-in state. 
* DFG-in to DFG-out: This conformational change inhibits the ability of the kinase to bind ATP productively and accommodates the binding of an appropriately substituted inhibitor into an extended lipophilic pocket

## Part-I: Testing the docking model with docking cognate ligands

* 4ASD - Kinase domain with juxtamembrane domain bound to # Sorafenib
* 6GQQ - Kinase domain bound to # AZD3299
* 2QU5 - KInase domain with activation loop missing bound to a # benzimiazole inhibitor

Here we prepared the three cognate ligands, prepared two types of grids (wet and dry) for three traget kinase (total 6 receptor grids to dock)

We evaluated different docking models using the prepared and aligned cognate ligands. You have been provided with grid files for docking that contain some waters from the crystal structures (wet) and grids that do not contain waters (dry) for each of your three VEGFR2 crystal structures

## Comments on docking models

Since both the wet and dry grids produced ligand poses that agree well with the known crystal structure pose, the presence of waters did not result in better docking results for the cognate ligands. Since we know that Glide uses a rigid receptor and would treat waters as part of the receptor, we will continue using only the dry grids to avoid the possibility that the waters in the wet grids may create artificial clashes when screening additional. ligands

## Part-II: Docking with HIT+Decoy series of ligands

In this part of the case study, we have been provided with a hit series of ligands and will use the same dry (that do not contain waters) grid files for docking for each of your three VEGFR2 crystal structures.

* we prepared the Hit Series of ligands using the same LigPrep settings as the cognate ligands
* As we have confirmed that our docking set up works well for known binders, let’s test each receptor grid to see if one gives better enrichment results than the others. we used a pre-generated file of ligands which combines the Hit Series with 160 unique VEGFR2 decoy structures from the DUD-E (http://dude.docking.org/) database. This file has already been prepared using LigPrep and contains 262 structures. we can find the Enrichment Calculator in Tasks by either searching for “enrichment” or navigating to Receptor-Based Virtual Screening > Enrichment Calculator.
* Dock the prepared Hit Series into the dry 2UQ5 grid and repeat for the dry 4ASD and 6GQQ grids (dry)
* Then we compared docking and Glide gscores

This analysis helped us determine which grid you would like to use when docking in LiveDesign in the next part of the Case Study.

## Part-III: Organize SAR Analysis Based on the results from part II

* We login LiveDesin and choose VEGFR2 projects and open Hit series
* We added QikProp (most important of which being the No.of Violations of Lipniski Rule of Five: https://en.wikipedia.org/wiki/Lipinski%27s_rule_of_five)
* Then we added the docking model(s) that you liked best from Part II
* Add Schrödinger Quick Properties to your LiveReport
* Create a scatter plot to visualize the relationship between:
      Molar Refractivity (MR)
      Ki
      Polar Surface Area (PSA)
      AlogP
 * Which of the hit series compounds have the best properties? Add in a Multi-Parameter Profile if you find this easier than using the scatter plot.
 * Then, we used what we have learned to construct a SAR to help with designing new ligands.
 * Open the SAR analysis tool

 * Create the SAR scaffold to the left
 * Create a Scatter Plot where:
      y = R1
      x = R2
      color by AlogP
      size by Ki
 * Analyze the contribution of each R group to inhibition of VEGFR2


 * Create another Scatter Plot where:

      y = R1
      x = R3
      color by PSA
   size by Ki
* Analyze the effect of each R group on the ligands

## Part-IV: Ideation of new Ligands
   
   * we can add new ligand ideas by changing R1, R2, R3
   * And then Dock them to our docking models
         * Compare docking scores
         * Compare  Quick Properties
         * Compare MPP scores
         * Compare interaction
         
 # Key Points From Module 7:
 
 * Structure differences btween crystals of the same receptor were important to consider when plan ning virtual screening
 * Shape-based and structure-based virtual screens resulted in comparable enrichment
 * Hits that are different from a crystal strcuture ligand usually do not return a docking score that correlates with binding affinity
 * Validating screening methods is very important



 
