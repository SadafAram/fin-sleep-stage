# Sleep Stage Classification with ViViT and Feature Imitation Networks (FIN)

## Introduction

This project focuses on sleep stage classification using deep learning techniques. We preprocess the PhysioNet dataset
to train a **Video Vision Transformer (ViViT)** model for classifying sleep stages. Additionally, we introduce **Feature
Imitation Networks (FIN)**, where we train separate models to estimate Shannon entropy and band power of a signal using
synthetic data. We then integrate FIN into ViViT and observe performance improvements.

### **Project Structure**

The project is organized as follows:

```
📂 data/
   ├── original/              # Original PhysioNet dataset
   ├── split/                 # Preprocessed sleep data
   ├── 3000/                  # Windowed data for training

📂 fin/
   ├── shannon_entropy.ipynb  # Shannon entropy model training
   ├── band_power.ipynb       # Band power model training

📂 models/

📂 results/

📂 scripts/
   ├── 0_preprocessing.ipynb  # Data preprocessing (EDF to CSV, windowing)
   ├── 1_simple_vivt.ipynb    # Training script for ViViT model
   ├── 2_integrated.ipynb     # Training script for FIN-enhanced ViViT model
   ├── dhedfreader.py         # Helper functions for preprocessing

📜 readme.md                  # This file
📜 requirements.txt           # Required Python dependencies
```

### **Methodology**

1. **Data Preprocessing:**
    - We process the **PhysioNet Sleep Dataset**, converting EEG signals from EDF format to structured NumPy arrays and
      CSV files.
    - Data is segmented into windows for training and saved in `data/3000/`.

2. **ViViT Model Training:**
    - We employ **Video Vision Transformer (ViViT)** to classify sleep stages using spectrogram representations of EEG
      signals.
    - The model is trained on processed PhysioNet data.

3. **Feature Imitation Networks (FIN):**
    - We create synthetic datasets and train separate models for **Shannon entropy estimation** and **band power
      detection**.
    - These models are trained using supervised learning with synthetic signal transformations.

4. **FIN Integration with ViViT:**
    - The trained entropy and band power models are incorporated as feature extractors into ViViT.
    - We fine-tune the integrated model and observe improvements in sleep stage classification accuracy.

---

## Installation

### **Step 1: Set Up Python Environment**

Ensure you have **Python 3.9** installed. You can create a virtual environment and activate it:

```bash
python3.9 -m venv sleep_env
source sleep_env/bin/activate  # For Linux/macOS
sleep_env\Scripts\activate    # For Windows
```

### **Step 2: Install Dependencies**

Run the following command to install all required packages:

```bash
pip install -r requirements.txt
```

## Results & Observations

- The **ViViT model alone** achieves a strong baseline accuracy for sleep stage classification.
- **Integrating FIN** improves performance by leveraging entropy and band power features.

---

## Acknowledgments

This project is based on **PhysioNet's Sleep-EDF dataset** and leverages **ViViT architecture** for video-based EEG
analysis.

---
