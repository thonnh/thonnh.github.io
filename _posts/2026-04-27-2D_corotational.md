---
layout: default
title: 2D Corotational Frame Element Formulation
date: 2026-4-27
---

# 2D Corotational Frame Element Formulation

The Corotational formulation is designed to handle large displacements and rotations by separating Rigid Body Motion from Pure Deformation. By attaching a local frame that moves with the element, we can use linear beam theory for internal force calculations.

1. Kinematics: Mapping Geometry

We track the element from its initial configuration $(L_0, \beta_0)$ to its current configuration $(L, \beta)$ based on the current global nodal coordinates $(x, y)$:

Current Length: $L = \sqrt{(x_2 - x_1)^2 + (y_2 - y_1)^2}$

Current Angle: $\beta = arctan(y_2 - y_1, x_2 - x_1)$

Rigid Body Rotation: $\alpha = \beta - \beta_0$

2. Local Deformation Extraction ($p_l$)

We eliminate rigid body translations and rotations to isolate the "pure" deformations in the local corotated frame:

$$p_l = \begin{bmatrix} u_l \\ \theta_{1l} \\ \theta_{2l} \end{bmatrix} = \begin{bmatrix} L - L_0 \\ \theta_1 - \alpha \\ \theta_2 - \alpha \end{bmatrix}$$

3. Transformation Matrix ($B$)

To relate local variations ($\delta p_l$) to global variations ($\delta p$), we derive the $3 \times 6$ transformation matrix $B$:

$$\delta p_l = B \delta p, \quad B = \begin{bmatrix} r^T \\ \frac{1}{L} z^T + [0, 0, 1, 0, 0, 0] \\ \frac{1}{L} z^T + [0, 0, 0, 0, 0, 1] \end{bmatrix}$$

Where $r = [-c, -s, 0, c, s, 0]^T$ and $z = [s, -c, 0, -s, c, 0]^T$.

4. Equilibrium and Internal Forces ($q_i$)

Using the Principle of Virtual Work, the global internal force vector $q_i$ is obtained by transforming the local forces $q_l$:

$$q_i = B^T q_l$$

Where $q_l = [N, \bar{M}_1, \bar{M}_2]^T$ is calculated using the standard material stiffness $C_l$ in the local frame.

5. The Tangent Stiffness Definition

For the Newton-Raphson solver, we need the Jacobian of the force vector (Tangent Stiffness Matrix, $K_t$). Taking the variation of the force equilibrium yields the relationship between an infinitesimal change in global coordinates and the resulting change in internal forces:

The Tangent Stiffness Definition:


$$\delta q_i = \left[ B^T C_l B + \frac{N}{L}zz^T + \frac{\bar{M}_1 + \bar{M}_2}{L^2}(rz^T + zr^T) \right] \delta p = [K_t] \delta p$$

$K_M = B^T C_l B$ (Material Stiffness): Resistance due to material deformation.

$K_G = \frac{N}{L}zz^T + \frac{\bar{M}_1 + \bar{M}_2}{L^2}(rz^T + zr^T)$ (Geometric Stiffness): Resistance due to geometry change and internal stress.

6. The Newton-Raphson Solver Loop

The theory is implemented into an iterative process to find the equilibrium state ($F_{ext} = F_{int}$):

State Assessment: Compute current $L, \beta, p_l$ and $q_l$ based on current $U$.

Assembly: Form $F_{int} = \sum B^T q_l$ and build the global $K_t$.

Residual Check: Calculate $R = F_{ext} - F_{int}$. If $\|R\| < \text{tolerance}$, exit.

Solve & Update: Solve $K_t \delta p = R$ and update displacement: $U_{new} = U_{old} + \delta p$.

Repeat: Return to step 1 until convergence.

This summary provides the mathematical foundation for the implementation shown in the video below (comparing between Load-Control and Displacement Control)

<div align="center">
  <iframe width="560" height="315" 
    src="https://www.youtube.com/embed/ZwiBlYo-44k" 
    title="YouTube video player" 
    frameborder="0" 
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
    allowfullscreen>
  </iframe>
</div>


