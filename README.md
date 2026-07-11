# AI Drug Repurposing — Univerzális Gyógyszer-újrapozicionáló Platform

**AutoDock Vina + ML alapú gyógyszerkutatási pipeline, amely egyetlen paranccsal képes bármely fehérjét bármely gyógyszerkönyvtárral szemben szűrni.**

## 🧪 Leírás

Ez a platform egy teljes körű, automatizált gyógyszer-újrapozicionálási (drug repurposing) rendszer, amely a következő lépéseket végzi el:

1. **Receptor előkészítés** — PDB struktúra letöltése és tisztítása
2. **Auto Box** — Kötőzseb automatikus detektálása
3. **AI szűrés** — ML proxy gyors előszűrés
4. **Ligandum előkészítés** — SMILES → 3D konformáció → PDBQT
5. **Parallel dokkolás** — AutoDock Vina párhuzamos futtatása
6. **Eredmények kiértékelése** — Rangsorolás és riport generálás
7. **Lead optimalizálás** — Jobb variánsok generálása (--deep mód)

### Eredmények

- **Top találat:** Nilotinib — -8.30 kcal/mol kötési energia
- Célfehérjék: 6LU7 (SARS-CoV-2 fő proteáz), 5KIR, 4LVT, 1M17, 1HPV
- ADMET szűrés és validálás elvégezve

## 📁 Fájlszerkezet

```
AI Drug Repurposing/
├── src/
│   ├── hermes_drug.py          # Fő belépési pont — univerzális pipeline
│   ├── pose_stability.py       # Póz stabilitás elemzés
│   └── admet_prediction.py     # ADMET (felszívódás, toxicitás) predikció
├── cloud_results/              # Felhőben futtatott dokkolás eredményei
│   └── 6LU7/                   # SARS-CoV-2 fő proteáz target
│       ├── run_parallel_docking.py
│       ├── parse_docking_results.py
│       ├── receptor_prep.py
│       ├── prep_ligands.py
│       ├── optimize_lead.py
│       ├── mutate_lead.py
│       ├── nilotinib_variants.csv
│       └── targets/            # Célfehérje struktúrák
│           ├── 6LU7/
│           ├── 5KIR/
│           ├── 4LVT/
│           ├── 1M17/
│           └── 1HPV/
├── github_repo/                # Publikus GitHub release anyagok
│   ├── README.md
│   ├── USAGE.md
│   ├── WHITEPAPER.md
│   └── CHANGELOG.md
├── final_validated_results.csv # Végleges validált eredmények
├── admet_screened_results.csv  # ADMET szűrt eredmények
└── merged_results.csv          # Összesített dokkolási eredmények
```

## 🚀 Használat

### Alap szűrés egy fehérjére

```bash
python src/hermes_drug.py --pdb 6LU7
```

### Mély mód (lead optimalizálással)

```bash
python src/hermes_drug.py --pdb 6LU7 --deep
```

### Felhő mód (távoli szerveren futtatás)

```bash
python src/hermes_drug.py --pdb 6LU7 --cloud
```

### Interaktív mód

```bash
python src/hermes_drug.py --interactive
```

### Egyedi gyógyszerkönyvtár használata

```bash
python src/hermes_drug.py --pdb 6LU7 --drug-library custom_drugs.csv
```

### Elérhető target-ek listázása

```bash
python src/hermes_drug.py --list-targets
```

## 📦 Függőségek

- **Python 3.8+**
- **AutoDock Vina** (külső program, PATH-ban kell lennie)
- **Open Babel** (ligandum konverzióhoz)
- Python csomagok:
  - `numpy`, `pandas`
  - `scikit-learn` (ML proxy)
  - `pyyaml`
  - `rdkit` (kémiai szerkezetek kezelése)
  - `requests` (PDB letöltés)

Telepítés:

```bash
pip install numpy pandas scikit-learn pyyaml rdkit requests
# AutoDock Vina és Open Babel külön telepítendő!
```

## 📊 Pipeline áttekintése

```
PDB letöltés → Receptor tisztítás → Kötőzseb detektálás
    → ML proxy gyorsszűrés → Ligandum 3D generálás
    → Parallel AutoDock Vina dokkolás → Eredmény rangsorolás
    → (opcionális) Lead mutáció és optimalizálás
    → ADMET predikció → Végső riport
```

## ⚠️ Figyelmeztetés

Ez a platform **kutatási célokra** készült. A dokkolási eredmények *in silico* predikciók, melyeket kísérleti validálásnak kell követnie. Ne használd orvosi döntések meghozatalára laboratóriumi megerősítés nélkül.
