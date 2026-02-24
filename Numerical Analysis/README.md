# Numerical Analysis

This folder collects small, focused notebooks that illustrate core ideas from numerical analysis and nonlinear dynamics. Each notebook combines short theoretical summaries with Python implementations and visualizations.

## Contents

- **`Numerical_Integration.ipynb` — Numerical quadrature**
  - Approximates definite integrals
    $$
    I = \int_a^b f(x)\,\mathrm{d}x
    $$
    using composite trapezoidal and Simpson rules.
  - Investigates how the error decreases as the step size $h$ is refined.

- **`Root_Finding.ipynb` — Solving $f(x)=0$**
  - Implements classic algorithms for root finding:
    - **Bisection method** on an interval $[a,b]$ with $f(a)\,f(b) < 0$.
    - **Newton–Raphson method** with the iteration
      $$
      x_{k+1} = x_k - \frac{f(x_k)}{f'(x_k)}.
      $$
  - Compares convergence behavior and sensitivity to initial guesses.

- **`Logistic Map.ipynb` — Bifurcation and chaos**
  - Studies the logistic map
    $$
    x_{n+1} = r x_n (1 - x_n), \qquad 0 \le x_n \le 1,
    $$
    as the control parameter \(r\) varies.
  - Builds a bifurcation diagram and illustrates period‑doubling routes to chaos.

## How to Run

1. Ensure you have `numpy` and `matplotlib` installed in your Python environment.
2. From the repository root, start Jupyter:
   ```bash
   jupyter lab
   ```
   or
   ```bash
   jupyter notebook
   ```
3. Open any notebook in the `Numerical Analysis/` folder and run the cells from top to bottom.

## Suggested Experiments

- **Numerical integration**
  - Change the function $f(x)$ (e.g. polynomials, oscillatory functions, exponentials).
  - Vary the number of sub‑intervals $n$ and observe how the error behaves for each method.

- **Root finding**
  - Try different nonlinear functions with multiple roots.
  - Experiment with good and bad initial guesses for Newton’s method and see when it fails.

- **Logistic map**
  - Change the initial condition $x_0$ and compare long‑term behavior for fixed $r$.
  - Zoom into regions of the bifurcation diagram where period‑doubling or chaotic windows appear.
