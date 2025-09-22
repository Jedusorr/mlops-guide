# MLOps - Celestial Body Classification

This repository contains the code from
[A guide to MLOps](https://mlops.swiss-ai-center.ch/).

## Notes
- Chapter 1.1 was done in a Jupyter Notebook.  
- In Chapter 1.2 the notebook was refactored into Python scripts:
  - `prepare.py` to preprocess the dataset (`data/raw` → `data/prepared`)
  - `train.py` to train a small CNN and save it under `model/`
  - `evaluate.py` to reload the model and produce metrics in `evaluation/`
- Parameters are centralized in `params.yaml` (e.g. learning rate, epochs, image size).
- A helper function `set_global_seed` in `src/utils/seed.py` ensures reproducibility.
- After running the full pipeline, the project produces:
  - `data/prepared/` with train/test datasets
  - `model/model.keras` (the trained model)
  - `evaluation/metrics.txt` and `evaluation/label_hist.png` (evaluation results)


  Pour executer :

  # Prepare the dataset
python3.12 src/prepare.py data/raw data/prepared

# Train the model with the train dataset and save it
python3.12 src/train.py data/prepared model

# Evaluate the model performance
python3.12 src/evaluate.py model data/prepared