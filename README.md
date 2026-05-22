# Anisotropic Diffusion Filtering for MRI Image Denoising

This project implements anisotropic diffusion filtering for MRI image denoising using PDE-based numerical methods. Both steady-state and time-dependent formulations are investigated using finite difference, finite volume, nonlinear iteration, and time integration methods for linear and nonlinear diffusion models. This project was developed as part of the Numerical Methods 2 course at TU Delft.

## Problem

The diffusion-reaction equation considered is

$$
\frac{\partial \phi}{\partial t} = \nabla \cdot (c \nabla \phi) + \lambda (\phi_0-\phi), \quad \text{in } \Omega,
$$

$$
\phi(x,y,0) = \phi_0(x,y), \quad \text{in } \Omega,
$$

$$
c \frac{\partial \phi}{\partial \mathbf{n}} = 0, \quad \text{on } \partial \Omega.
$$

where $\phi$ represents the filtered image, $\phi_0$ the original image, $\lambda$ the fidelity parameter controlling confidence in the original image, and $c>0$ is the diffusion coefficient, defined either as

$$
c = 1
$$

or

$$
c(||\nabla \phi||)=
\frac{1}{1+\left(\frac{||\nabla\phi||}{K}\right)^2}.
$$

The nonlinear diffusion coefficient reduces smoothing near sharp gradients, allowing edges in the image to be preserved while noise is removed in smoother regions.

The computational domain is given by $(x,y)\in\Omega=(0,1)^2$ and discretized using a uniform grid with mesh size

$$
h=\frac{1}{N}.
$$

## Implemented Methods
- Finite Difference Method (FDM)
- Finite Volume Method (FVM)
- Picard iteration for nonlinear steady-state problems
- Forward Euler time integration
- Backward Euler time integration

## Results

The notebook contains:

- denoised MRI reconstructions
- comparisons between isotropic and anisotropic diffusion
- steady-state filtering experiments
- transient diffusion simulations
- visualization of denoising performance

The experiments demonstrate how anisotropic diffusion filtering can effectively reduce noise while preserving important image edges.

## Running the Project

The project was developed and tested using Python 3.12. Install the required packages: pip install -r requirements.txt

Open the notebook:

jupyter notebook notebooks/anisotropic-diffusion-filtering.ipynb

Run all cells sequentially to reproduce the denoising experiments, figures, and time integration results.

Before running the notebook, ensure that the file `SL_simulated.gif` is located in the same directory as the notebook, since it is used as input for the MRI denoising experiments.
