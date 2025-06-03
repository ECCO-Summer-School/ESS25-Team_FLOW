# First Learn tO Walk (FLOW) ![flow_logo](https://github.com/user-attachments/assets/18df64de-6f91-4836-b0af-e913002029f6) 

## Project Overview

This project explores state estimation in climate systems using the Budyko-Sellers one-dimensional energy balance model (EBM) and its adjoint, generated through automatic differentiation (AD). Our main goal is to recover realistic control parameters (e.g., albedo, diffusivity) from noisy data, leveraging gradient-based optimization methods.

We build on the [Budyko Sellers model](https://github.com/Shreyas911/ESS25_AD) provided by Shreyas Gaikwad and Ian Fenty in Fortran, and have developed two tutorial notebooks that explore the implementation and performance of three gradient descent algorithms. We pay particular attention to how the number and scaling of control parameters affect the final state estimate.

---

## Budyko-Sellers Model Equations

The Budyko-Sellers model is a 1D energy balance model (EBM) for Earth's climate, describing the evolution of zonal mean surface temperature ($T(\phi)$) as a function of latitude ($\phi$):

$$
 \frac{\partial E(\phi,t)}{\partial t} = Q(1-\alpha) - \epsilon \sigma T^4 + \frac{D}{\cos{\phi}} \frac{\partial}{\partial\phi}(\cos{\phi}\frac{\partial T}{\partial \phi}),
$$

where:
- $ Q(\phi) $: Incoming solar radiation (insolation)
- $\alpha(\phi) $: Albedo, a function of latitude
- $\sigma$: Stefan-Boltzmann constant
- $\epsilon$: emissivity
- $D$: Diffusion coefficient (meridional heat transport)

Our forward model numerically solves these equations to simulate equilibrium temperature profiles given a set of physical parameters. The adjoint model allows us to compute gradients with respect to control parameters, enabling efficient optimization and state estimation.

---

## Collaborators

| Name                   | Personal goals                                                                  | Can help with                                        | Role                |
|------------------------|--------------------------------------------------------------------------------|------------------------------------------------------|---------------------|
| Noah Rosenberg         |  I want to learn specific python libraries for working with these data         | Understanding our dataset, programming in R          | Project Lead        |
| Karina Ramos Musalem   | I want to understand the optimization process and different components that go into a state estimate calculation | Programming in Python, understanding the model  | Project Lead        |
| Shreyas Gaikwad        |                               |            | Project collaborator|
| Ian Fenty              |                                         |                       | Project collaborator|

---

## Data and Methods

### Data

Our primary dataset is the NCEP reanalysis zonal mean surface temperature, providing realistic climate targets for state estimation experiments.

### Existing Methods

Traditionally, parameter estimation in EBMs relies on manual tuning or simple statistical approaches. Adjoint-based methods, while common in large-scale models, are less frequently applied to simple climate models but offer both opportunities to learn and illustrate these methods and useful gradient information for optimization.

### Proposed Methods/Tools

We implement an adjoint-based optimization using three gradient descent methods in python. The project also explores sensitivity to the number and type of control parameters, and the effect of control scaling. 

### Additional Resources or Background Reading

- ["Lecture 14: The one-dimensional energy balance model"](https://www.atmos.albany.edu/facstaff/brose/classes/ATM623_Spring2015/Notes/Lectures/Lecture14%20--%20Diffusive%20energy%20balance%20model.html) by Brian E. J. Rose (University at Albany)
- [Original Budyko-Sellers model repository](https://github.com/Shreyas911/ESS25_AD)

---

## Project Goals and Tasks

### Project Goals

* Demonstrate adjoint-based state estimation with a 1D EBM.
* Evaluate gradient descent methods for parameter recovery.
* Assess effects of control parameter choices and scaling.
* Create reproducible tutorial notebooks for other students.

### Tasks

* Model experiments: Implement and test gradient descent algorithms in tutorial notebooks
  * Task 2a: Parameter tuning in Python (assigned to Karina)
  * Task 2b: Implementation of gradient descent methods (assigned to Noah)
* Documentation: Write up results, methods, and lessons learned

---

## Project Results

We developed two tutorial notebooks:

1. **Gradient Descent Optimization** – Demonstrates parameter recovery with different algorithms and control settings.
2. **Sensitivity Analysis** – Explores the impact of control parameter scaling and selection.

These resources are available in the [notebooks](notebooks/) folder. Our results show that adjoint-based optimization can recover key climate parameters, but the outcome is very sensitive to the choice and scaling of controls.
