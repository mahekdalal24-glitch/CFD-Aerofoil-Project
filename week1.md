# Week 1 – Research into CFD Fundamentals  

## 1. Introduction  
The first week of my project focused on building a foundational understanding of **Computational Fluid Dynamics (CFD)**. Before attempting simulations in OpenFOAM, it was important to review the physical principles underlying fluid flow and the numerical strategies used to model them. This week’s work covered the **continuity equation**, **Navier–Stokes equations**, **finite discretisation methods**, and an introduction to **turbulence modelling**.  

---

## 2. Continuity Equation  
The continuity equation represents the **conservation of mass** in a control volume. In its differential form:  

\[
\frac{\partial \rho}{\partial t} + \nabla \cdot (\rho \vec{V}) = 0
\]

For incompressible fluids (\(\rho = \text{const}\)):  

\[
\nabla \cdot \vec{V} = 0
\]

This ensures that the net volumetric flow into any control volume equals the net flow out, preventing unphysical sources or sinks of mass. In CFD, this condition is enforced within each mesh cell.  

---

## 3. Navier–Stokes Equations  
The Navier–Stokes equations are the governing equations of fluid motion, derived from **Newton’s second law applied to fluids**. They describe how momentum is transported by convection, diffusion, and external forces:  

\[
\rho \frac{\partial \vec{V}}{\partial t} + \rho (\vec{V} \cdot \nabla)\vec{V} 
= -\nabla p + \mu \nabla^2 \vec{V} + \rho \vec{g}
\]

Where:  
- \(\vec{V}\): velocity vector  
- \(p\): pressure  
- \(\mu\): dynamic viscosity  
- \(\rho \vec{g}\): body forces (e.g., gravity)  

Key terms:  
- **Unsteady acceleration**: \(\frac{\partial \vec{V}}{\partial t}\)  
- **Convective acceleration**: \((\vec{V}\cdot\nabla)\vec{V}\)  
- **Pressure gradient**: \(-\nabla p\)  
- **Viscous diffusion**: \(\mu \nabla^2 \vec{V}\)  
- **External forces**: \(\rho \vec{g}\)  

These nonlinear PDEs are the foundation of CFD. Analytic solutions exist only for simple cases, hence the need for numerical discretisation.  

---

## 4. Numerical Discretisation Methods  
To solve the governing equations numerically, the continuous domain is divided into a mesh of finite cells. Integrals and derivatives are approximated, converting PDEs into algebraic equations.  

### (1) Finite Difference Method (FDM)  
Approximates derivatives using Taylor expansions. For example, a first derivative (forward difference):  

\[
\frac{du}{dx}\bigg|_i \approx \frac{u_{i+1} - u_i}{\Delta x}
\]

Simple, but less suited for irregular geometries.  

---

### (2) Finite Element Method (FEM)  
Uses shape functions within each element to approximate solutions. Very flexible and powerful, but computationally expensive for fluids.  

---

### (3) Finite Volume Method (FVM) – used in OpenFOAM  
The governing equations are integrated over each control volume. Using Gauss’s divergence theorem, volume integrals of divergence terms are converted into surface integrals:  

\[
\int_V \nabla \cdot (\rho \vec{V}) \, dV = \oint_S \rho \vec{V}\cdot \vec{n}\, dS
\]

This expresses conservation laws as **flux balances across cell faces**:  
- Fluxes (mass, momentum, energy) are computed at cell faces.  
- Strict conservation is guaranteed in every cell.  
- Robust for complex geometries like aerofoils.  

The discretised system produces large sparse matrices, which OpenFOAM solves using iterative methods (e.g. conjugate gradient or multigrid).  

---

## 5. Explicit vs Implicit Schemes  

- **Explicit schemes**:  
  - New values are computed directly from old ones.  
  - Simple but limited by stability criteria (e.g. **CFL condition**).  
  - CFL requires \(\Delta t\) small enough that information does not cross more than one cell per step.  
  - Well-suited for highly unsteady flows.  

- **Implicit schemes**:  
  - New values depend on solving coupled equations at each step.  
  - Unconditionally stable for larger time steps.  
  - More computationally intensive per step.  

Most CFD codes (including OpenFOAM) use implicit schemes for steady flows, and explicit for certain transient solvers.  

---

## 6. Grid Convergence & Discretisation Error  
- **Discretisation error** arises from approximating continuous derivatives.  
- The **order of accuracy** (e.g. \(O(\Delta x)\), \(O(\Delta x^2)\)) determines how error shrinks with refinement.  
- **Grid convergence**: refining the mesh until results stabilise within tolerance.  
- Best practice: simulate on multiple meshes and check convergence to ensure reliability.  

---

## 7. Turbulence Modelling  
Turbulent flows are chaotic, 3D, and energy-dissipative. Direct Numerical Simulation (DNS) of turbulence is infeasible for most engineering cases, so CFD uses turbulence models:  

- **RANS (Reynolds-Averaged Navier–Stokes)**:  
  - Models time-averaged turbulence.  
  - Common models:  
    - **k–ε**: \(k\) = turbulent kinetic energy, \(\epsilon\) = dissipation rate.  
      - Robust, widely used, but less accurate near walls.  
    - **k–ω SST**: \(\omega\) = specific dissipation rate.  
      - Combines accuracy near walls with stability in the free stream.  

- **LES (Large Eddy Simulation)**:  
  - Resolves large eddies, models small ones.  
  - More accurate but computationally expensive.  

- **Hybrid methods (e.g. DES)**:  
  - Combine RANS near walls with LES in separated regions.  
  - Balance accuracy and cost.  

For this project, I will begin with the **k–ω SST model** in OpenFOAM, as it is widely used for airfoil and external aerodynamic applications.  

---

## 8. Reflection & Relevance to Project  
- Understanding **continuity** ensures meshes and solvers conserve mass in each cell.  
- The **Navier–Stokes equations** remind me what OpenFOAM is solving behind the scenes: convection, diffusion, and pressure forces.  
- Awareness of **turbulence models** prepares me for making correct solver choices later when simulating flow over the NACA 2412 aerofoil.  
- This theoretical foundation will help me interpret simulation results critically and validate CFD output against physical expectations.  

---
