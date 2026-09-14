# Truss Structural Analysis using CALFEM (FEM)

A finite element analysis of a 2D pin-jointed (truss) structure, solved using the direct stiffness method via [CALFEM](https://calfem-for-python.readthedocs.io/) in Python. Done as part of the **Computational Methods in Design (CMD)** course, IIT Madras.

## Problem

A planar truss with 12 nodes and 25 bar elements, fixed to a wall at the left end (nodes 1 & 2, fully constrained) and loaded with three point loads:

- **P1 = 15 × 10⁶ N** — downward, at node 5 (0.4, 0.2)
- **P2 = 2 × 10⁶ N** — downward, at node 10 (0.8, 0)
- **P3 = 2 × 10⁶ N** — horizontal, at node 12 (1, 0)

**Geometry:** panel length L = 0.2 m, height H = 0.2 m, spanning 1 m total
**Material:** Cross-sectional area A = 0.2 m², Young's modulus E = 200 GPa

## What the notebook does

1. Loads and displays the problem statement (`Question3.jpg`)
2. Defines element topology (`Edof`) — DOF connectivity for all 25 bar elements
3. Defines global nodal coordinates and DOF numbering (12 nodes, 24 DOFs)
4. Assembles the global stiffness matrix `K` and load vector `f` using `calfem.core.bar2e` and `calfem.core.assem`
5. Applies boundary conditions and solves the system with `calfem.core.solveq`
6. Tabulates nodal displacements (`ux`, `uy`) and support reaction forces (`fx`, `fy`) using `pandas`
7. Plots the original vs. deformed truss geometry (deformation scaled ×20) with `matplotlib`

## Requirements

```
numpy
pandas
matplotlib
Pillow
calfem-python
```

Install with:
```bash
pip install numpy pandas matplotlib pillow calfem-python
```

## Usage

Open `CMD.ipynb` in Jupyter and run all cells top to bottom.

> Note: the first cell loads a local image (`Question3.jpg`) for reference — update the file path or skip that cell if you don't have the image.

## Output

- Displacement table for all 12 nodes
- Reaction force table at the fixed supports
- Plot comparing the undeformed and deformed truss shapes
