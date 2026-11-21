# From window estimates to the Riemann Hypothesis

[中文](../zh/from-windows-to-rh.md) · [Reading and review status](../../STATUS.md)

The arithmetic and geometric part of the Lean proof constructs common data, compares lattice slopes and converts a prime-power count into a bound for a weighted prime sum. The analytic part uses that bound to rule out zeros right of the critical line. This note proves the analytic implication with the window estimate as input.

## 1. The window estimate

Let $J$ be a finite set. For $j\in J$ choose a Dirichlet character $\chi_j$ of positive modulus and a weight $a_j>0$. The only principal character allowed is the character $\mathbf 1$ modulo $1$. Assume it occurs in the family. Write $\Lambda$ for the von Mangoldt function and $\gamma_E$ for Euler's constant. For $y>0$ define

$$
S_\chi(y)=\sum_{1\le n\le y}\Lambda(n)\chi(n)(y/n-1),
\qquad
G_{\mathbf 1}(y)=S_{\mathbf 1}(y)-y\log y+(1+\gamma_E)y.
$$

For a nonprincipal character set $G_\chi(y)=S_\chi(y)+yL'(1,\chi)/L(1,\chi)$. Set $G(y)=\sum_{j\in J}a_j\operatorname{Re}G_{\chi_j}(y)$.

**Proposition.** Suppose there are fixed $\lambda>1$, $B\in\mathbb R$ and $\varepsilon_0>0$ such that for each $0<\varepsilon<\varepsilon_0$ and $T\ge1$ there is $Y\ge T$ with $G(y)\le y^{1/2+B\varepsilon}$ for every $y\in[Y,Y^\lambda]$. Then RH holds. The choice of $Y$ can depend on $\varepsilon$ and $T$.

## 2. Nonvanishing to the right

If $\zeta(s)=0$ with $\beta=\operatorname{Re}s>1/2$, choose $1/2<\theta<\min(\beta,1)$ and then an allowed $\varepsilon$ for which $1/2+B\varepsilon\le\theta$. The hypothesis gives $G(y)\le y^\theta$ throughout arbitrarily late windows.

Put $g(u)=G(e^u)$. The [pole-data lemma](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/poleData.lean#L248) continues the Laplace transform of $g$ to the right half-plane and puts a pole at each zero of any family member in that half-plane. It gives positive residues at real poles. In its residue calculation the common factor at a zero $\rho$ is $-1/[\rho(\rho-1)]$, and the remaining factor is a positive weighted sum of zero multiplicities. A [derivation of that input in Chinese](../zh/pole-data.md) is available.

Given $\eta>0$ and a lower bound $U_0$, choose a window large enough that $U=\log Y\ge\max(1,U_0)$. On $[U,\lambda U]$ use $R(u)=e^{\theta u}$ as the upper bound for $g(u)$. Then

$$
\int_U^{\lambda U}R(u)e^{-\theta u}\,du=(\lambda-1)U\le e^{\eta U}.
$$

The [Landau window lemma](landau-window.md) shows that the transform has no pole with real part greater than $\theta$. Since the family contains $\mathbf 1$, and $L(s,\mathbf 1)=\zeta(s)$, the assumed zero would give a pole with real part $\beta>\theta$. This is impossible.

## 3. Reflection

The [functional-equation argument](rh-from-right-half-plane.md) now applies. A nontrivial zero to the left of the line would force a zero at $1-s$, which lies to its right. Hence every nontrivial zero has real part $1/2$.

## Lean correspondence

`core_gm` converts the pointwise arithmetic bounds into a weighted prime-sum estimate. `level_gm_le_on_family_scales` extends it over the relevant windows. `lemmaL` and `rh_of_right` handle the analytic conclusion. The final Lean statement has no additional mathematical premise. This note starts at the window estimate. [Pointwise bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/PrimitiveCosets/CoreGm.lean#L12) · [Windows](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/PrimitiveCosets/LevelGmLeOnFamilyScales.lean#L28) · [Landau application](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/lemmaL.lean#L13) · [Reflection](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GammaFactorNonvanishing/RhOfRight.lean#L5) · [Final statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Main.lean#L4)

O’Desky’s [weighted prime-sum note](https://andrewodesky.com/rh/s/bound-G.html) lists the arithmetic inputs used at this interface.
