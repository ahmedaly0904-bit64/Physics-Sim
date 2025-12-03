# ⚛️ Computational Physics Simulations

A collection of physics simulations built with **Python**, **NumPy**, and **Matplotlib**.
This repository aims to bridge the gap between theoretical physics equations and visual code simulations.

## 📂 Projects

### 1. 🔭 Projectile Motion Simulator
Simulating projectile trajectories under different gravitational fields.

* **Physics:** Newton's Equations of Motion ($y = v_0t - \frac{1}{2}gt^2$).
* **Highlights:**
    * Comparison between trajectories on **Earth** ($9.81 m/s^2$), **Moon** ($1.62 m/s^2$), and **Jupiter** ($24.79 m/s^2$).
    * Using `NumPy` for vectorized calculations over time arrays.
* **File:** [`Projectile.ipynb`](./Projectile.ipynb)

---

### 2. 🎲 2D Random Walk (The Drunkard's Walk)
Simulating chaotic motion and diffusion phenomena (Brownian Motion).

* **Physics:** Statistical Mechanics & Einstein's Diffusion Law ($Distance \propto \sqrt{N}$).
* **Highlights:**
    * Generating thousands of random steps efficiently without loops (Vectorization).
    * Visualizing the chaotic path using `Matplotlib`.
    * Verifying the theoretical root-mean-square distance.
* **File:** [`Random_Walk.ipynb`](./Random_Walk.ipynb)

## 🛠️ Tech Stack
* **Python 3**
* **NumPy** (Numerical Computing & Arrays)
* **Matplotlib** (Data Visualization)
* **Jupyter Notebook** (Interactive Environment)

---
*Created by [Ahmed Aly] - Student at Aswan University, Faculty of Science.*