# Monte Carlo Simulations of Buffon's Needle 

> **Abstract:** This repository provides a Monte Carlo simulation framework for the classical Buffon's Needle problem. It extends the traditional fixed-length paradigm by investigating the statistical effects of randomized needle lengths (via uniform and normal distributions) on intersection probabilities and the subsequent convergence of pi estimation.

## Table of Contents
* [Overview](#overview)
* [Libraries & Dependencies](#libraries--dependencies)
* [Repository Structure](#repository-structure)
* [Methodology](#methodology)
* [Installation & Usage](#installation--usage)
* [Visualizations](#visualizations)
* [License](#license)

## Overview
Buffon's Needle is a classic problem in geometric probability. This project simulates dropping needles on a lined surface to approximate the value of pi. While standard simulations assume a constant needle length, this repository broadens the scope by evaluating how variance in needle length—sampled from continuous probability distributions—impacts the phase space and overall convergence.

## Libraries & Dependencies
This project is built using standard scientific computing libraries in Python. To run the notebooks, you will need:
* **NumPy**: Used for generating random variables (positions, angles, lengths) and vectorized mathematical operations.
* **Matplotlib**: Used for generating phase space maps, heatmaps, convergence curves, and comparative distribution plots.
* **SciPy**: Specifically `scipy.stats.gaussian_kde` and `scipy.stats.norm`, used to calculate probability density functions for normally distributed needle lengths.

## Repository Structure
* `classical_buffon_needle.ipynb`: A baseline simulation assuming a constant needle length. It includes functions to calculate intersections and plot the phase space and pi convergence curve.
* `random_needle_length.ipynb`: An advanced simulation where the needle length is a random variable. It supports both `uniform` and `normal` distributions and features extended visualizations, including success distribution histograms and phase space heatmaps.

## Methodology



In the classical problem, a needle of length L is dropped onto a plane ruled with parallel lines separated by a distance D (where L $\leq$ D). The position of the needle's center is $x$, and its angle relative to the lines is $\theta$.

The theoretical probability $P$ of the needle crossing a line is given by:

$$P=\frac{2L}{\pi D}$$

By simulating this process over $N$ iterations and calculating the ratio of successful intersections ($P_{sim}$), we can approximate $\pi$:

$$\pi \approx \frac{2L}{D \cdot P_{sim}}$$

For the extended notebook (`random_needle_length.ipynb`), $L$ is treated as a continuous random variable. The theoretical probability is adjusted to utilize the expected value (mean) of the needle length, denoted as $\mu_L$:

$$P=\frac{2\mu_L}{\pi D}$$

## Installation & Usage

1. **Clone the repository:**
   ```bash
   git clone https://github.com/rpoliselit/buffon_s_needle.git
   cd buffon_s_needle
   ```

2. **Install required packages:**
   ```bash
   pip install numpy matplotlib scipy jupyter
   ```

3. **Run the notebooks:**
   Launch Jupyter Notebook or Jupyter Lab and open either `classical_buffon_needle.ipynb` or `random_needle_length.ipynb`.
   ```bash
   jupyter notebook
   ```

**Example execution (from the random length notebook):**
```python
# Simulates 10,000 drops with needle lengths uniformly distributed between 2 and 3. Distance between lines is 5.
monte_carlo_buffon(10000, 2, 3, 5, L_distribution='uniform', charts=True)
```


## Visualizations
The notebooks provide rich visualizations to contextualize the Monte Carlo results:
* **Phase Space Plots**: Highlights the theoretical boundaries of intersection versus the simulated scatter of needle drops.
* **Convergence Curves**: Tracks the estimation of pi as the number of steps $N$ approaches 100,000.
* **Phase Space Heatmaps**: Illustrates the local probability density of successes across the $x$ and $\theta$ parameters.
* **Comparative Distributions**: Overlays the probability density of all generated needle lengths against those that successfully crossed a line.

## License
This project is licensed under the [MIT License](LICENSE) - see the LICENSE file for details.
