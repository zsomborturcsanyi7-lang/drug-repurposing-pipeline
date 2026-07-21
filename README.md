# Drug Repurposing Pipeline — AutoDock Vina + ML gyógyszer-újrahasznosítás

**Status:** ⚠️ Prototype — docking pipeline validált, ML proxy betanítva, Kaggle GPU kell a teljes futtatáshoz

Automatizált gyógyszer-újrahasznosítás pipeline: receptor előkészítés → AutoDock Vina docking → ML eredmény kiértékelés. Nilotinib a top találat.

**Megjegyzés:** Ez a repo átfedi a `universal-drug-repurposing` repót. Itt a konkrét AutoDock Vina pipeline van, a másikban a teljes platform.

## ⚠️ THIS PROJECT IS UNFINISHED — FEEL FREE TO CONTINUE IT ⚠️

**Ez a projekt NINCS KÉSZEN. Bárki folytathatja, aki akarja!**
Ezt a projektet Zsombi & Hermes Agent (Nous Research) közösen fejlesztette, de egyik projekt sincs 100%-osan befejezve.

---

## Pipeline lépések

1. **Receptor Preparation** — PDB struktúrák letöltése és tisztítása
2. **Auto Box** — Automatikus kötőhely detektálás
3. **AI Screening** — ML proxy alapú gyors előszűrés
4. **Ligand Preparation** — SMILES → 3D konformáció → PDBQT
5. **Parallel Docking** — Párhuzamosított AutoDock Vina futtatás
6. **Result Evaluation** — Rangsorolás és riport generálás

## Fájlok

| Fájl | Leírás |
|------|--------|
| `src/vina_pipeline.py` | Fő docking pipeline |
| `src/ml_proxy.py` | ML proxy modell |
| `config.yaml` | Konfiguráció |
| `nilotinib_variants.csv` | Nilotinib eredmények |
| `final_validated_results.csv` | Validált eredmények |

## Fejlesztő
Zsombi & Hermes Agent (Nous Research)
