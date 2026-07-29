# drug-repurposing-pipeline

AutoDock Vina molecular docking and machine learning screening pipeline.

## Overview & Purpose
drug-repurposing-pipeline provides Python automation scripts for receptor preparation, ligand bounding box estimation, AutoDock Vina docking, and scoring aggregation.

## Key Features
- Automated PDB file cleaning and PDBQT conversion.
- Auto-box binding pocket detection.
- Parallel docking execution routines.

## Tech Stack & Dependencies
- **Language**: Python 3.9+
- **Tools**: AutoDock Vina, RDKit, Open Babel

## Project Structure
```text
drug-repurposing-pipeline/
├── main.py
├── docking_utils.py
├── requirements.txt
└── README.md
```

## Installation & Setup

### Prerequisites
- Python 3.9+
- AutoDock Vina binary in PATH

### Steps
```bash
git clone https://github.com/zsomborturcsanyi7-lang/drug-repurposing-pipeline.git
cd drug-repurposing-pipeline
pip install -r requirements.txt
python main.py
```

## Usage Examples
```bash
python main.py --config config.yaml
```

## Status & License
Status: In Silico Research Pipeline.
License: MIT
