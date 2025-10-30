

**Repository:** `Harsh-ryUk/Fungi-Computer-Vision`  
**Competition referenced:** [FungiCLEF25 @ CVPR-FGVC & LifeCLEF](https://www.kaggle.com/competitions/lifeclef-2025-fungiclef)

---

## Project Overview

This repository contains the code and experiments for the **FungiCLEF25 @ CVPR-FGVC / LifeCLEF** Kaggle competition.  
The main objective is automated identification of fungal species from images and metadata using advanced computer vision and ML techniques.

The dataset comprises thousands of annotated macro photos of fungi from global community sources, along with associated ecological and location metadata.

---

## Repository Structure

```
.
├── data/                   # (not included) place dataset files here or mount Kaggle data
├── notebooks/              # EDA, model exploration, visualizations
├── src/                    # Training scripts, models, data pipelines
├── models/                 # Saved model checkpoints
├── submissions/            # Generated submission CSVs
├── requirements.txt        # Python dependencies
├── config.py               # Project configuration (example)
└── README.md               # This file
```

## Getting the Data

1. Go to the [Kaggle competition page](https://www.kaggle.com/competitions/lifeclef-2025-fungiclef)
2. Accept the competition rules
3. Download the training/test data and place it like:

```
data/
 ├── train_images/
 ├── test_images/
 ├── train_metadata.csv
 ├── test_metadata.csv
 └── train_labels.csv
```

---

## Setup

Create a virtual environment and install dependencies:

```bash
python -m venv .venv
source .venv/bin/activate        # macOS / Linux
# .venv\Scripts\activate         # Windows

pip install -r requirements.txt
```

Minimal `requirements.txt` example:

```
numpy
pandas
scikit-learn
torch>=1.8
tqdm
opencv-python
matplotlib
seaborn
efficientnet-pytorch
albumentations
```

---

## How to Run

### 1. Preprocess

```bash
python src/preprocess.py --input_dir data/train_images --meta_path data/train_metadata.csv --output_dir data/processed --config config.py
```

### 2. Train

```bash
python src/train.py --data_dir data/processed --model_dir models/exp1 --epochs 50 --batch-size 32
```

### 3. Inference

```bash
python src/inference.py --model_path models/exp1/best.pth --test_dir data/test_images --meta_path data/test_metadata.csv --output submissions/submission_exp1.csv
```

---

## Notebooks

Open `notebooks/` for:

- Data exploration and metadata analysis
- Visualization of fungal images (species, distribution, etc.)
- Baseline models: EfficientNet, ResNet, Vision Transformers

---

## Tips

- Handle class imbalance with weighted sampling and focal loss
- Apply data augmentation: rotation, blur, scaling, color jitter
- Incorporate metadata (location, ecology) for improved predictions
- Experiment with ensemble methods for higher accuracy

---

## References

- [FungiCLEF25 @ CVPR-FGVC & LifeCLEF 2025](https://www.kaggle.com/competitions/lifeclef-2025-fungiclef)

---
'''

# Write to file
with open('README_FungiCLEF25.md', 'w', encoding='utf-8') as f:
    f.write(fungiclef_readme)
'File README_FungiCLEF25.md generated.'
