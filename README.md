# Deep Learning - Hands-on Labs

Hands-on lab sessions for the **Deep Learning** lectures of the
[MDMC – Master in Data Management and Curation](https://www.areasciencepark.it/call/mdmc/),
a collaboration between [Area Science Park](https://www.areasciencepark.it/) and
[SISSA](https://www.sissa.it/) (Scuola Internazionale Superiore di Studi Avanzati), Trieste.

## Teaching staff

| Role | Name |
|------|------|
| Deep Learning lecturer | Alessio Ansuini |
| Hands-on session tutor | Emanuele Goat |

## About the master

MDMC is a postgraduate advanced training programme (60 ECTS) taught entirely in English. It
trains data professionals to apply FAIR principles and Open Science practices, design
FAIR-by-design data workflows, write and manage Data Management Plans, curate metadata, and
preserve research data in trusted repositories.

The 3rd edition (academic year 2026–2027) runs from September 2026 to June 2027. It consists of
about eight weeks of in-person lectures at Area Science Park and SISSA, a six-month laboratory
internship, and a final project. These labs belong to the lecture block.

**Expected background:** basic Python programming, undergraduate-level mathematical analysis, and
basic probability and statistics.

## About these labs

The labs are Jupyter notebooks built on **PyTorch**. They take you from your first
multilayer perceptron up to autoencoders and learning without labels, using MNIST and
FashionMNIST throughout so that the focus stays on the models and not on the data plumbing.

## Contents

| Lab | Notebook | Open in Colab | Topics |
|-----|----------|---------------|--------|
| 1 | [`hands_on_1.ipynb`](hands_on_1.ipynb) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/progManu/mdmc_dl_hands_on/blob/master/hands_on_1.ipynb) | **Introduction to MLPs and CNNs** — Colab and PyTorch basics, datasets, transforms and `DataLoader`s, MLPs, autograd, optimizers (SGD, Adam), cross-entropy loss, training and evaluation loops, confusion matrices, hyperparameter tuning with grid search (skorch), CNNs and MLP vs CNN comparison |
| 2a | [`hands_on_2a.ipynb`](hands_on_2a.ipynb) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/progManu/mdmc_dl_hands_on/blob/master/hands_on_2a.ipynb) | **Learning without labels: PCA, K-means and Autoencoders** — supervised vs unsupervised learning, PCA as encoder/decoder, explained variance and reconstructions, K-means (by hand and on MNIST), clustering accuracy, autoencoders and their latent space, clustering in latent space, anomaly detection via reconstruction error, pre-training and fine-tuning with few labels |
| 2b | [`hands_on_2b.ipynb`](hands_on_2b.ipynb) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/progManu/mdmc_dl_hands_on/blob/master/hands_on_2b.ipynb) | **Discriminative vs Generative models: Autoencoders and VAEs** — what a classifier knows (noise inputs, drawing digits by gradient ascent), autoencoders and reconstruction loss, sampling the latent space, VAEs (probabilistic encoder, ELBO, KL divergence, reparameterization trick), generation and AE vs VAE interpolation, conditional VAE as a generative classifier, discriminative vs generative comparison |

Each lab ends with a short **homework** building on the day's material; we discuss doubts and
curiosities at the start of the next session.

### Repository layout

```
.
├── hands_on_1.ipynb          # Lab 1 — student version (exercises to complete)
├── hands_on_2a.ipynb         # Lab 2a — student version
├── hands_on_2b.ipynb         # Lab 2b — student version
├── solutions/
│   ├── solved_hands_on_1.ipynb   # Lab 1 — solutions
│   ├── solved_hands_on_2a.ipynb  # Lab 2a — solutions
│   └── solved_hands_on_2b.ipynb  # Lab 2b — solutions
├── notebooks_imgs/           # figures embedded in the notebooks
└── pocs/                     # drafts / proofs of concept for upcoming labs
                              #   (e.g. Lab 2: discriminative vs generative models, AEs and VAEs)
```

## How to use the notebooks

The `hands_on_*.ipynb` files are the **student versions**: some code cells are incomplete and
completing them is your job.

- **🛠 Exercise** cells explain what to implement, with hints on which functions to use.
- The code cell right after each exercise contains `# TODO` comments and `...` placeholders:
  **replace every `...` with your code**. Everything else is already written — read it, you will need it.
- Many exercises are followed by a **✅ Check** cell: run it after your solution. If it prints
  `All good!` (or the expected values), move on.
- Run the cells **in order**: later exercises rely on variables and functions defined earlier.
- If you get stuck, read the docstrings, the explanation cells above the exercise and the linked
  documentation — or ask!

The `solutions/solved_hands_on_*.ipynb` notebooks contain the reference solutions. Try the exercises on your
own first.

## Running the labs

### First: clone the repository

The notebooks use files from this repository (e.g. the figures in `notebooks_imgs/`), so
**do not download a single notebook on its own**: clone the whole repository and open the
notebooks from inside the cloned folder, otherwise those paths will not work.

```bash
git clone https://github.com/progManu/mdmc_dl_hands_on.git mdmc_dl_hands_on
cd mdmc_dl_hands_on
```

### On Google Colab (recommended during the course)

The experiments are lightweight, so the labs are designed to run on
[Google Colab](https://colab.research.google.com/), which provides free (time-limited) GPU access.
Open a lab directly in Colab with the **Open in Colab** badge in the [Contents](#contents) table
(these open the student versions, not the solutions). Then clone the repository by running this
in a code cell before anything else, so the notebook can find the files it uses:

```python
!git clone https://github.com/progManu/mdmc_dl_hands_on.git mdmc_dl_hands_on
%cd mdmc_dl_hands_on
```

Enable a GPU from `Runtime > Change runtime type` if needed. Your changes live only in the Colab
session: use `File > Save a copy in Drive` to keep your work. PyTorch, torchvision and
scikit-learn are preinstalled; install skorch with:

```bash
!pip install skorch
```

### Locally

The notebooks were developed with Python 3.12. From inside the cloned `mdmc_dl_hands_on` folder:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter lab
```

Datasets (MNIST, FashionMNIST) are downloaded automatically by `torchvision` the first time
they are used. Everything runs on CPU, though a GPU speeds up training noticeably.

## Requirements

- Python ≥ 3.10 (developed on 3.12)
- [PyTorch](https://pytorch.org/) and [torchvision](https://docs.pytorch.org/vision/stable/)
- NumPy, Matplotlib
- [scikit-learn](https://scikit-learn.org/)
- [skorch](https://skorch.readthedocs.io/) (Lab 1, hyperparameter search)

## Acknowledgements

Material prepared for the [MDMC – Master in Data Management and Curation](https://www.areasciencepark.it/call/mdmc/),
Area Science Park & SISSA, Trieste. For information about the programme, see the official page or write to
[mdmc@sissa.it](mailto:mdmc@sissa.it).
