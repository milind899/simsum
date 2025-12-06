# SIMSUM: Document-level Text Simplification via Simultaneous Summarization

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.10%2B-green.svg)](https://www.python.org/)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.0%2B-orange.svg)](https://pytorch.org/)

A PyTorch implementation for document-level text simplification using simultaneous summarization, based on the ACL 2023 paper.

> **📝 Original Work**: This project is a fork of [epfml/easy-summary](https://github.com/epfml/easy-summary) by the **EPFL MLO Lab**. All credit for the original research and implementation goes to the original authors.
>
> **📄 Paper**: [SIMSUM: Document-level Text Simplification via Simultaneous Summarization (ACL 2023)](https://aclanthology.org/2023.acl-long.123/)

---

## ✨ Changes from Original

This fork includes the following improvements:

| Change | Description |
|--------|-------------|
| 🪟 **Windows Compatibility** | Fixed `DataLoader` freezing issue by setting `num_workers=0` (multiprocessing doesn't work well on Windows) |
| � **Updated Dependencies** | Upgraded all packages to latest compatible versions (original had outdated dependencies that caused errors) |
| �📖 **Improved Documentation** | Added detailed README with installation steps, configuration options, and troubleshooting |
| 🧹 **Code Cleanup** | Removed debug files and unnecessary dependencies |
| 🐍 **Python 3.10+ Support** | Verified compatibility with modern Python versions |

---

## 🚀 Quick Start

### Prerequisites
- Python 3.10 or higher
- NVIDIA GPU with CUDA support (recommended)
- Git

### Installation

```bash
# Clone the repository
git clone https://github.com/milind899/simsum.git
cd simsum

# Create virtual environment
python -m venv venv

# Activate virtual environment
# Windows:
.\venv\Scripts\activate
# Linux/Mac:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt
```

### Training

```bash
cd SimSum
python main.py --max_epochs 1 --gpus 1
```

### Evaluation

```bash
cd SimSum
python evaluate.py
```

---

## 📁 Project Structure

```
simsum/
├── SimSum/
│   ├── data/                    # Datasets (D-Wiki, WikiDoc)
│   ├── Bart_baseline_finetuned.py   # BART model implementation
│   ├── T5_baseline_finetuned.py     # T5 model implementation
│   ├── Bart2.py                 # SimSum with BART backbone
│   ├── T5_2.py                  # SimSum with T5 backbone
│   ├── main.py                  # Training entry point
│   ├── evaluate.py              # Evaluation script
│   └── preprocessor.py          # Data preprocessing utilities
├── requirements.txt
└── LICENSE
```

---

## 📊 Datasets

The datasets are located in `SimSum/data/`:
- **D-Wiki** (`D_wiki/`): D-Wikipedia dataset
- **WikiDoc** (`wiki_doc/`): WikiDoc dataset

---

## 🔧 Configuration Options

| Argument | Default | Description |
|----------|---------|-------------|
| `--max_epochs` | 7 | Number of training epochs |
| `--gpus` | 1 | Number of GPUs to use |
| `--train_batch_size` | 6 | Training batch size |
| `--learning_rate` | 1e-5 | Learning rate |
| `--max_seq_length` | 256 | Maximum sequence length |

---

## 📈 Metrics

The evaluation script computes:
- **SARI**: Simplification quality
- **D-SARI**: Document-level SARI
- **BLEU**: Translation quality
- **FKGL**: Flesch-Kincaid Grade Level (readability)

---

## 🐛 Troubleshooting

### Training stuck at 0% on Windows
This is a known issue with PyTorch DataLoader on Windows. The fix has already been applied (using `num_workers=0`).

### CUDA out of memory
Reduce batch size: `--train_batch_size 2`

### Missing NLTK data
The script automatically downloads required NLTK data on first run.

---

## 📜 License

This project is licensed under the **Apache License 2.0** - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- **Original Authors**: [EPFL MLO Lab](https://github.com/epfml) for the SIMSUM research and implementation
- **Paper**: "SIMSUM: Document-level Text Simplification via Simultaneous Summarization" (ACL 2023)
- **Original Repository**: [epfml/easy-summary](https://github.com/epfml/easy-summary)

---

## 📖 Citation

If you use this code, please cite the original paper:

```bibtex
@inproceedings{simsum2023,
  title={SIMSUM: Document-level Text Simplification via Simultaneous Summarization},
  author={...},
  booktitle={Proceedings of the 61st Annual Meeting of the Association for Computational Linguistics (ACL)},
  year={2023}
}
```