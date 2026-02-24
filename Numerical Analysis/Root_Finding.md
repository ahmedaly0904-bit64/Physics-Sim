# Root_Finding.ipynb — Solving $f(x) = 0$

This notebook explores standard numerical algorithms for solving nonlinear equations of the form
$$
f(x) = 0,
$$
where an analytical solution may not be available. It focuses on bracketing and open methods, and compares their convergence behavior.

## Mathematical Background

### Problem Setup

Given a continuous function $f : \mathbb{R} \to \mathbb{R}$, we often need to find a root $x^\star$ such that $f(x^\star) = 0$. Numerical methods construct a sequence $\{x_k\}$ that (hopefully) converges to a root.

### Bisection Method

The **bisection method** requires an initial interval $[a_0, b_0]$ with
$$
f(a_0)\,f(b_0) < 0,
$$
guaranteeing (by the Intermediate Value Theorem) at least one root inside.

At each iteration:

1. Compute the midpoint
   $$
   m_k = \frac{a_k + b_k}{2}.
   $$
2. Evaluate $f(m_k)$.
3. Replace the sub‑interval that does *not* contain a sign change:
   - If $f(a_k)\,f(m_k) < 0$, set $a_{k+1} = a_k$, $b_{k+1} = m_k$.
   - Else, set $a_{k+1} = m_k$, $b_{k+1} = b_k$.

This produces a shrinking interval $[a_k, b_k]$ whose length halves every step; the error decreases linearly with rate $1/2$.

### Newton–Raphson Method

The **Newton–Raphson method** is an open (non‑bracketing) method that uses derivative information. Starting from an initial guess $x_0$, we iterate
$$
x_{k+1} = x_k - \frac{f(x_k)}{f'(x_k)}.
$$
Geometrically, this is the $x$‑intercept of the tangent line to $f(x)$ at $x_k$.

Near a simple root where $f'(x^\star) \neq 0$, Newton’s method converges **quadratically**, meaning that roughly
$$
|x_{k+1} - x^\star| \approx C |x_k - x^\star|^2.
$$
However, poor initial guesses, flat derivatives, or discontinuities can lead to divergence.

### (Optional) Secant Method

Some implementations also include the **secant method**, which approximates the derivative using the last two iterates:
$$
x_{k+1} = x_k - f(x_k)\,\frac{x_k - x_{k-1}}{f(x_k) - f(x_{k-1})}.
$$
This avoids explicit computation of \(f'(x)\) while typically converging faster than bisection but slower than Newton’s method.

## Notebook Structure

- Define example functions $f(x)$ that illustrate different behaviors (single root, multiple roots, flat regions, etc.).
- Implement:
  - Bisection method on a user‑specified interval.
  - Newton–Raphson iteration (and optionally the secant method).
- Compare:
  - Number of iterations required to reach a given tolerance.
  - Sensitivity to initial guesses and parameter choices.

## Dependencies

- `numpy`
- `matplotlib` (for plotting functions and iteration progress)

Install (if needed) with:

```bash
pip install numpy matplotlib
```

## How to Run

1. Launch Jupyter from the repository root:
   ```bash
   jupyter lab
   ```
   or
   ```bash
   jupyter notebook
   ```
2. Open `Numerical Analysis/Root_Finding.ipynb`.
3. Run all cells and inspect the printed output and plots.

## Things to Try

- Change the function $f(x)$ to include:
  - Multiple roots.
  - Roots with multiplicity $> 1$ (where Newton’s method slows down).
- Vary initial guesses for Newton’s method and observe when convergence fails.
- Compare the number of function evaluations required by each method to reach the same accuracy.
