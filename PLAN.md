# 90-Day Drug Discovery ML Plan

## Identity
> "I build AI systems for molecular screening, property prediction, and drug evaluation."

---

## Ground Rules
- Build every week — no exceptions
- One GitHub commit minimum per day during build weeks
- Every 2 weeks — one LinkedIn post about what you built
- Never spend more than 2 days stuck — move forward, come back later

## Time Budget (18h/week)
| Activity | Hours |
|----------|-------|
| Building | 9h |
| Learning | 5h |
| Debugging | 3h |
| Writing/posting | 1h |

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

**Status:** [ ] Complete

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

**Status:** [ ] Complete

---

## Week 4 — Drug-likeness + Descriptors
**Outcome:** You can programmatically evaluate whether a molecule is drug-like.

### Deliverable
```
✅ Function: evaluate_druglikeness(smiles)
   Returns: mw, logp, hbd, hba, lipinski, veber, score
```

**Status:** [ ] Complete

---

## Week 5 — Project 1: Solubility Predictor
**Outcome:** First end-to-end ML pipeline on real molecular data.

### Deliverable
```
✅ GitHub repo: solubility-predictor
   - CLI: python predict_solubility.py --smiles "CCO"
   - Clean README
   - LinkedIn post
```

**Status:** [ ] Complete

---

# Month 2 — Structure-Aware ML
**Objective:** Learn why molecular graphs outperform flat feature vectors.

---

## Week 6 — Molecules as Graphs
**Outcome:** Convert any molecule into a graph for GNN input.

### Deliverable
```
✅ molecule_to_graph.ipynb
   - 5 molecules converted to PyG Data objects
   - Side-by-side visualization
```

**Status:** [ ] Complete

---

## Week 7 — Build Your First GNN
**Outcome:** Working GNN that predicts molecular properties.

### Deliverable
```
✅ gnn_solubility.ipynb
   - GNN trained on ESOL
   - RMSE comparison: Random Forest vs GNN
```

**Status:** [ ] Complete

---

## Week 8 — Toxicity Predictor (Tox21)
**Outcome:** Multi-task classifier on real safety-critical biomedical data.

### Deliverable
```
✅ GitHub repo: toxicity-predictor
   - Multi-task GNN
   - ROC-AUC per endpoint
   - FastAPI + Docker
   - LinkedIn post
```

**Status:** [ ] Complete

---

## Week 9 — Molecular Search Engine
**Outcome:** Similarity-based retrieval over a large molecular database.

### Deliverable
```
✅ molecular-search-engine/
   - Indexed 250k ZINC molecules
   - FastAPI /similar endpoint
   - < 500ms search time
```

**Status:** [ ] Complete

---

# Month 3 — Systems Thinking
**Objective:** Stop building models. Build systems.

---

## Week 10 — Cancer Drug Response (GDSC)
**Outcome:** First cancer-specific ML model.

### Deliverable
```
✅ cancer_drug_response.ipynb
   - Model trained on GDSC
   - Performance by cancer type
   - SHAP plot: top 10 genomic features
```

**Status:** [ ] Complete

---

## Week 11 — Molecule Generator
**Outcome:** System that generates new candidate molecules.

### Deliverable
```
✅ Function: generate_molecules(n=10, seed_smiles=None)
   - Returns n valid SMILES strings
   - All pass RDKit validity + Lipinski Rule of 5
```

**Status:** [ ] Complete

---

## Week 12 — Core Evaluation Engine
**Outcome:** Unified pipeline that scores any molecule across all dimensions.

### Pipeline
```
SMILES → Validation → Drug-likeness → Solubility → Toxicity → Similarity → Cancer score → Report
```

### Deliverable
```
✅ Function: evaluate_molecule(smiles)
   - Returns structured JSON
   - Runs in < 2 seconds
```

**Status:** [ ] Complete

---

## Week 13 — Production API
**Outcome:** Everything deployed. Accessible via URL.

### Endpoints
```
POST /evaluate
POST /generate
GET  /similar
GET  /health
```

### Deliverable
```
✅ Live URL on HuggingFace Spaces
✅ Auto-generated API docs
✅ Dockerized
```

**Status:** [ ] Complete

---

## Week 14 — Capstone: AI Drug Discovery Assistant
**Outcome:** The project that gets you interviews.

### Pitch
> "Give me a molecule like Imatinib but less toxic and more soluble"

### Deliverable
```
✅ GitHub repo: ai-drug-discovery-assistant
   - Live demo
   - 3-minute demo video
   - Architecture diagram
   - LinkedIn post
```

**Status:** [ ] Complete

---

# Portfolio Summary

| Project | Skills | Relevant To |
|---------|--------|-------------|
| Solubility Predictor | RDKit, scikit-learn, pipelines | All companies |
| Toxicity Predictor | GNNs, multi-task, Docker | Tempus, Exscientia |
| Molecular Search Engine | Retrieval, FastAPI | Recursion, Foundation Medicine |
| Cancer Drug Response | GDSC, genomics, SHAP | Tempus, AstraZeneca |
| Drug Discovery Assistant | Full system | All companies |

---

# LinkedIn Posts Schedule

| Week | Topic |
|------|-------|
| 5 | "I built my first molecular ML model — here's what I learned" |
| 8 | "Why toxicity prediction is a graph problem" |
| 10 | "How I used GDSC data to predict cancer drug response" |
| 14 | "I built an AI drug discovery assistant in 90 days — here's the demo" |
