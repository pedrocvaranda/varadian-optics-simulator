# Installation Guide — Varandian Optics Simulator

**Get the simulator running in under 5 minutes.**

---

## Prerequisites

Make sure you have Python 3.8+ installed:

```bash
python --version  # Should be 3.8 or higher
```

---

## Step-by-Step Setup

### 1. Clone or Download

```bash
cd varandian-optics-simulator
```

### 2. Create Virtual Environment (Recommended)

**Windows:**

```bash
python -m venv venv
venv\Scripts\activate
```

**Mac/Linux:**

```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

Installs: numpy, scipy, matplotlib, jupyter, ipywidgets, and more.

### 4. Test Installation

```bash
python -m tests.test_geodesics
```

Expected output:

```text
SK Euclidean test passed
SK Spherical test passed
SK Hyperbolic test passed
Space naming test passed
Geodesic computation test passed

All tests passed!
```

### 5. Launch Jupyter

```bash
jupyter notebook examples/quickstart.ipynb
```

Your browser will open with the interactive tutorial.

---

## Project Structure

```text
varandian-optics-simulator/
├── core/                    # Core mathematical engine
│   ├── metrics.py          # Eq (1)-(2): SK(r) functions
│   ├── geodesics.py        # Eq (3)-(5): Ray propagation
│   └── __init__.py
├── visualization/          # Plotting & projections
│   ├── projections.py     # 2D projections
│   ├── plotting.py        # Plot functions
│   └── __init__.py
├── examples/              # Jupyter notebooks
│   ├── quickstart.ipynb   # START HERE
│   └── comparison.ipynb   # Advanced comparisons
├── tests/                 # Unit tests
│   └── test_geodesics.py
├── paper/                 # Original research paper
├── requirements.txt       # Dependencies
└── README.md
```

---

## Troubleshooting

### "No module named 'core'"

Make sure you're running from the project root directory:

```bash
cd varandian-optics-simulator
python -m tests.test_geodesics
```

### "numpy not found"

```bash
pip install -r requirements.txt
```

### Jupyter doesn't open

```bash
pip install --upgrade jupyter
jupyter notebook
```

---

## Next Steps

1. Run quickstart: `jupyter notebook examples/quickstart.ipynb`
2. Explore code: read through `core/metrics.py`
3. Run tests: `python -m tests.test_geodesics`
4. Modify examples: create your own notebooks

---

## Citation

If you use this software, please cite:

```bibtex
@software{varanda2026varandian_sim,
  author = {Varanda, Pedro Coutinho},
  title  = {Varandian Optics Simulator},
  year   = {2026},
  url    = {https://github.com/pedrocvaranda/varandian-optics-simulator}
}
```

And the original paper:

```bibtex
@article{varanda2026varandian,
  author = {Varanda, Pedro Coutinho},
  title  = {Varandian Optics: A Non-Euclidean Formulation of Light Propagation},
  year   = {2026},
  doi    = {10.5281/zenodo.18529071},
  url    = {https://doi.org/10.5281/zenodo.18529071}
}
```

---

## Need Help?

- Read the [README.md](README.md)
- Check the [paper](https://doi.org/10.5281/zenodo.18529071)
- Open an issue on GitHub
