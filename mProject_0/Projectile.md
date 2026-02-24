# Projectile.ipynb — 2D Projectile Motion

This notebook illustrates the classical physics of a projectile launched in a uniform gravitational field (no air resistance). It computes trajectories for different launch speeds and angles and compares numerical results with analytical formulas.

## Physical Model

We consider a point mass launched from $(x_0, y_0)$ with initial speed $v_0$ at an angle $\theta$ above the horizontal, subject only to constant gravitational acceleration $g$ downward.

In component form, the equations of motion are
$$
\frac{\mathrm{d}^2 x}{\mathrm{d}t^2} = 0, \qquad
\frac{\mathrm{d}^2 y}{\mathrm{d}t^2} = -g.
$$

Integrating with initial conditions $x(0) = x_0$, $y(0) = y_0$ and
$$
v_x(0) = v_0 \cos\theta, \qquad
v_y(0) = v_0 \sin\theta,
$$
gives the analytical trajectory
$$
x(t) = x_0 + v_0 \cos\theta \, t,
$$
$$
y(t) = y_0 + v_0 \sin\theta \, t - \frac{1}{2} g t^2.
$$

For a projectile launched from ground level ($y_0 = 0$) and landing back at $y=0$, the theoretical **range** is
$$
R = \frac{v_0^2 \sin(2\theta)}{g},
$$
which is maximized at $\theta = 45^\circ$ in this idealized model.

## Numerical Approach

The notebook typically:

- Discretizes time as $t_i = i\,\Delta t$.
- Updates position and velocity using kinematic relations at each time step:
  $$
  v_y^{(i+1)} = v_y^{(i)} - g\,\Delta t, \qquad
  x^{(i+1)} = x^{(i)} + v_x\,\Delta t, \qquad
  y^{(i+1)} = y^{(i)} + v_y^{(i)}\,\Delta t.
  $$
- Stops integration when the projectile hits the ground again ($y \le 0$).

This simple time‑stepping scheme allows you to experiment with non‑analytic scenarios (e.g. later extensions including drag).

## Notebook Structure

- Parameter definitions: $v_0$, $\theta$, $g$, $\Delta t$.
- Time‑stepping loop to compute $(x(t), y(t))$.
- Plots of:
  - Trajectory in the $x$–$y$ plane.
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
   - Initial speed $v_0$,
   - Launch angle $\theta$,
   - Time step $\Delta t$,
   to see how the trajectory and numerical accuracy change.

## Things to Try

- Plot trajectories for multiple launch angles on the same figure and compare ranges with the analytical prediction.
- Decrease \(\Delta t\) to see how the numerical trajectory approaches the exact parabolic path.
- As an extension, modify the acceleration to include a simple drag term proportional to velocity and observe how the trajectory changes.
