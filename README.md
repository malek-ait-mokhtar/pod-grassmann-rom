# Parametric Model Order Reduction with POD and Grassmann Manifold Interpolation

This repository contains the numerical work carried out on parametric model order reduction using Proper Orthogonal Decomposition (POD), Galerkin projection, and interpolation on the Grassmann manifold.

The methods are applied to a two-dimensional diffusion equation discretized with finite elements. The diffusion coefficient is then treated as a parameter: POD subspaces are computed at a set of training values and interpolated using the Amsallem–Farhat method to construct reduced models at unseen parameter values.

## Results

For a fixed diffusion coefficient, the POD–Galerkin model reduces the full-order system from **961 to 5 dimensions**, with a mean relative error of **6.52 × 10⁻⁶**.

For the parametric problem, POD subspaces are computed at **7 training parameters** and the interpolation is evaluated at **6 unseen parameters**. The mean Grassmann distance between interpolated and directly constructed POD subspaces is **2.41 × 10⁻⁴**. The interpolated reduced models achieve a mean relative error of **6.996 × 10⁻⁴**, compared with **6.999 × 10⁻⁴** for reduced models constructed directly at the validation parameters.

## Notebooks

### [`diffusion-equation-pod-galerkin.ipynb`](diffusion-equation-pod-galerkin.ipynb)

Construction and validation of the POD–Galerkin reduced-order model:
- finite-element discretization of the diffusion equation;
- snapshot generation and POD basis construction;
- Galerkin projection;
- comparison between the full-order and reduced-order solutions.

### [`amsallem-farhat-interpolation.ipynb`](amsallem-farhat-interpolation.ipynb)

Extension to the parametric problem:
- construction of local POD subspaces at the training parameters;
- interpolation of these subspaces on the Grassmann manifold;
- construction of the interpolated POD–Galerkin models;
- out-of-sample comparison with POD models constructed directly at the target parameters.

## Report

The full mathematical development is available in [`parametric-pod-grassmann-report-french.pdf`](parametric-pod-grassmann-report-french.pdf).

It covers the theoretical formulation of POD and POD–Galerkin reduction, the Riemannian geometry of the Grassmann manifold, the Amsallem–Farhat and IDW-G interpolation methods, and the numerical experiments presented in the notebooks.

## Dependencies

The implementation uses Python, NumPy, SciPy, Matplotlib, FEniCSx/DOLFINx, PETSc and mpi4py.
