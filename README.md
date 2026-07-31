# Varandian Optics Simulator

**Interactive 2D visualization of light propagation in constant-curvature spaces**

Implementation of the theoretical framework from:

> **Varandian Optics: A Non-Euclidean Formulation of Light Propagation**
> Pedro Coutinho Varanda
> *Zenodo*, 2026

[Read the paper](https://doi.org/10.5281/zenodo.18529071)

---

## What is This?

This simulator brings to life the **Varandian Optics** framework, which extends classical geometric optics from flat (Euclidean) space to curved spaces with constant curvature.

**Key Features:**

- **Geodesic light ray propagation** — in spherical (K > 0) and hyperbolic (K < 0) spaces
- **2D projections** — Stereographic (spherical) and Poincaré disk (hyperbolic)
- **Interactive Jupyter notebooks** — with real-time parameter control
- **Side-by-side comparison** — propagation across different curvatures
- **Exact implementation** — equations (1)–(7) from the research paper

---

## Quick Start

### Installation

```bash
# Clone repository
git clone https://github.com/pedrocvaranda/varandian-optics-simulator.git
cd varandian-optics-simulator

# Install dependencies
pip install -r requirements.txt

# Launch Jupyter
python -m notebook examples/quickstart.ipynb
```

### Your First Ray

```python
from core import compute_ray
from visualization import plot_single_ray

# Compute ray in spherical space
theta, r = compute_ray(r0=0.5, theta0=0, K=1.0, C=0.3)

# Visualize with stereographic projection
plot_single_ray(theta, r, K=1.0)
```

---

## Theory

### The Four Laws of Varandian Optics

**Law I — Geodesic Propagation**
Light propagates along geodesics of the curved space.

**Law II — Varandian Refraction** (Equation 6)
Generalized Snell's law:

```text
n₁ SK₁(r) sin(θ₁) = n₂ SK₂(r) sin(θ₂)
```

**Law III — Varandian Reflection**
Reflection follows geodesic symmetry: `θᵢ = θᵣ`

**Law IV — Index-Curvature Duality** (Equation 7)
Radial refractive index profiles can emulate curved metrics:

```text
n(ρ) = 2/(1 + ρ²)   for K = +1 (spherical)
n(ρ) = 2/(1 - ρ²)   for K = -1 (hyperbolic)
```

### The Metric (Equations 1–2)

```text
ds² = dr² + SK(r)² dθ²
```

where:

```text
         ⎧ (1/√K) sin(√K r)       K > 0  (Spherical)
SK(r) =  ⎨ r                      K = 0  (Euclidean)
         ⎩ (1/√|K|) sinh(√|K| r)  K < 0  (Hyperbolic)
```

---

## Project Structure

```text
varandian-optics-simulator/
├── README.md
├── requirements.txt
├── INSTALL.md
├── docs/
│   ├── README.md
│   ├── index.html
│   └── Varandian_Optics.pdf    # Original research paper
├── core/
│   ├── __init__.py
│   ├── metrics.py              # Equations (1)-(2): Metrics
│   ├── geodesics.py            # Equations (3)-(5): Ray propagation
│   └── refraction.py           # Equation (6): Refraction law
├── visualization/
│   ├── projections.py          # Stereographic & Poincaré projections
│   ├── plotting.py             # High-level plotting functions
│   └── __init__.py
├── examples/
│   ├── quickstart.ipynb        # START HERE
│   ├── refraction_demo.ipynb
│   ├── simple_example.py
│   ├── run_critical_angles.py
│   └── comparison.ipynb
└── tests/
    ├── __init__.py
    └── test_geodesics.py
```

---

## Examples

### Example 1: Basic Ray

```python
from core import compute_ray, space_type_name
from visualization import plot_single_ray

r0 = 0.5      # Initial radius
K  = 1.0      # Curvature (spherical)
C  = 0.3      # Constant of motion

theta, r = compute_ray(r0, theta0=0, K=K, C=C)

plot_single_ray(theta, r, K)
print(f"Ray in {space_type_name(K)} space")
```

### Example 2: Comparing Curvatures

```python
from visualization import plot_comparison

results = {}
for K in [-1, 0, 1]:
    _, r = compute_ray(r0=0.6, theta0=0, K=K, C=0.35)
    results[K] = r

plot_comparison(theta, results, K_values=[-1, 0, 1])
```

### Example 3: Multiple Rays

```python
from visualization import plot_multiple_rays

rays = []
for C_val in [0.2, 0.3, 0.4, 0.5]:
    theta, r = compute_ray(r0=0.5, theta0=0, K=1.0, C=C_val)
    rays.append((theta, r, f'C={C_val}', plt.cm.viridis(C_val)))

plot_multiple_rays(rays, K=1.0)
```

---

## About the Author

**Pedro Coutinho Varanda**

- **#1 Brazil** — National Astronomy Olympiad (OBA 2025, Perfect Score)
- **#2 Brazil** — OBA 2023
- **#3 Brazil** — OBA 2024
- **3x Selected** — International Olympiad on Astronomy and Astrophysics (IOAA)
- **4x Gold** — Canguru Mathematics Competition (2022–2025)

ML/AI enthusiast | Rio de Janeiro, Brazil

[GitHub](https://github.com/pedrocvaranda) • [ORCID](https://orcid.org/0009-0004-5199-1745) • [Email](mailto:pedrocvaranda@gmail.com)

---

## Contributing

Contributions are welcome! Feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## Related Projects

- [Cash Allocation Model](https://github.com/pedrocvaranda/modelo_alocacao_caixa) — ML-based financial optimizer
- [Chess Trainer](https://github.com/pedrocvaranda/treinador-xadrez) — AI-powered chess learning

---

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org) [![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE) [![Status](https://img.shields.io/badge/Status-Active-success.svg)]() [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.18529071.svg)](https://doi.org/10.5281/zenodo.18529071)
