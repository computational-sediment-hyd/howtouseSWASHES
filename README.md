
# Getting Started with **SWASHES** (Shallow Water Analytic Solutions for Hydraulic and Environmental Studies)


  - [What is SWASHES? (Claude)](#what-is-swashes-claude)
    - [Background and Purpose](#background-and-purpose)
    - [Main Contents](#main-contents)
    - [Features](#features)
    - [Use Cases](#use-cases)
  - [Setting Up SWASHES](#setting-up-swashes)
  - [List of Analytic Solutions in SWASHES](#list-of-analytic-solutions-in-swashes)
  - [Running SWASHES](#running-swashes)
    - [Overview of Arguments](#overview-of-arguments)
    - [Sample Case 1: "Dressler's dam break with friction"](#sample-case-1-dresslers-dam-break-with-friction)
    - [Sample Case 2: "Bedload (Exner) Meyer-Peter \& Müller eq."](#sample-case-2-bedload-exner-meyer-peter--müller-eq)
  - [Summary](#summary)


## What is SWASHES? (Claude)


**SWASHES** (Shallow Water Analytic Solutions for Hydraulic and Environmental Studies) is a **software library and database of analytic (exact) solutions to the shallow water equations** (Saint-Venant equations).

It was developed and released by researchers at INRAE (formerly IRSTEA) in France, led primarily by Olivier Delestre and his group.

**Official website**
https://www.idpoisson.fr/swashes/
(hosted by Institut Denis Poisson, Université d'Orléans)

---

### Background and Purpose

The shallow water equations are the fundamental governing equations used to simulate a wide range of hydraulic and environmental phenomena, including floods, tsunamis, dam-break floods, and river flows. **Verification** of numerical solvers requires analytic solutions that can be compared against numerical results, but these solutions were previously scattered across the literature. SWASHES was created to **consolidate, implement, and distribute** them in a single, unified resource.

---

### Main Contents

The analytic solutions included are broadly classified into the following categories:

- **Dam-break problems**: dry bed, wet bed, 1D and 2D
- **Steady-flow problems**: hydraulic jumps in channels, flow over bed steps, etc.
- **Unsteady problems**: Thacker solution (oscillating water surface over a parabolic basin), etc.
- **Cases with and without friction**: solutions accounting for bed friction such as Manning's law are included
- **Rainfall-runoff problems**: analytic solutions for surface flow driven by rainfall

---

### Features

- Implemented in C++ and Python and released as **open-source** software
    - Source code: https://sourcesup.renater.fr/projects/swashes/
    - Python packages
        - **PyPI**: https://pypi.org/project/swashes/
        - **conda-forge**: https://anaconda.org/conda-forge/swashes
        - **Python API (pySWASHES)** (not recently updated): https://pyswashes.readthedocs.io/en/latest/

- Can be used as a **benchmark reference** by numerical scheme developers to validate their own codes
- Also published academically as: *Delestre et al. (2013), SWASHES: a compilation of shallow water analytic solutions for hydraulic and environmental studies, International Journal for Numerical Methods in Fluids*
    - **Paper (arXiv)**: https://arxiv.org/abs/1110.0288
    - **Paper (Wiley / IJNMF)**: https://onlinelibrary.wiley.com/doi/abs/10.1002/fld.3741
    - **HAL (preprint)**: https://hal.inrae.fr/hal-00628246
    - **INRAE (developer) page**: https://www6.val-de-loire.inrae.fr/ur-sols_eng/Productions/Software/SWASHES

※ Some models are not included in the paper above and require consultation of individual publications.

---

### Use Cases

- Accuracy verification of new numerical schemes (finite volume methods, discontinuous Galerkin methods, etc.)
- Validation of well-balanced schemes (testing the balance between bed slope and friction terms)
- Promoting understanding of the shallow water equations for educational and research purposes

---

SWASHES is widely referenced as a **standard benchmark suite** in the field of hydraulic numerical computation and plays an important role in assessing the reliability of numerical models.

## Setting Up SWASHES

We set up SWASHES using the Python package described above.

The Python environment can be built with Conda using the following command:

```sh
conda create -n pyswashes -c conda-forge jupyterlab matplotlib swashes
```

## List of Analytic Solutions in SWASHES

We refer to the latest documentation v1.05.00 (2025-04-22).

To download:
 - Go to https://sourcesup.renater.fr/projects/swashes/, click the "Docs" tab at the top, then click "doc" in the sidebar and find the latest version.
 - [Direct link](https://sourcesup.renater.fr/docman/view.php/876/21474): use the above if this link is broken.

An overview of the analytic solutions included in the latest version is as follows:

 - **1D**: types 0–9 (inclined plane, bumps, MacDonald, dam break, oscillations, bedload, sluice gates, dam break with step, solute model, mobile rain)
 - **Pseudo-2D (1.5)**: MacDonald-type rectangular and trapezoidal channels
 - **2D**: oscillations, 2D dam, spherical geometry

Details of each analytic solution are shown in the table below.
(Compiled from the manual, though some entries may contain errors.)

<table>
  <thead>
    <tr>
      <th>Dim.</th>
      <th>Type</th>
      <th>Domain</th>
      <th>choice</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>

<!-- DIMENSION 1 -->
<tr><td colspan="5"><strong>DIMENSION = 1 (One-dimensional)</strong></td></tr>

<!-- type 0 -->
<tr>
    <td rowspan="3" align="center">1</td>
    <td rowspan="3">type 0<br>Inclined plane</td>
    <td>domain 1&nbsp;&nbsp;L=10 m</td>
    <td align="center">1</td>
    <td>Supercritical flow</td>
</tr>
<tr>
    <td rowspan="2">domain 2&nbsp;&nbsp;L=20 m</td>
    <td align="center">1</td>
    <td>Transient solution</td>
</tr>
<tr>
    <td align="center">2</td>
    <td>Periodic wave</td>
</tr>

<!-- type 1 -->
<tr>
    <td rowspan="5" align="center">1</td>
    <td rowspan="5">type 1<br>Bumps</td>
    <td rowspan="5">domain 1&nbsp;&nbsp;L=25 m</td>
    <td align="center">1</td>
    <td>Subcritical flow</td>
</tr>
<tr><td align="center">2</td><td>Transcritical flow without shock</td></tr>
<tr><td align="center">3</td><td>Transcritical flow with shock</td></tr>
<tr><td align="center">4</td><td>Lake at rest, immersed bump</td></tr>
<tr><td align="center">5</td><td>Lake at rest, emerged bump</td></tr>

<!-- type 2 -->
<tr>
    <td rowspan="16" align="center">1</td>
    <td rowspan="16">type 2<br>MacDonald</td>
    <td rowspan="8">domain 1&nbsp;&nbsp;L=1000 m<br>(long channel)</td>
    <td align="center">1</td><td>Subcritical flow — Darcy-Weisbach</td>
</tr>
<tr><td align="center">2</td><td>Subcritical flow — Manning</td></tr>
<tr><td align="center">3</td><td>Supercritical flow — Darcy-Weisbach</td></tr>
<tr><td align="center">4</td><td>Supercritical flow — Manning</td></tr>
<tr><td align="center">5</td><td>Sub- to supercritical flow — Darcy-Weisbach</td></tr>
<tr><td align="center">6</td><td>Sub- to supercritical flow — Manning</td></tr>
<tr><td align="center">7</td><td>Super- to subcritical flow — Darcy-Weisbach</td></tr>
<tr><td align="center">8</td><td>Super- to subcritical flow — Manning</td></tr>
<tr>
    <td rowspan="3">domain 2&nbsp;&nbsp;L=100 m<br>(short channel)</td>
    <td align="center">2</td><td>Smooth transition / shock — Manning</td>
</tr>
<tr><td align="center">4</td><td>Supercritical flow — Manning</td></tr>
<tr><td align="center">6</td><td>Sub- to supercritical flow — Manning</td></tr>
<tr>
    <td>domain 3&nbsp;&nbsp;L=5000 m<br>(undulating channel)</td>
    <td align="center">2</td><td>Subcritical flow — Manning</td>
</tr>
<tr>
    <td rowspan="4">domain 4&nbsp;&nbsp;L=1000 m<br>(with rainfall)</td>
    <td align="center">1</td><td>Subcritical flow — Darcy-Weisbach</td>
</tr>
<tr><td align="center">2</td><td>Subcritical flow — Manning</td></tr>
<tr><td align="center">3</td><td>Supercritical flow — Darcy-Weisbach</td></tr>
<tr><td align="center">4</td><td>Supercritical flow — Manning</td></tr>

<!-- type 2 domain 5 -->
<tr>
    <td rowspan="2" align="center">1</td>
    <td rowspan="2">type 2<br>MacDonald</td>
    <td rowspan="2">domain 5&nbsp;&nbsp;L=1000 m<br>(with diffusion)</td>
    <td align="center">1</td><td>Subcritical flow</td>
</tr>
<tr><td align="center">2</td><td>Supercritical flow</td></tr>

<!-- type 3 -->
<tr>
    <td rowspan="5" align="center">1</td>
    <td rowspan="5">type 3<br>Dam breaks</td>
    <td rowspan="3">domain 1&nbsp;&nbsp;L=10 m</td>
    <td align="center">1</td><td>Wet bed, no friction — Stoker solution</td>
</tr>
<tr><td align="center">2</td><td>Dry bed, no friction — Ritter solution</td></tr>
<tr><td align="center">3</td><td>Dry bed, with friction — Dressler solution</td></tr>
<tr>
    <td rowspan="2">domain 2&nbsp;&nbsp;L=20 m</td>
    <td align="center">1</td><td>Self-similar solution, flat bed, laminar friction</td>
</tr>
<tr><td align="center">2</td><td>Self-similar solution, inclined bed, laminar friction</td></tr>

<!-- type 4 -->
<tr>
    <td rowspan="2" align="center">1</td>
    <td rowspan="2">type 4<br>Oscillations</td>
    <td>domain 1&nbsp;&nbsp;L=4 m</td>
    <td align="center">1</td><td>Planar surface in parabola, no friction — Thacker solution</td>
</tr>
<tr>
    <td>domain 2&nbsp;&nbsp;L=10000 m</td>
    <td align="center">1</td><td>Planar surface in parabola, linear friction — Sampson solution</td>
</tr>

<!-- type 5 -->
<tr>
    <td rowspan="2" align="center">1</td>
    <td rowspan="2">type 5<br>Bedload / Exner</td>
    <td rowspan="2">domain 1&nbsp;&nbsp;L=15 m</td>
    <td align="center">1</td><td>Grass formula</td>
</tr>
<tr><td align="center">2</td><td>Meyer-Peter &amp; Müller formula</td></tr>

<!-- type 6 -->
<tr>
    <td rowspan="3" align="center">1</td>
    <td rowspan="3">type 6<br>Sluice gates</td>
    <td rowspan="3">domain 1&nbsp;&nbsp;L=10 m</td>
    <td align="center">1</td><td>Gate opening onto dry bed</td>
</tr>
<tr><td align="center">2</td><td>Wet bed, free flow, low h_right (= 0.01 × gate size)</td></tr>
<tr><td align="center">3</td><td>Wet bed, free flow, h_right = gate size</td></tr>

<!-- type 7 -->
<tr>
    <td align="center">1</td>
    <td>type 7<br>Dam break with step</td>
    <td>domain 1&nbsp;&nbsp;L=20 m</td>
    <td align="center">1</td><td>Dam break over discontinuous topography</td>
</tr>

<!-- type 8 -->
<tr>
    <td rowspan="4" align="center">1</td>
    <td rowspan="4">type 8<br>Solute model</td>
    <td rowspan="4">domain 1&nbsp;&nbsp;L=1000 m</td>
    <td align="center">1</td><td>No decay, initial solute concentration</td>
</tr>
<tr><td align="center">2</td><td>No decay, boundary solute concentration</td></tr>
<tr><td align="center">3</td><td>With decay, initial solute concentration</td></tr>
<tr><td align="center">4</td><td>With decay, boundary solute concentration</td></tr>

<!-- type 9 -->
<tr>
    <td rowspan="3" align="center">1</td>
    <td rowspan="3">type 9<br>Mobile rain</td>
    <td rowspan="3">domain 1&nbsp;&nbsp;L=18000 m</td>
    <td align="center">1</td><td>Rain moving at the same speed as the flow</td>
</tr>
<tr><td align="center">2</td><td>Rain moving slower than the flow</td></tr>
<tr><td align="center">3</td><td>Rain moving faster than the flow</td></tr>

<!-- DIMENSION 1.5 -->
<tr><td colspan="5"><strong>DIMENSION = 1.5 (Pseudo-2D)</strong></td></tr>

<tr>
    <td rowspan="6" align="center">1.5</td>
    <td rowspan="6">type 1<br>MacDonald pseudo-2D</td>
    <td rowspan="4">domain 1<br>Rectangular short channel B1<br>L=200 m</td>
    <td align="center">1</td><td>Subcritical flow</td>
</tr>
<tr><td align="center">2</td><td>Supercritical flow</td></tr>
<tr><td align="center">3</td><td>Smooth transition</td></tr>
<tr><td align="center">4</td><td>Hydraulic jump</td></tr>
<tr>
    <td rowspan="2">domain 2<br>Trapezoidal long channel B2<br>L=400 m</td>
    <td align="center">1</td><td>Subcritical flow</td>
</tr>
<tr><td align="center">2</td><td>Smooth transition / hydraulic jump</td></tr>

<!-- DIMENSION 2 -->
<tr><td colspan="5"><strong>DIMENSION = 2 (Two-dimensional)</strong></td></tr>

<!-- type 1 2D -->
<tr>
    <td rowspan="2" align="center">2</td>
    <td rowspan="2">type 1<br>Oscillations</td>
    <td rowspan="2">domain 1&nbsp;&nbsp;L=l=4 m</td>
    <td align="center">1</td><td>Rotationally symmetric paraboloid — Thacker solution</td>
</tr>
<tr><td align="center">2</td><td>Planar surface in paraboloid — Thacker solution</td></tr>

<!-- type 2 2D -->
<tr>
    <td rowspan="2" align="center">2</td>
    <td rowspan="2">type 2<br>Dam in 2D</td>
    <td>domain 1&nbsp;&nbsp;L=25 m, l=10 m<br>(≥50 points recommended)</td>
    <td align="center">1</td><td>Parabolic-shaped dam</td>
</tr>
<tr>
    <td>domain 2&nbsp;&nbsp;L=10 m, l=10 m<br>(≥20 points recommended)</td>
    <td align="center">1</td><td>Cross-shaped dam with central ring</td>
</tr>

<!-- type 3 2D -->
<tr>
    <td rowspan="2" align="center">2</td>
    <td rowspan="2">type 3<br>Spherical geometry</td>
    <td>domain 1&nbsp;&nbsp;α=0 rad</td>
    <td align="center">1</td><td>Global steady nonlinear zonal geostrophic flow</td>
</tr>
<tr>
    <td>domain 2&nbsp;&nbsp;α=0.406 rad</td>
    <td align="center">1</td><td>Global steady nonlinear zonal geostrophic flow</td>
</tr>

  </tbody>
</table>


## Running SWASHES

### Overview of Arguments

As shown in the table above, most computational conditions for each analytic solution in SWASHES are fixed and cannot be changed. The only parameter the user can modify is the number of spatial divisions (1D: Nx; 2D: Nx, Ny).

At runtime, the conditions from the table above are passed as arguments. Five or six arguments are required:

 - arg1: Dimension
     - 1: One-dimensional (linear flow)
     - 2: Two-dimensional (full planar flow)
     - 1.5: Pseudo-2D (MacDonald's method)
 - arg2: Type
 - arg3: Domain
 - arg4: Choice (computational condition)
 - arg5, 6: Number of cells
     - For 2D cases, also include the number of cells in the y-direction.


### Sample Case 1: "Dressler's dam break with friction"

This is a 1D dam-break problem using the Dressler solution with friction.

The following computational conditions:

 - Domain length: L = 2000 m
 - Initial water depth: hl = 6 m
 - Dam location: x0 = 1000 m
 - Chézy coefficient: C = 40 m^(1/2)/s
 - Simulation time: T = 40 s

are fixed default values and cannot be changed. Only the number of spatial divisions can be modified.

The model arguments, referring to the table above, are as follows:

 - arg1: Dimension = 1
 - arg2: Type = 3 (dam break)
 - arg3: Domain = 1 (L=2000m) ※ The manual contains an error here.
 - arg4: Choice = 3 (Dressler solution)
 - arg5: Number of cells = 20 and 200 (two cases)


The execution commands are as follows:

```sh
swashes 1 3 1 3 20 > sol11.dat

swashes 1 3 1 3 200 > sol12.dat
```

The results, when plotted, look like this:

<img src="https://computational-sediment-hyd.github.io/howtouseSWASHES/calcoutC1.png" width="100%">

### Sample Case 2: "Bedload (Exner) Meyer-Peter & Müller eq."

This case is a bedload transport model accounting for bed variation, using the Meyer-Peter & Müller formula.

The mathematical derivation is highly complex; please refer to:
*Berthon et al. (2012)*, *"An analytical solution of the shallow water system coupled to the Exner equation"*, *Comptes Rendus Mathématique*, vol. 350, no. 3–4, pp. 183–186.

 - DOI: [10.1016/j.crma.2012.01.007](https://doi.org/10.1016/j.crma.2012.01.007)
 - Preprint: https://arxiv.org/abs/1112.1582

and the SWASHES documentation on bedload solutions: https://sourcesup.renater.fr/docman/view.php/876/21533

The main computational conditions are as follows:

 - Domain length: L = 15 m
 - Unit discharge: q = 1 m^2/s
 - Simulation time: T = 7 s

These are fixed default values and cannot be changed.
Many other parameters are also included, and none of them can be modified.
Only the number of spatial divisions can be changed.

The model arguments, referring to the table above, are as follows:

 - arg1: Dimension = 1
 - arg2: Type = 5 (Bedload (Exner))
 - arg3: Domain = 1
 - arg4: Choice = 2 (Meyer-Peter & Müller eq.)
 - arg5: Number of cells = 200


The execution command is as follows:

```sh
swashes 1 5 1 2 200 > sol22.dat
```

The results, when plotted, look like this:

<img src="https://computational-sediment-hyd.github.io/howtouseSWASHES/calcoutC2.png" width="100%">

## Summary

 - The library includes some lesser-known analytic solutions, which I personally found very educational.
 - The inability to modify detailed computational conditions is a drawback, but the ease with which analytic solutions can be obtained is a significant advantage.
 - The computational formulas for each analytic solution are organized in the documentation, making it a useful reference when implementing your own models.
