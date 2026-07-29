# drug-repurposing-pipeline

**Status:** ⚠️ Prototype — docking pipeline validated, ML proxy trained, Kaggle GPU needed for full run

Automated drug repurposing pipeline: receptor prep → AutoDock Vina docking → ML evaluation. Nilotinib is the top hit.

**Note:** This repo overlaps with `universal-drug-repurposing`. This one contains the specific AutoDock Vina pipeline; the other has the full platform.

## ⚠️ THIS PROJECT IS UNFINISHED — FEEL FREE TO CONTINUE IT ⚠️

This project was developed by Zsombi & Hermes Agent (Nous Research).

---

## Contents
| File | Description |
|------|-------------|
| `src/vina_pipeline.py` | Main docking pipeline |
| `src/ml_proxy.py` | ML proxy model |
| `config.yaml` | Configuration |
| `nilotinib_variants.csv` | Nilotinib results |
| `final_validated_results.csv` | Validated results |

## Developer
Zsombi & Hermes Agent (Nous Research)
