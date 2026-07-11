# AI Drug Repurposing — Universal Drug Repurposing Platform

**Status:** ⚠️ Prototype — docking pipeline validated, ML proxy trained, needs Kaggle GPU for full run


**An AutoDock Vina + ML-based drug discovery pipeline capable of screening any protein against any drug library with a single command.**

## ⚠️ THIS PROJECT IS UNFINISHED — FEEL FREE TO CONTINUE IT ⚠️

**Ez a projekt NINCS KÉSZEN. Bárki folytathatja, aki akarja!**
Ezt a projektet Zsombi & Hermes Agent (Nous Research) közösen fejlesztette, de egyik projekt sincs 100%-osan befejezve. Ha tetszik az ötlet és tovább fejlesztenéd, nyugodtan fork-old, folytasd, és csinálj belőle valami nagyszerűt!

---


## 🧪 Description

This platform is a complete, automated drug repurposing system that performs the following steps:

1. **Receptor Preparation** — Download and clean PDB structures
2. **Auto Box** — Automatic binding pocket detection
3. **AI Screening** — ML proxy-based fast pre-screening
4. **Ligand Preparation** — SMILES → 3D conformation → PDBQT
5. **Parallel Docking** — Parallelized AutoDock Vina execution
6. **Result Evaluation** — Ranking and report generation
7. **Lead Optimization** — Generate improved variants (--deep mode)

### Results

- **Top hit:** Nilotinib — -8.30 kcal/mol binding energy
- Target proteins: 6LU7 (SARS-CoV-2 main protease), 5KIR, 4LVT, 1M17, 1HPV
- ADMET screening and validation completed

## 📁 File Structure

```
AI Drug Repurposing/
├── src/
│   ├── hermes_drug.py          # Main entry point — universal pipeline
│   ├── pose_stability.py       # Pose stability analysis
│   └── admet_prediction.py     # ADMET (absorption, toxicity) prediction
├── cloud_results/              # Cloud-run docking results
│   └── 6LU7/                   # SARS-CoV-2 main protease target
│       ├── run_parallel_docking.py
│       ├── parse_docking_results.py
│       ├── receptor_prep.py
│       ├── prep_ligands.py
│       ├── optimize_lead.py
│       ├── mutate_lead.py
│       ├── nilotinib_variants.csv
│       └── targets/            # Target protein structures
│           ├── 6LU7/
│           ├── 5KIR/
│           ├── 4LVT/
│           ├── 1M17/
│           └── 1HPV/
├── github_repo/                # Public GitHub release materials
│   ├── README.md
│   ├── USAGE.md
│   ├── WHITEPAPER.md
│   └── CHANGELOG.md
├── final_validated_results.csv # Final validated results
├── admet_screened_results.csv  # ADMET screened results
└── merged_results.csv          # Aggregated docking results
```

## 🚀 Usage

### Basic screening against a protein

```bash
python src/hermes_drug.py --pdb 6LU7
```

### Deep mode (with lead optimization)

```bash
python src/hermes_drug.py --pdb 6LU7 --deep
```

### Cloud mode (run on remote server)

```bash
python src/hermes_drug.py --pdb 6LU7 --cloud
```

### Interactive mode

```bash
python src/hermes_drug.py --interactive
```

### Using a custom drug library

```bash
python src/hermes_drug.py --pdb 6LU7 --drug-library custom_drugs.csv
```

### Listing available targets

```bash
python src/hermes_drug.py --list-targets
```

## 📦 Dependencies

- **Python 3.8+**
- **AutoDock Vina** (external program, must be in PATH)
- **Open Babel** (for ligand conversion)
- Python packages:
  - `numpy`, `pandas`
  - `scikit-learn` (ML proxy)
  - `pyyaml`
  - `rdkit` (chemical structure handling)
  - `requests` (PDB download)

Installation:

```bash
pip install numpy pandas scikit-learn pyyaml rdkit requests
# AutoDock Vina and Open Babel must be installed separately!
```

## 📊 Pipeline Overview

```
PDB download → Receptor cleanup → Binding pocket detection
    → ML proxy fast screening → Ligand 3D generation
    → Parallel AutoDock Vina docking → Result ranking
    → (optional) Lead mutation and optimization
    → ADMET prediction → Final report
```

## ⚠️ Warning

This platform is intended for **research purposes**. Docking results are *in silico* predictions that must be followed by experimental validation. Do not use for medical decisions without laboratory confirmation.

## Author
Zsombi & Hermes Agent (Nous Research)
