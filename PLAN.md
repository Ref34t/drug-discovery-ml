# 90-Day Drug Discovery ML Plan

## Identity
> "I build AI systems for molecular screening, property prediction, and drug evaluation."

---

## Ground Rules
- Build every week — no exceptions
- One GitHub commit minimum per day during build weeks
- Every 2 weeks — one LinkedIn post about what you built
- Never spend more than 2 days stuck — move forward, come back later
- Every Friday — 15 min weekly review (write review.md)
- Every week from Week 6 — read one paper (30 min max)

## Failure Protocol
If stuck > 2 days on anything:
1. Simplify the model (RF before GNN, always)
2. Reduce dataset size (100 molecules not 10k)
3. Post the error on Stack Overflow or ask
4. Move forward — come back later

## Time Budget (18h/week)
| Activity | Hours |
|----------|-------|
| Building | 9h |
| Learning | 5h |
| Debugging | 3h |
| Writing/posting | 1h |

## Minimum Viable Week
Life happens. If you only have 8 hours:
- Skip the polish, skip the LinkedIn post
- Just build the core notebook or function
- Commit it — never fully skip a week

---

# Month 1 — Molecules as Data
**Objective:** Stop seeing molecules as chemistry. Start seeing them as data structures.

---

## Week 1 — Environment + Biology Basics
**Outcome:** Your machine is ready. You understand the domain you're entering.

### Setup
```bash
uv init drug-discovery-ml
cd drug-discovery-ml
uv add rdkit pandas scikit-learn jupyter matplotlib
```

### Biology (5h this week only)
- Read: Hallmarks of Cancer — Hanahan & Weinberg (summary version)
- Browse ChEMBL — understand what bioassay data looks like
- Browse TCGA — understand what genomic data looks like
- Watch: "What is a SMILES string" (20 min YouTube)

### Minimum Viable Week
Just get RDKit installed and load one molecule.

**Status:** [x] Complete

---

## Week 2 — RDKit Foundations
**Outcome:** You can load, visualize, and manipulate molecules in code.

### Deliverable
```
✅ rdkit_basics.ipynb
   - Loads ESOL dataset
   - Visualizes 10 molecules
   - Prints properties for each
   - Handles 3 invalid SMILES examples
```

### Minimum Viable Week
Load ESOL dataset and print atom properties for 5 molecules.

**Status:** [ ] Complete

---

## Week 3 — Fingerprints + Molecular Similarity
**Outcome:** You understand how molecules become vectors.

### Deliverable
```
✅ Function: find_similar(query_smiles, dataset, top_n=5)
   - Returns top N most similar molecules
   - Includes similarity scores
   - Deployed as a script
```

### Minimum Viable Week
Compute Morgan fingerprints for 10 molecules and print Tanimoto similarity.

**Status:** [ ] Complete

---

## Week 4 — Drug-likeness + Descriptors
**Outcome:** You can programmatically evaluate whether a molecule is drug-like.

### Deliverable
```
✅ Function: evaluate_druglikeness(smiles)
   Returns: mw, logp, hbd, hba, lipinski, veber, score
```

### Minimum Viable Week
Implement Lipinski Rule of 5 for one molecule.

**Status:** [ ] Complete

---

## Week 5 — Project 1: Solubility Predictor
**Outcome:** First end-to-end ML pipeline on real molecular data.

### Metric Target
```
RMSE < 1.0 log mol/L on test set
R²   > 0.70
```

### Deliverable
```
✅ GitHub repo: solubility-predictor
   - CLI: python predict_solubility.py --smiles "CCO"
   - README with: problem, data, model, RMSE + R² results
   - LinkedIn post: "I built my first molecular ML model"
```

### Explain It (write this before posting)
> "I built a solubility predictor using RDKit descriptors and Random Forest.
> Solubility is critical in drug development — a drug that won't dissolve
> can't reach its target. I trained on the ESOL dataset (1128 compounds)
> and achieved RMSE of X. The model runs as a CLI tool."

### Minimum Viable Week
Trained model in a notebook with RMSE reported.

**Status:** [ ] Complete

---

# Month 2 — Structure-Aware ML
**Objective:** Learn why molecular graphs outperform flat feature vectors.

### Papers (one per week from here)
```
Week 6:  "Neural Message Passing for Quantum Chemistry" — Gilmer 2017
Week 7:  "Molecular Graph Convolutions" — Duvenaud 2015
Week 8:  "Analyzing Learned Molecular Representations" — Yang 2019
Week 9:  Any paper on virtual screening or molecular similarity
```

---

## Week 6 — Molecules as Graphs
**Outcome:** Convert any molecule into a graph for GNN input.

### Paper This Week
"Neural Message Passing for Quantum Chemistry" — Gilmer 2017 (30 min)

### Deliverable
```
✅ molecule_to_graph.ipynb
   - 5 molecules converted to PyG Data objects
   - Node + edge feature shapes printed
   - Side-by-side visualization: molecule image vs graph
```

### Minimum Viable Week
Convert one molecule to a PyG Data object and print its features.

**Status:** [ ] Complete

---

## Week 7 — Build Your First GNN
**Outcome:** Working GNN that predicts molecular properties.

### Paper This Week
"Molecular Graph Convolutions" — Duvenaud 2015 (30 min)

### Metric Target
```
Compare RMSE: Random Forest (Week 5) vs GNN
Write 3 sentences explaining why results differ
```

### Deliverable
```
✅ gnn_solubility.ipynb
   - 3-layer GCN → global mean pooling → MLP head
   - RMSE: Random Forest vs GNN side by side
   - 3-sentence explanation of the difference
```

### Minimum Viable Week
GNN trains without errors and produces a prediction.

**Status:** [ ] Complete

---

## Week 8 — Toxicity Predictor (Tox21)
**Outcome:** Multi-task classifier on real safety-critical biomedical data.

### Paper This Week
"Analyzing Learned Molecular Representations" — Yang 2019 (30 min)

### Metric Target
```
ROC-AUC > 0.75 average across all 12 Tox21 endpoints
```

### Deliverable
```
✅ GitHub repo: toxicity-predictor
   - Multi-task GNN
   - ROC-AUC reported per endpoint + average
   - FastAPI + Docker
   - LinkedIn post: "Why toxicity prediction is a graph problem"
```

### Explain It (write this before posting)
> "I built a multi-task GNN to predict 12 toxicity endpoints
> simultaneously using the Tox21 dataset. Toxicity prediction is critical
> in drug discovery — most drug candidates fail due to safety issues.
> The model achieves ROC-AUC of X averaged across all endpoints."

### Minimum Viable Week
Single-task GNN on one Tox21 endpoint with ROC-AUC reported.

**Status:** [ ] Complete

---

## Week 9 — Molecular Search Engine
**Outcome:** Similarity-based retrieval over a large molecular database.

### Paper This Week
Any paper on virtual screening (search: "virtual screening review 2020")

### Metric Target
```
Search time < 500ms for 250k molecules
```

### Deliverable
```
✅ molecular-search-engine/
   - Indexed 250k ZINC molecules
   - FastAPI /similar endpoint
   - Search time benchmarked and logged
```

### Minimum Viable Week
find_similar() function working on ESOL dataset (1128 molecules).

**Status:** [ ] Complete

---

# Month 3 — Systems Thinking
**Objective:** Stop building models. Build systems.

### Papers (one per week)
```
Week 10: "Genomics of Drug Sensitivity in Cancer" — Yang 2012
Week 11: Any paper on protein-ligand interaction
Week 12: "A Deep Learning Approach to Antibiotic Discovery" — Stokes 2020
Week 13: Any paper on ML model deployment in drug discovery
```

---

## Week 10 — Cancer Drug Response (GDSC)
**Outcome:** First cancer-specific ML model.

### Paper This Week
"Genomics of Drug Sensitivity in Cancer" — Yang 2012 (30 min)

### Metric Target
```
R² > 0.60 on held-out cell lines
Report performance separately for: breast, lung, colon cancer
```

### Deliverable
```
✅ cancer_drug_response.ipynb
   - Model trained on GDSC
   - R² reported per cancer type
   - SHAP plot: top 10 genomic features driving predictions
   - LinkedIn post: "How I used GDSC data to predict cancer drug response"
```

### Explain It (write this before posting)
> "I trained a model to predict how cancer cell lines respond to drugs
> using the GDSC dataset. The model takes genomic features (mutations,
> gene expression) + drug structure as input and predicts IC50 values.
> SHAP analysis revealed that X gene is the strongest predictor for
> breast cancer drug response."

### Minimum Viable Week
Model trained on GDSC with R² reported — no SHAP required.

**Status:** [ ] Complete

---

## Week 11 — Protein-Ligand Interaction Basics
**Outcome:** Understand what a binding pocket is and visualize protein-ligand structure.

### Paper This Week
Any paper on protein-ligand binding or docking (search: "protein ligand interaction ML review")

### Why This Replaced Molecule Generator
Protein-ligand interaction is directly relevant to Relay Therapeutics and
Exscientia. It connects your Week 10 cancer work to structural biology —
a gap most ML engineers have.

### Deliverable
```
✅ protein_ligand_basics.ipynb
   - Download one protein structure from PDB (e.g. BCR-ABL: PDB 1IEP)
   - Visualize with py3Dmol
   - Identify the binding pocket
   - Load Imatinib (your Day 2 molecule) as the ligand
   - Show protein + ligand together
```

### Minimum Viable Week
Download PDB structure and visualize it in the notebook.

**Status:** [ ] Complete

---

## Week 12 — Core Evaluation Engine
**Outcome:** Unified pipeline that scores any molecule across all dimensions.

### Paper This Week
"A Deep Learning Approach to Antibiotic Discovery" — Stokes 2020 (30 min)
This is a landmark paper — a GNN discovered a new antibiotic. Read it carefully.

### Metric Target
```
Pipeline runs end-to-end in < 2 seconds per molecule
```

### Pipeline
```
SMILES → Validation → Drug-likeness → Solubility → Toxicity → Similarity → Cancer score → Report
```

### Deliverable
```
✅ Function: evaluate_molecule(smiles)
   - Returns structured JSON with all scores
   - Latency logged and reported
   - Runs in < 2 seconds
```

### Minimum Viable Week
Pipeline connects at least 3 models (druglikeness + solubility + toxicity).

**Status:** [ ] Complete

---

## Week 13 — Production API
**Outcome:** Everything deployed. Accessible via URL.

### Endpoints
```
POST /evaluate   → full molecule evaluation
POST /similar    → find similar molecules
GET  /health     → uptime check
```

### Deliverable
```
✅ Live URL on HuggingFace Spaces
✅ Auto-generated FastAPI docs (/docs)
✅ Dockerized
✅ README with architecture diagram
```

### Minimum Viable Week
FastAPI running locally with /evaluate endpoint working.

**Status:** [ ] Complete

---

## Week 14 — Capstone: AI Drug Discovery Assistant
**Outcome:** The project that gets you interviews.

### Pitch
> "Give me a molecule like Imatinib but less toxic and more soluble"

### Metric Target
```
End-to-end latency < 10 seconds for 50 candidates
All generated candidates pass RDKit validity + Lipinski
```

### System Flow
```
User input (SMILES)
      ↓
Generate 50 candidates (SMILES RNN)
      ↓
evaluate_molecule() on all 50
      ↓
Filter: Lipinski + validity
      ↓
Cancer relevance score (GDSC model)
      ↓
Rank + return top 5 with full report
```

### Deliverable
```
✅ GitHub repo: ai-drug-discovery-assistant
   - Live demo (HuggingFace Spaces)
   - 3-minute demo video posted on LinkedIn
   - Architecture diagram in README
   - Honest limitations section
   - LinkedIn post: "I built an AI drug discovery assistant in 90 days"
```

### Explain It (write this before posting)
> "I built an end-to-end AI system that takes a seed molecule and returns
> optimized candidates ranked by drug-likeness, predicted solubility,
> toxicity, and cancer drug response. The system generates 50 candidates
> in under 10 seconds. Built with RDKit, PyTorch, GNNs, and FastAPI."

**Status:** [ ] Complete

---

# Portfolio Summary

| Project | Key Metric | Skills | Relevant To |
|---------|-----------|--------|-------------|
| Solubility Predictor | RMSE < 1.0 | RDKit, scikit-learn | All companies |
| Toxicity Predictor | ROC-AUC > 0.75 | GNNs, multi-task, Docker | Tempus, Exscientia |
| Molecular Search Engine | < 500ms search | Retrieval, FastAPI | Recursion, Foundation Medicine |
| Cancer Drug Response | R² > 0.60 | GDSC, genomics, SHAP | Tempus, AstraZeneca |
| Drug Discovery Assistant | < 10s end-to-end | Full system | All companies |

---

# LinkedIn Posts Schedule

| Week | Topic |
|------|-------|
| 5 | "I built my first molecular ML model — here's what I learned" |
| 8 | "Why toxicity prediction is a graph problem" |
| 10 | "How I used GDSC data to predict cancer drug response" |
| 14 | "I built an AI drug discovery assistant in 90 days — here's the demo" |

---

# Weekly Review Template
Save as `week{n}/review.md` every Friday (15 min):

```
## Week N Review

### What I built
-

### What slowed me down
-

### What I do differently next week
-

### Metric achieved
-
```
