# Physics-Sim

This repository collects small, self‑contained physics and numerical simulation projects intended for learning, teaching, and quick experimentation. Each subfolder contains one or more Jupyter notebooks plus a focused README that explains the underlying mathematics and how to run the code.

## Projects Overview

- **`mProject_0/` — Projectile motion**
  - Constant‑gravity projectile motion in 2D without air resistance.
  - The theoretical trajectory of a projectile launched with initial speed $v_0$ and angle $\theta$ (from horizontal) is
    $$
    x(t) = v_0 \cos\theta \, t, \qquad
    y(t) = y_0 + v_0 \sin\theta \, t - \frac{1}{2} g t^2.
    $$
  - The notebook compares numerical trajectories with these analytic expressions and explores how the range
    $$
    R = \frac{v_0^2 \sin(2\theta)}{g}
    $$
    depends on launch angle.

- **`mProject_1/` — Random walk**
  - 2D random walk (drunkard’s walk) with independent steps in $x$ and $y$.
  - Demonstrates that the typical displacement after $N$ steps scales like
    $$
    \langle r^2 \rangle^{1/2} \propto \sqrt{N},
    $$
    a fundamental result in diffusion and stochastic processes.

- **`Numerical Analysis/` — Numerical methods and dynamical systems**
  - **`Numerical_Integration.ipynb`**: Approximates integrals
    $$
    I = \int_a^b f(x)\,\mathrm{d}x
    $$
    using the trapezoidal and Simpson rules, and compares numerical errors as the step size $h$ is refined.
  - **`Root_Finding.ipynb`**: Solves nonlinear equations $f(x)=0$ using bisection and Newton–Raphson iterations
    $$
    x_{k+1} = x_k - \frac{f(x_k)}{f'(x_k)}.
    $$
  - **`Logistic Map.ipynb`**: Iterates the logistic map
    $$
    x_{n+1} = r x_n (1 - x_n)
    $$
    and builds a bifurcation diagram showing period‑doubling and chaos as the control parameter $r$ varies.

See the README in each subfolder for more detailed mathematical background and notebook‑specific instructions.

## Requirements

- Python 3.8+
- `numpy`
- `matplotlib`
- A Jupyter environment (`jupyterlab` or `notebook`)

You can install dependencies either from `requirements.txt` (if present) or manually:

```bash
pip install numpy matplotlib jupyterlab
```

## How to Run the Notebooks

1. **Create and activate a virtual environment** (recommended).
2. **Install dependencies**, e.g.
   ```bash
   pip install -r requirements.txt
   ```
   or
   ```bash
   pip install numpy matplotlib jupyterlab
   ```
3. **Start Jupyter** in the repository root:
   ```bash
   jupyter lab
   ```
   or
   ```bash
   jupyter notebook
   ```
4. Open the notebook of interest (e.g. `mProject_0/Projectile.ipynb`) and run the cells from top to bottom.

Each project README suggests experiments and parameter changes to help you explore the underlying physics or numerical method.
