# Universal Drug Repurposing Platform

> **AI-powered virtual screening platform for rapid drug repurposing against any protein target.**
> 
> "From PDB ID to ranked drug candidates in 30 minutes — no programming required."

[![Python](https://img.shields.io/badge/Python-3.12-blue)](https://www.python.org/)
[![RDKit](https://img.shields.io/badge/RDKit-2024-green)](https://www.rdkit.org/)
[![License](https://img.shields.io/badge/License-MIT-yellow)](LICENSE)

---

## 🎯 What This Does

1. **Input:** A protein PDB ID (e.g., `6LU7` for SARS-CoV-2 Mpro) or upload any protein structure
2. **Process:** AI-pre-screens thousands of FDA-approved drugs + generates optimized variants
3. **Output:** Ranked list of candidate drugs with predicted binding affinities

**New virus emerges → find potential treatments in hours, not years.**

---

## ⚡ Quick Start

```bash
# Interactive mode (for doctors/researchers — no coding!)
python hermes_drug.py --interactive

# Command line mode (for developers)
python hermes_drug.py --pdb 6LU7 --depth standard

# Cloud-accelerated mode (Kaggle)
python hermes_drug.py --pdb 6LU7 --cloud
```

---

## 🧪 Results: Nilotinib_Var_17 — A Multi-Target Binder

Discovered through our AI optimization pipeline, **Nilotinib_Var_17** shows exceptional binding across 5 therapeutically relevant protein targets:

| Protein Target | PDB ID | Binding Affinity |
|---------------|--------|-----------------|
| SARS-CoV-2 Mpro (COVID-19) | 6LU7 | **-8.85 kcal/mol** |
| HIV-1 Protease | 1HPV | **-10.09 kcal/mol** |
| EGFR Kinase (Cancer) | 1M17 | **-10.94 kcal/mol** |
| Bcl-2 (Apoptosis) | 4LVT | **-8.06 kcal/mol** |
| COX-2 (Inflammation) | 5KIR | Strong binder |

Nilotinib is an FDA-approved leukemia drug (Tasigna® by Novartis). Our results suggest potential for drug repurposing against viral and oncological targets.

---

## 🏗️ Architecture

```
User Input (PDB ID / Protein)
         │
         ▼
┌────────────────────────────────┐
│  receptor_prep.py              │  Auto-fetch + clean PDB structure
│  auto_box.py                   │  Auto-detect binding pocket
└────────────────────────────────┘
         │
         ▼
┌────────────────────────────────┐
│  screen_ai.py                  │  AI pre-screen (ECFP4 + 200+ features)
│  optimize_lead.py              │  Generate structural variants
└────────────────────────────────┘
         │
         ▼
┌────────────────────────────────┐
│  prep_ligands.py               │  SMILES → 3D PDBQT (OpenBabel)
│  run_parallel_docking.py       │  AutoDock Vina (multi-core)
└────────────────────────────────┘
         │
         ▼
┌────────────────────────────────┐
│  parse_docking_results.py      │  Parse & rank results
│  train_ml_proxy.py             │  Train ML model on docking data
└────────────────────────────────┘
         │
         ▼
    Ranked Drug Candidates
```

---

## 📊 Model Performance

| Model | Metric | Value |
|-------|--------|-------|
| Single-receptor (Mpro) | R² | **0.60** |
| Multi-receptor (5 targets) | R² | **0.63** |
| Prediction error (MAE) | kcal/mol | **±0.43** |
| Ranking accuracy (Spearman) | correlation | **0.62** |
| Training samples | compounds | **313** |
| Receptors covered | proteins | **5** |

---

## 🔬 Methods

- **Virtual Screening:** AutoDock Vina 1.2.7
- **AI Features:** Morgan fingerprints (ECFP4/ECFP6), 200+ RDKit descriptors, drug-likeness scores
- **ML Models:** Random Forest, HistGradientBoosting, ExtraTrees, SVR
- **Docking Box:** Auto-detection (blind, reference ligand, fpocket)
- **Cloud:** Kaggle kernel integration for GPU-accelerated docking

---

## 📦 Installation

```bash
git clone https://github.com/horvatjanos/universal-drug-repurposing.git
cd universal-drug-repurposing
pip install -r requirements.txt
```

**Requirements:**
- Python 3.10+
- RDKit
- OpenBabel (system package)
- AutoDock Vina (included: `vina_1.2.7_win.exe`)

---

## 📁 Project Structure

```
├── hermes_drug.py              Main entry point
├── config.yaml                 Universal configuration
├── receptor_prep.py            PDB fetch & preparation
├── auto_box.py                 Binding pocket detection
├── screen_ai.py                AI screening pipeline
├── optimize_lead.py            Lead optimization
├── prep_ligands.py             SMILES → PDBQT
├── parse_docking_results.py    Result parser
├── train_advanced_model.py     ML training pipeline
├── cloud_runner.py             Kaggle integration
├── vina_1.2.7_win.exe          AutoDock Vina binary
├── vina_affinity_proxy.pkl     Trained ML model
├── receptor/                   Receptor PDBQT files
├── ligands/                    Ligand PDBQT files
├── docking_results/            Docking output logs
└── targets/                    Cached receptor data
```

---

## 🤝 Collaboration

We are seeking academic partners for **in vitro validation** of predicted drug candidates. Institutions with BSL-2+ laboratory capabilities for enzymatic assays or cell-based testing are ideal.

**Contact:** [GitHub Issues](https://github.com/horvatjanos/universal-drug-repurposing/issues)

---

## 📄 License

MIT License — see [LICENSE](LICENSE)

---

*Built with Python, RDKit, AutoDock Vina, and OpenBabel.*
*Datasets from ChEMBL, RCSB PDB, and DrugBank.*
