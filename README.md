# FVOD: Formal Verification for Object Detection

This repository contains the implementation accompanying our paper:

**Towards Formal Verification of Deep Neural Networks for Object Detection**

The code extends state-of-the-art neural network verification techniques to object detection models, with a particular focus on verifying IoU-related properties.

---

## 📁 Repository Structure

```
 ├── abcrown/    # Extended version of alpha-beta-CROWN with OD / IoU verification support
 ├── train/      # Pre-processing scripts (training models, data preparation)
 ├── analyze/    # Post-processing and result analysis
```

* **abcrown/**: A fork of [alpha-beta-CROWN](https://github.com/Verified-Intelligence/alpha-beta-CROWN), extended to support object detection and IoU-based verification conditions.
* **train/** and **analyze/**: Utilities for preparing models and analyzing verification results.
* The main entry point is [`abcrown/FVOD/verify_fc.py`](abcrown/FVOD/verify_fc.py), which provides a minimal, configurable verification workflow.

---

## 📦 Requirements and Installation

The code is built on top of the **alpha-beta-CROWN** verification framework.
Our implementation is based on the April 2024 version of alpha-beta-CROWN (commit `1a3533a`).

### Setup Instructions

1. **Clone alpha-beta-CROWN and checkout the required commit:**

```bash
git clone --recursive https://github.com/Verified-Intelligence/alpha-beta-CROWN.git
cd alpha-beta-CROWN
git checkout 1a3533a
```

2. **Create and activate a conda environment:**

```bash
conda create -n alpha-beta-crown python=3.11 -y
conda activate alpha-beta-crown
```

3. **Install dependencies:**

```bash
pip install -r complete_verifier/requirements.txt
```

This repository introduces only **pure-Python modifications** and does not add dependencies beyond those required by alpha-beta-CROWN.

After installation, replace the original alpha-beta-CROWN source code with the modified version provided in this repository under the `abcrown/` directory.

---

## Usage

### Minimal Example

After setup, a minimal verification example can be run using:

```bash
python abcrown/FVOD/verify_fc.py --config abcrown/complete_verifier/exp_configs/OD/d_loc_init.yaml
```

This configuration is intended for fast validation and sanity checking.

### General Usage

To run verification with a custom configuration:

```bash
python abcrown/FVOD/verify_fc.py --config path/to/your_config.yaml
```

Verification behavior (model, dataset, perturbation bounds, and IoU thresholds) can be customized directly via the YAML configuration files.

---

## 📄 License

MIT License

The software is provided “as is”, without warranty of any kind, express or implied.
