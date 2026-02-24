# mProject_1 — 2D Random Walk

This folder contains a notebook demonstrating a 2D random walk (the “drunkard’s walk”). It visualizes individual random paths and compares the numerical results with theoretical expectations for diffusion‑like processes.

## Files

- `Random_Walk.ipynb` — Main notebook that:
  - Simulates a 2D random walk.
  - Plots the trajectory in the $x$–$y$ plane.
  - Computes statistics such as the final displacement and its scaling with the number of steps.

## Mathematical Background

In a simple 2D random walk, a particle starts at the origin and takes $N$ steps. At each step $k$,
$$
\Delta \mathbf{r}_k = (\Delta x_k, \Delta y_k)
$$
is a random displacement, often chosen to have zero mean:
$$
\langle \Delta x_k \rangle = 0, \qquad \langle \Delta y_k \rangle = 0.
$$

The position after $N$ steps is
$$
\mathbf{r}_N = \sum_{k=1}^{N} \Delta \mathbf{r}_k,
$$
and the **mean‑squared displacement** obeys
$$
\langle r_N^2 \rangle = \langle \mathbf{r}_N \cdot \mathbf{r}_N \rangle
  \propto N,
$$
so the typical distance from the origin grows like
$$
\sqrt{\langle r_N^2 \rangle} \propto \sqrt{N}.
$$
The notebook verifies this $\sqrt{N}$ scaling numerically.

## How to Run

1. From the repository root, start Jupyter:
   ```bash
   jupyter lab
   ```
   or
   ```bash
   jupyter notebook
   ```
2. Open `mProject_1/Random_Walk.ipynb`.
3. Run all cells to generate sample paths and statistics.

## Dependencies

- `numpy`
- `matplotlib`

Install (if needed) with:

```bash
pip install numpy matplotlib
```

## Things to Try

- Change the number of steps `steps` and observe how the typical displacement scales with $\sqrt{N}$.
- Modify the step distribution (e.g. fixed‑length steps vs. Gaussian steps).
- Run multiple independent walks and compute ensemble averages of $r_N^2$.
