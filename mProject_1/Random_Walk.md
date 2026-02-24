# Random_Walk.ipynb — 2D Random Walk Simulation

This notebook simulates a two‑dimensional random walk, visualizes individual paths, and compares numerical measurements with theoretical predictions for how the displacement grows with the number of steps.

## Mathematical Model

Consider a particle starting at the origin `r0 = (0, 0)`. At each step `k = 1,…,N`, it takes a random displacement

`Δr_k = (Δx_k, Δy_k),`

often chosen so that

`⟨Δx_k⟩ = 0`, &nbsp; `⟨Δy_k⟩ = 0`,

and the steps are independent and identically distributed.

The position after `N` steps is

`r_N = Σ_{k=1}^N Δr_k.`

For many common step distributions (e.g. symmetric steps on a grid or Gaussian steps), the **mean‑squared displacement** obeys

`⟨r_N²⟩ ∝ N`,

so the typical distance from the origin scales like

`(⟨r_N²⟩)^(1/2) ∝ √N`.

This is a discrete analogue of diffusion.

## What the Notebook Does

- Generates a random walk in 2D using `numpy`:
  - Draws random steps in `x` and `y`.
  - Computes the cumulative sum to obtain `(x_k, y_k)` along the path.
- Plots:
  - The trajectory in the `x–y` plane.
  - Optionally, the distance from the origin as a function of step number.
- Estimates:
  - Final displacement `r_N`.
  - How `r_N` or `r_N²` scales with the number of steps `N`.

## Key Parameters

- `steps` — Total number of time steps `N`.
- (Optionally) Step size distribution or variance.

## Dependencies

- `numpy`
- `matplotlib`

Install (if needed) with:

```bash
pip install numpy matplotlib
```

## How to Run

1. Start Jupyter in the repository root:
   ```bash
   jupyter lab
   ```
   or
   ```bash
   jupyter notebook
   ```
2. Open `mProject_1/Random_Walk.ipynb`.
3. Run all cells.

## Experiments

- Vary `steps` over a wide range and record the final displacement; check that it grows approximately like `√N`.
- Run multiple walks and average \(r_N^2\) over the ensemble to reduce statistical noise.
- Change the step distribution (e.g. biased steps) and observe how the walk drifts in a preferred direction.
