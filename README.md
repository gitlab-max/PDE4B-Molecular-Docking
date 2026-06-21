# Molecular-Docking

#Tools: Schrödinger AutoDock 

#Deliverables: Docking scores Interaction maps 

#Time: 2–5 days  

#Price: $300–1000

🧬 PDE4B Structure-Based Drug Repurposing Workflow

This project performs computational drug repurposing against PDE4B using FDA-approved compounds.

📌 Workflow Overview
1. Protein Preparation
Retrieve PDE4B crystal structure from RCSB PDB (e.g., 1XMU)
Remove crystallographic water molecules
Add missing hydrogen atoms
Assign bond orders and protonation states
Minimize structure using OPLS force field

3. Ligand Preparation
Download FDA-approved drugs (ZINC / PubChem)
Generate 3D conformers
Ionization state adjustment at pH 7.4
Energy minimization using OPLS4

5. Receptor Grid Generation (Glide)
Define active site around co-crystallized ligand or key residues:
Phe446
His234
Tyr403
Metal site (Mg²⁺ if present)
Grid box centered on catalytic pocket
Default van der Waals scaling: 1.0 / 0.8

7. Molecular Docking (Glide XP)
Precision: Extra Precision (XP)
Flexible ligand docking
Post-docking minimization enabled
Output: docking score + poses

8. Pose Selection & Interaction Analysis
For top-ranked ligands:

Hydrogen bonds
π–π stacking (Phe/Tyr/Trp residues)
Hydrophobic contacts
Metal coordination (Mg²⁺ interactions)

6. MM-GBSA Binding Free Energy
Tool: Prime MM-GBSA
Force field: OPLS4 / OPLS_2005
Solvent model: VSGB2.1

Key output:
ΔG Bind (primary ranking metric)

7. Ranking Strategy
Final ranking based on:

Docking score
MM-GBSA ΔG Bind
Key interactions (H-bond / π–π / metal binding)

A ligand is considered a strong candidate if:

ΔG Bind < -40 kcal/mol (MM-GBSA)
Stable docking pose in catalytic pocket
Persistent interactions with key residues:
Phe446
Tyr403
His234
Metal coordination (Mg²⁺/Zn²⁺) if present
Acceptable ADMET profile

🧪 Top Hits (Example from the study)
| Rank | Ligand       | Glide Score (kcal/mol) | Key interactions                             |
| ---- | ------------ | ---------------------- | -------------------------------------------- |
| 1    | Cilomilast   | **-9.506**             | π–π (Phe414, Phe446), Mg²⁺ coordination      |
| 2    | Perphenazine | **-9.459**             | H-bonds (HIS234, THR145), π–π (Phe446), Mg²⁺ |
| 3    | Haloperidol  | **-8.877**             | π–π (Phe414, Phe446), hydrophobic pocket     |
| 4    | Roflumilast  | **-8.874**             | H-bonds (GLN443, THR345), metal proximity    |

| Ligand       | Glide Score | MM-GBSA ΔG Bind (kcal/mol) | Interpretation                      |
| ------------ | ----------- | -------------------------- | ----------------------------------- |
| Roflumilast  | -8.874      | **-87.47**                 | Strong binder (reference inhibitor) |
| Haloperidol  | -8.877      | **-59.73**                 | Repurposing candidate               |
| Perphenazine | -9.459      | **-48.03**                 | Strong multi-interaction binder     |
| Cilomilast   | -9.506      | **-19.85**                 | Moderate but validated inhibitor    |


📌 Key Insight
Known PDE4 inhibitors (Roflumilast, Cilomilast) validated the docking protocol, while antipsychotic drugs showed potential repurposing signals.

