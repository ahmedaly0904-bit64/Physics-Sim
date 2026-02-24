# Projectile.ipynb — 2D Projectile Motion

This notebook illustrates the classical physics of a projectile launched in a uniform gravitational field (no air resistance). It computes trajectories for different launch speeds and angles and compares numerical results with analytical formulas.

## Physical Model

We consider a point mass launched from `(x0, y0)` with initial speed `v0` at an angle `θ` above the horizontal, subject only to constant gravitational acceleration `g` downward.

In component form, the equations of motion are

`d²x/dt² = 0`, &nbsp; `d²y/dt² = −g`.

Integrating with initial conditions `x(0) = x0`, `y(0) = y0` and

`v_x(0) = v0 cos(θ)`, &nbsp; `v_y(0) = v0 sin(θ)`,

gives the analytical trajectory

`x(t) = x0 + v0 cos(θ) · t`

`y(t) = y0 + v0 sin(θ) · t − 0.5 g t²`

For a projectile launched from ground level (`y0 = 0`) and landing back at `y = 0`, the theoretical **range** is

`R = (v0² · sin(2θ)) / g`,

which is maximized at `θ = 45°` in this idealized model.

## Numerical Approach

The notebook typically:

- Discretizes time as `t_i = i · Δt`.
- Updates position and velocity using kinematic relations at each time step:
  - `v_y(i+1) = v_y(i) − g · Δt`
  - `x(i+1)   = x(i)   + v_x · Δt`
  - `y(i+1)   = y(i)   + v_y(i) · Δt`
- Stops integration when the projectile hits the ground again (`y ≤ 0`).

This simple time‑stepping scheme allows you to experiment with non‑analytic scenarios (e.g. later extensions including drag).

## Notebook Structure

- Parameter definitions: `v0`, `θ`, `g`, `Δt`.
- Time‑stepping loop to compute `(x(t), y(t))`.
- Plots of:
  - Trajectory in the `x–y` plane.
  - Optionally, height vs. time or velocity components vs. time.
- Comparisons to analytical formulas for trajectory and range.

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
2. Open `mProject_0/Projectile.ipynb`.
3. Run all cells, then adjust:
   - Initial speed `v0`,
   - Launch angle `θ`,
   - Time step `Δt`,
   to see how the trajectory and numerical accuracy change.

## Things to Try

- Plot trajectories for multiple launch angles on the same figure and compare ranges with the analytical prediction.
- Decrease \(\Delta t\) to see how the numerical trajectory approaches the exact parabolic path.
- As an extension, modify the acceleration to include a simple drag term proportional to velocity and observe how the trajectory changes.
