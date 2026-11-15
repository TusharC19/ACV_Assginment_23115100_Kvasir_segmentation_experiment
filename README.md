# Kvasir Segmentation Experiment

This repository contains a reproducible deep learning experiment for binary polyp segmentation on the Kvasir-SEG dataset.

The project is implemented in a single Jupyter notebook and compares a small U-Net baseline against a controlled variant that adds a global-pooling context branch in the bottleneck.

## Project goal

The goal is to evaluate whether adding an image-level global context branch improves segmentation quality for polyp detection while keeping the rest of the architecture and training setup unchanged.

## What is included

- Automatic download and extraction of the Kvasir-SEG dataset
- Seeding and deterministic split creation
- Train/validation/test data loaders
- Baseline U-Net implementation
- Modified U-Net with a global-pooling context branch
- Identical training budget for both models
- Evaluation metrics such as IoU, Dice, and latency
- Artifact export for comparison plots and saved checkpoints

## Dataset

- Dataset: Kvasir-SEG
- Task: binary semantic segmentation
- Classes:
  - 0 = background
  - 1 = polyp
- Dataset size: 1000 images with matching masks
- Split: seeded 80/10/10 train/validation/test split
- Input size: 256 x 256

## Notebook

- `Kvasir_Segmentation_Experiment_v3.ipynb`

This notebook contains the complete workflow, including:

1. Dataset download and validation
2. Data preprocessing and split creation
3. Model architecture definition
4. Training loop with early stopping
5. Evaluation and statistical comparison
6. Prediction visualization and failure analysis
7. Export of artifacts to a ZIP bundle

## Environment

The project is designed to run in Google Colab or Kaggle notebooks, and it also supports local execution if the Kvasir-SEG dataset is available.

Recommended dependencies:

- Python 3.10+
- PyTorch
- TorchVision
- NumPy
- Matplotlib
- Pillow
- pandas
- SciPy (optional for Wilcoxon comparison)

## Running the project

1. Open the notebook in Colab or Jupyter.
2. Run all cells in order.
3. If needed, upload or download the Kvasir-SEG ZIP dataset automatically from the dataset source.
4. Allow the training and evaluation cells to complete.
5. Inspect generated artifacts in the working directory.

## Generated outputs

The notebook produces files such as:

- `split_indices.json`
- `baseline_best.pth`
- `modified_best.pth`
- `baseline_history.json`
- `modified_history.json`
- `model_comparison.csv`
- `evaluation_results.json`
- `loss_curves.png`
- `predictions.png`
- `failure_cases.png`
- `assignment_b_artifacts.zip`

## Notes

This repository focuses on a controlled experiment rather than a production deployment. The key experimental variable is intentionally isolated: the global-pooling context branch is the only architectural change between the baseline and the modified model.

## License

No explicit license file is included in this repository. Please check the repository settings or upstream assignment instructions for licensing details.
