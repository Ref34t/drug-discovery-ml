# Week 1 Day 2 Notes

## Track 1 — RDKit Molecules

### Molecule Object
- `Chem.MolFromSmiles(smiles)` → returns a `Mol` object
- If invalid SMILES → returns `None`
- RDKit ignores hydrogens by default (only heavy atoms)

### Atoms
- `mol.GetAtoms()` → iterate over all atoms
- `atom.GetIdx()` → atom's index number
- `atom.GetSymbol()` → element symbol (C, O, N...)
- `atom.GetIsAromatic()` → True if part of aromatic ring (benzene)
- `atom.GetDegree()` → number of bonds this atom has
  - degree 1 = end of chain
  - degree 2 = middle of chain
  - degree 3 = branching point

### Bonds
- `mol.GetBonds()` → iterate over all bonds
- `bond.GetBondTypeAsDouble()` → bond type as number
  - 1.0 = single bond
  - 2.0 = double bond
  - 1.5 = aromatic (benzene ring)
- `bond.IsInRing()` → True if bond is part of a ring

### Aspirin (CC(=O)Oc1ccccc1C(=O)O)
- 13 heavy atoms (9 carbons + 4 oxygens)
- 13 bonds
- Atoms 4-9 are aromatic (benzene ring)
- Two C=O double bonds (carbonyl groups)

### ESOL Dataset
- 1128 molecules, 10 columns
- Target column: `measured log solubility in mols per litre`
- Lower value = less soluble (harder to dissolve in water)
- 100% valid SMILES — no cleaning needed
- This is the Week 5 project dataset

---

## Track 2 — Biology

### SMILES Notation
- CC = ethane (two carbons)
- c1ccccc1 = benzene (lowercase = aromatic)
- CC(=O)O = acetic acid (branch in parentheses)
- = means double bond

### Hallmarks of Cancer
Six rules every cancer cell breaks:

1. **Sustaining Growth Signals** — generates its own growth signals, no permission needed
2. **Evading Growth Suppressors** — disables tumor suppressors like TP53 (mutated in 50% of cancers)
3. **Resisting Cell Death** — disables apoptosis (self-destruct mechanism)
4. **Enabling Replicative Immortality** — activates telomerase, divides forever
5. **Inducing Angiogenesis** — grows its own blood vessels to feed the tumor
6. **Activating Invasion and Metastasis** — escapes, travels through blood, colonizes organs (kills most patients)

Each hallmark = a drug target = a dataset to model

### ChEMBL — Imatinib
- ChEMBL is a bioactivity database (not ChEBI)
- IC50 = concentration needed to kill 50% of cancer cells (lower = more potent)
- Imatinib IC50 on random target = 1181 nM (weak)
- Imatinib IC50 on BCR-ABL = 115 nM (potent — this is its real target)
- Selectivity = hits target hard, ignores everything else
- Off-target activity = side effects

### Key Genes to Remember
- TP53 — tumor suppressor, mutated in 50% of cancers
- BCR-ABL — Imatinib's primary target (chronic myeloid leukemia)
- KRAS, EGFR — growth signal targets (hallmark 1)
- BCL-2 — apoptosis target (hallmark 3)
