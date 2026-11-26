# Image Classification with CNNs — CIFAR-10

Deep Learning project (Ironhack, week 7): build a Convolutional Neural Network to classify the
[CIFAR-10](https://www.cs.toronto.edu/~kriz/cifar.html) dataset, compare it with transfer learning
on pre-trained models, and deploy the best model as a Flask web app.

- **Dataset:** CIFAR-10 — 60,000 colour images (32×32) in 10 classes
- **Framework:** TensorFlow / Keras
- **Training environment:** Google Colab (GPU)

## Notebooks

| # | Notebook | Content | Open |
|---|----------|---------|------|
| 1 | [`01_data_preprocessing.ipynb`](notebooks/01_data_preprocessing.ipynb) | Data loading, exploration, train/val/test split, normalization, augmentation, `tf.data` pipeline | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/MartinAlani/project_deep_learning_week_7/blob/main/notebooks/01_data_preprocessing.ipynb) |
| 2 | Custom CNN | Architecture, training with early stopping | *coming soon* |
| 3 | Evaluation | Accuracy, precision, recall, F1, confusion matrix | *coming soon* |
| 4 | Transfer learning | Comparison of pre-trained models | *coming soon* |

## Project structure

```
├── notebooks/      # Jupyter notebooks, one per project phase
├── models/         # Trained models (not tracked by git)
├── app/            # Flask deployment app
├── report/         # PDF report and presentation
├── test_images/    # Sample images to test the deployed app
└── requirements.txt
```

## Setup

The notebooks are designed for Google Colab: click an **Open in Colab** badge above and select
*Runtime → Change runtime type → T4 GPU*.

To run locally instead:

```bash
pip install -r requirements.txt
```
