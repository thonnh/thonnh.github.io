---
layout: default
title: Introduction to PINNs
date: 2025-11-26
---

# Introduction to PINNs
- Accurate for isotropic, incompressible, rubber-like materials under **large defromation**.
- More amicable to mathematical analysis than strain invariant-based model. 
- Considering rubber-like material to be ideally hyperelastic, such that material do not exhibit hysteresis where the stress is only a function of the strain (usually right Cauchy–Green strain tensor) without its strain history.
The strain energy density ($\psi$) in Ogden's model can be expressed as

$$
\psi(\lambda_1, \lambda_2,\lambda_3)=\sum_{i=1}^n{\mu_i\frac{[\lambda_1^{\alpha_i}+\lambda_2^{\alpha_i}+\lambda_3^{\alpha_i}-3]}{\alpha_i}},
$$

where $\lambda_i$ refer to three principal stretches, and $\mu_i$ and $\alpha_i$ are the Ogden material parameters.
The pricipal stretches can be obtained from the spectral decomposition of the Cauchy–Green strain tensor where

$$
\mathbf C = \sum_{\alpha = 1}^3\lambda_\alpha^2(\mathbf r^{(\alpha)} \otimes \mathbf r^{(\alpha)}).
$$

Note that $\mathbf r^{(\alpha)}$ is the normalized eigenvectors where $(\mathbf r^{(1)} \times \mathbf r^{(2)})\cdot\mathbf r^{(3)}=1$ (orthonormal basis).

Once the strain energy density is determined, it yields first Piola–Kirchoff stress tensor as 

$$
\mathbf S = \frac{\partial \psi}{\partial \mathbf F}-p\mathbf F^{-T}
$$
where $p$ is the presssure variable (considering incompressible material).
