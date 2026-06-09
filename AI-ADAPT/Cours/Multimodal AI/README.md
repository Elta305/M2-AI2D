# Fungi Multimodal Binary Classification

This repository contains a small pipeline to train unimodal and multimodal (early & late fusion) binary classifiers to distinguish `Agaricus arvensis` vs `Cyanosporus caesius` using the provided dataset.

Files:
- `multimodal_pipeline.py`: script that loads CSVs, extracts image color-histogram features, TF-IDF text features, tabular geodata features, trains classifiers, and evaluates.
- `requirements.txt`: minimal dependencies. See note about optional DL backends below.

Quick start (from workspace root):

1. Create a virtualenv and install requirements:

```bash
python -m venv .venv
# Windows PowerShell
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

2. Run the pipeline (paths are relative to workspace root):

```bash
python multimodal_pipeline.py --train "Fungi binary data/train" --test "Fungi binary data/test" --out models
```

Optional: use pretrained image embeddings (ResNet50) instead of handcrafted color histograms. This requires either `torch` (torchvision) or `tensorflow` to be installed. Use the `--use-pretrained` flag:

```bash
python multimodal_pipeline.py --use-pretrained --train "Fungi binary data/train" --test "Fungi binary data/test" --out models
```

Outputs will be placed in the `models/` folder: trained models, preprocessor objects, and a `results.joblib` summary.
