# Logistic Map (Bifurcation Diagram)

This notebook studies the logistic map, a simple nonlinear recurrence that exhibits a rich variety of behaviors—from fixed points to chaos. It constructs a **bifurcation diagram** showing long‑term values of the system as a function of a control parameter.

## Mathematical Model

The logistic map is defined by the iteration
$$
x_{n+1} = r x_n (1 - x_n),
$$
where

- $x_n \in [0,1]$ represents a normalized population at step $n$,
- $r > 0$ is a growth‑rate parameter.

For different values of $r$, the system exhibits:

- **$0 < r < 1$**: Population decays to $x=0$.
- **$1 < r < 3$**: Convergence to a non‑zero fixed point:
  $$
  x^\star = 1 - \frac{1}{r}.
  $$
- **$3 < r \lesssim 3.57$**: Period‑doubling cascade—stable orbits of period $2,4,8,\dots$.
- **$r \gtrsim 3.57$**: Onset of chaos, with windows of periodicity embedded in chaotic regions.

## Bifurcation Diagram

To build the bifurcation diagram, the notebook:

1. Chooses a dense grid of $r$ values in an interval such as $[2.5, 4]$.
2. For each $r$:
   - Iterates the map many times starting from an initial $x_0$.
   - Discards an initial **transient** (e.g. the first 100–1000 steps) to allow the system to settle.
   - Plots the remaining $x_n$ values against the corresponding $r$.

The resulting scatter plot reveals:

- Stable fixed points and periodic orbits as discrete branches.
- Period‑doubling as branches split.
- Chaotic bands where points fill intervals densely.

## Notebook Structure

- Parameter setup (`r` range, number of iterations, transient length).
- Core loop to iterate \(x_{n+1} = r x_n (1 - x_n)\) using `numpy`.
- Plotting routine to produce the bifurcation diagram in `matplotlib`.

## Dependencies

- `numpy`
- `matplotlib`

Install (if needed) with:

```bash
pip install numpy matplotlib
```

## How to Run

1. Start Jupyter from the repository root:
   ```bash
   jupyter lab
   ```
   or
   ```bash
   jupyter notebook
   ```
2. Open `Numerical Analysis/Logistic Map.ipynb`.
3. Run all cells to generate the bifurcation diagram.

## Things to Try

- Increase the resolution in $r$ or the number of iterations to get a smoother diagram.
- Change the initial condition $x_0$ and verify that long‑term behavior in chaotic regions becomes independent of $x_0$.
- Zoom into specific $r$‑intervals to explore self‑similar structure and periodic windows within chaos.
