<<<<<<< HEAD
# Therapy Response AI Prototype

This repository provides a research prototype to predict whether a patient will respond to chemotherapy or immunotherapy using pre-treatment multimodal data (e.g., medical images + genomics + metabolic/clinical parameters).

Important notices:
- This project uses ONLY synthetic or openly accessible, de-identified data for examples and testing.
- No personal identifiers (PII/PHI) are included in this repository.
- The prototype is for research and educational purposes only and is NOT a medical device or clinical decision support tool.

## Repository Structure
therapy-response-ai/
├── data/
│ ├── synthetic_data_generator.py # Synthetic dataset generator
│ ├── example_dataset.csv # Small example dataset
├── models/
│ ├── multimodal_model.py # Image + genomics + clinical fusion model
├── training/
│ ├── train.py # Model training
│ ├── evaluate.py # Validation and ROC/F1 metrics
├── README.md
├── LICENSE
└── requirements.txt


## Quick Start

1) Create environment and install dependencies:

```bash
python -m venv .venv
# Windows PowerShell
. .venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

2) Generate a synthetic dataset (images + tabular features + labels):

```bash
python data/synthetic_data_generator.py --num-samples 500 --image-size 64 --out-dir data
```

This creates PNG images under `data/images/` and a CSV at `data/example_dataset.csv` with columns:
- image_path: relative path to the image file
- genomics_*, metabolic_*, clinical_*: simulated tabular features
- label: binary response (0/1)

3) Train the multimodal model:

```bash
python training/train.py ^
  --csv-path data/example_dataset.csv ^
  --image-size 64 ^
  --epochs 10 ^
  --batch-size 32 ^
  --lr 1e-3 ^
  --out-dir runs/basic
```

4) Evaluate and compute ROC AUC / F1:

```bash
python training/evaluate.py ^
  --csv-path data/example_dataset.csv ^
  --checkpoint runs/basic/best_model.pt ^
  --image-size 64 ^
  --out-dir runs/basic
```

This will print metrics and save a ROC curve to `runs/basic/roc_curve.png`.

## Data, Privacy, and Ethics
- Only synthetic or publicly available, de-identified datasets are used.
- No personal data is stored in this repository.
- This code is a prototype and should not be used for clinical decision making.

## Notes
- The model is intentionally small and designed for demonstration.
- Extend features and preprocessing as needed for real research.


=======
# Therapy Response AI (Prototype)
 
This repository provides a research prototype to predict whether a patient will respond to chemotherapy or immunotherapy using pre-treatment multimodal data (image + genomics + metabolic/clinical).
 
Important notices: 
- Synthetic or open, de-identified data only. 
- No PII/PHI in this repo. 
- Research/education prototype; not a medical device.
 
Quick Start (Windows): 
1) python -m venv .venv && . .venv\Scripts\Activate.ps1 && pip install -r requirements.txt 
2) python data\synthetic_data_generator.py --num-samples 500 --image-size 64 --out-dir data 
3) python training\train.py --csv-path data\example_dataset.csv --image-size 64 --epochs 10 --batch-size 32 --lr 1e-3 --out-dir runs\basic 
4) python training\evaluate.py --csv-path data\example_dataset.csv --checkpoint runs\basic\best_model.pt --image-size 64 --out-dir runs\basic
 
Files: 
- data/synthetic_data_generator.py: creates images and example_dataset.csv 
- models/multimodal_model.py: CNN image encoder + MLP tabular encoder + fusion 
- training/train.py: training loop, metrics, checkpoint 
- training/evaluate.py: ROC AUC, F1, ROC plot (runs\basic\roc_curve.png) 
 
Privacy and Ethics: 
- Only synthetic or public, de-identified data. 
- Do not use for clinical decision making.
>>>>>>> 80b1677 ( docs: complete README with setup and usage)
