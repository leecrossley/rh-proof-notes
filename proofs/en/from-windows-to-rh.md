# From window estimates to the Riemann Hypothesis

[Chinese proof](../zh/%E4%BB%8E%E7%AA%97%E5%8F%A3%E4%BC%B0%E8%AE%A1%E5%88%B0%E9%BB%8E%E6%9B%BC%E7%8C%9C%E6%83%B3.md) · [Chinese reading guide](../zh/from-windows-to-rh.md) · [Reading and review status](../../STATUS.md)

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

### Arithmetic conditions that give the window estimate

In the conditional theorem in the Chinese proof, the characters form a fixed finite project layer $\mathcal L$ of primitive characters containing $\mathbf 1$, equipped with the positive weights of that layer and $a_{\mathbf 1}=1$. Fix $\lambda>1$, two loss exponents $e_D,e_L$, and $\varepsilon_1>0$. Suppose that for each $0<\varepsilon<\varepsilon_1$ there are one family $F$ of arithmetic data and a set $W$ of its scales with the following properties.

1. For every real $T$, some $Y\ge T$ satisfies $[Y,Y^\lambda]\subseteq W$.
2. There exist $C,x_E$ such that every candidate of $F$ at every $x\ge x_E$ is compatible with the layer and satisfies the project's explicit-formula and distribution condition `EAtH` with constant $C$. In particular the pertinent log derivatives at $1$ have modulus at most $C\log x$.
3. There exist $K,c_{HH},e_K,x_0$ such that for every $x\in W$ with $x\ge x_0$, at least one candidate satisfies `CoreAtH`. These are the arithmetic identities, coverage and error bounds with loss exponents controlled by $e_D,e_L$. The candidate may depend on $x$.

Fix $\varepsilon$ and such a family. The pointwise lemma `core_gm` uses `EAtH` and `CoreAtH` on the same candidate. It gives a threshold $x_1$ above which $G(x)\le x^{1/2+(e_D+e_L+7)\varepsilon}$. Indeed the underlying arithmetic estimate is $G(x)\le x^a+4o x^{1/2+\varepsilon}$, where $a=1/2+(e_D+e_L+6)\varepsilon$ and $o$ is the layer's integer parameter. The data give $e_D+e_L\ge0$, so for $x\ge1$ the right side is at most $(1+4o)x^a$. For fixed $\varepsilon$, enlarge $x_1$ until $1+4o\le x^\varepsilon$. For any $x\in W$ above $X=\max(x_1,x_0,x_E,1)$, choose a candidate by condition 3 and apply condition 2 to that same candidate. Thus the estimate holds throughout every window from condition 1 with $Y\ge X$, with $B=e_D+e_L+7$ and $\varepsilon_0=\varepsilon_1$. In particular the loss exponents are fixed before making the small-$\varepsilon$ choice in the analytic argument. [Explicit-formula input](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/RamificationFrobenius/TotientGaloisClasses/ExplicitFormulaErrorOfHostConditions.lean) · [Arithmetic input](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/PrimitiveCosets/CoreAtH.lean) · [Assembly of a window family](assembling-a-window-family.md)

## 2. Nonvanishing to the right

If $\zeta(s)=0$ with $\beta=\operatorname{Re}s>1/2$, take $d=\frac12\min(\beta-1/2,1/2)$ and $\theta=1/2+d$. The choice $\varepsilon=\min(\varepsilon_0/2,d/(|B|+1))$ gives $\theta<\min(\beta,1)$ and $1/2+B\varepsilon\le\theta$. The hypothesis gives $G(y)\le y^\theta$ throughout arbitrarily late windows.

Put $g(u)=G(e^u)$. Its Laplace transform $\Phi(z)=\int_0^\infty g(u)e^{-zu}\,du$ is initially defined on $\Re z>2$. The [pole-data lemma](pole-data.md) continues it meromorphically to $\Re z>0$ and puts a simple pole at each zero $\rho$ of any family member with $0<\Re\rho<1$. The common residue factor is $-1/[\rho(\rho-1)]$, and the remaining factor is a positive weighted sum of zero multiplicities. This gives positive residues at real poles. Nonvanishing on $\Re z\ge1$ is supplied separately by the standard nonvanishing theorem, with the zeta pole at $1$ excluded.

Given $\eta>0$ and a lower bound $U_0$, choose a window large enough that $U=\log Y\ge\max(1,U_0)$. On $[U,\lambda U]$ use $R(u)=e^{\theta u}$ as the upper bound for $g(u)$. Then

$$
\int_U^{\lambda U}R(u)e^{-\theta u}\,du=(\lambda-1)U\le e^{\eta U}.
$$

The [Landau window lemma](landau-window.md) shows that the transform has no pole with real part greater than $\theta$. Since the family contains $\mathbf 1$, and $L(s,\mathbf 1)=\zeta(s)$, the assumed zero would give a pole with real part $\beta>\theta$. This is impossible.

## 3. Reflection

The [functional-equation argument](rh-from-right-half-plane.md) now applies. For $\Re s<1/2$ write $\zeta(s)=2^s\pi^{s-1}\Gamma(1-s)\sin(\pi s/2)\zeta(1-s)$. The Gamma factor is finite and nonzero, and a zero of the sine factor on this side would be a negative even integer or $0$. The former are trivial zeros and $\zeta(0)=-1/2$. Thus a nontrivial zero on the left would force a zero at $1-s$ on the right. Every nontrivial zero therefore has real part $1/2$.

## Lean correspondence

`core_gm` converts the pointwise arithmetic bounds into a weighted prime-sum estimate. `level_gm_le_on_family_scales` extends it over the relevant windows. `lemmaL` and `rh_of_right` handle the analytic conclusion. The final Lean statement has no additional mathematical premise. The conditional deduction above uses the stated arithmetic hypotheses. [Pointwise bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/PrimitiveCosets/CoreGm.lean#L12) · [Windows](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/PrimitiveCosets/LevelGmLeOnFamilyScales.lean#L28) · [Landau application](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/lemmaL.lean#L13) · [Reflection](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GammaFactorNonvanishing/RhOfRight.lean#L5) · [Final statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Main.lean#L4)

O’Desky’s [weighted prime-sum note](https://andrewodesky.com/rh/s/bound-G.html) lists the arithmetic inputs used at this interface.
