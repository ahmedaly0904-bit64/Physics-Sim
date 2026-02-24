# Numerical_Integration.ipynb — Numerical Quadrature

This notebook demonstrates how to approximate definite integrals numerically and how the error depends on the step size. The goal is to approximate
\[
I = \int_a^b f(x)\,\mathrm{d}x
\]
when an analytical antiderivative is difficult or impossible to obtain.

## Mathematical Background

### Discretization

We partition the interval \([a,b]\) into \(n\) sub‑intervals of equal width
\[
h = \frac{b-a}{n}, \qquad x_i = a + i h,\; i = 0,\dots,n.
\]
The integral is then approximated by a weighted sum of function values \(f(x_i)\).

### Trapezoidal Rule

The **composite trapezoidal rule** treats each sub‑interval \([x_i, x_{i+1}]\) as a trapezoid:
\[
I \approx T_n =
h\left[\frac{f(x_0) + f(x_n)}{2}
  + \sum_{i=1}^{n-1} f(x_i)\right].
\]
For sufficiently smooth \(f\), the global error behaves like
\[
|I - T_n| = O(h^2),
\]
so halving \(h\) roughly reduces the error by a factor of \(4\).

### Simpson’s Rule

The **composite Simpson rule** fits parabolas through pairs of sub‑intervals (requires \(n\) even):
\[
I \approx S_n = \frac{h}{3}
\left[
  f(x_0) + f(x_n)
  + 4\sum_{\substack{i=1 \\ i\ \text{odd}}}^{n-1} f(x_i)
  + 2\sum_{\substack{i=2 \\ i\ \text{even}}}^{n-2} f(x_i)
\right].
\]
Under similar smoothness assumptions,
\[
|I - S_n| = O(h^4),
\]
so Simpson’s rule converges much faster than the trapezoidal rule as \(h \to 0\).

The notebook numerically confirms these error scalings by comparing against exact integrals for test functions.

## Notebook Structure

- **Define test functions** \(f(x)\) with known analytical integrals.
- **Implement trapezoidal and Simpson rules** using `numpy` arrays.
- **Error study**:
  - Loop over different step counts \(n\).
  - Compute numerical approximations and compare to the exact integral.
  - Plot error vs. \(h\) on log–log scales to estimate convergence rates.

## Dependencies

- `numpy`
- `matplotlib`

Install (if needed) with:

```bash
pip install numpy matplotlib
```

## How to Run

1. Start Jupyter in the repository:
   ```bash
   jupyter lab
   ```
   or
   ```bash
   jupyter notebook
   ```
2. Open `Numerical Analysis/Numerical_Integration.ipynb`.
3. Run all cells sequentially.

## Things to Try

- Replace the default \(f(x)\) with:
  - Highly oscillatory functions (e.g. \(\sin(kx)\) for large \(k\)).
  - Functions with sharp peaks.
- Compare how many sub‑intervals \(n\) are required for each method to reach a desired accuracy.
- Examine how floating‑point round‑off can affect results when \(n\) becomes extremely large.
