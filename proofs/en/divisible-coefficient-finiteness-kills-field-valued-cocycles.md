# Divisible-coefficient finiteness kills field-valued cocycles

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E7%94%B1%E5%8F%AF%E9%99%A4%E7%B3%BB%E6%95%B0%E7%9A%84%E6%9C%89%E9%99%90%E6%80%A7%E6%B6%88%E5%8E%BB%E5%9F%9F%E7%B3%BB%E6%95%B0%E4%BD%99%E9%97%AD%E9%93%BE.md)

## Statement

Let $k_0$ be a number field, $\ell$ a prime, $\psi:G_{k_0}\to\overline{\mathbb Q}_\ell^\times$ a character with open kernel, $e\ge1$, and $\theta=\psi^{-1}\varepsilon_\ell^{-e}$. Suppose $z:G_{k_0}\to\overline{\mathbb Q}_\ell$ is a continuous $\theta$-cocycle. On every finite inertia group and every decomposition group above $\ell$, suppose it has the form $z(g)=(\theta(g)-1)b$ with an independently chosen local parameter. Under `LemmaK`, global Poitou–Tate duality, local finiteness and local Tate duality, there is one parameter giving this formula everywhere. The result applies to integral tangent classes in the [large-conductor V case](the-large-conductor-v-case-over-the-gaussian-field.md), and the same kind of finiteness and vanishing enter [cases II and III](cases-ii-and-iii-share-the-rank-four-length-method.md).

## A common coefficient field

The finite image of $\psi$ lies in a finite extension $E_0/\mathbb Q_\ell$ which also contains the values of $\theta$. The algebraic closure is a countable union of finite extensions $E_i$, by finiteness of local extensions of each degree up to isomorphism and finiteness of their embeddings. The sets $\{g:z(g)\in E_iE_0\}$ are closed subgroups by continuity, closedness of finite-dimensional subspaces and the cocycle identity. They cover the compact group. Baire gives one with interior, hence an open subgroup. Adjoin the $z$-values of finitely many coset representatives. The cocycle identity now puts all values in a finite extension $E$. Set $O_E$ to be its ring of integers. A local parameter can be taken in $E$ by evaluating at any element with $\theta(g)\ne1$ and dividing, or taking parameter zero when the action is trivial.

## A uniform annihilator and the limit

Set $A=E/O_E$ with action $\theta$, and let $M$ be the corresponding localization kernel in $H^1(G_{k_0},A)$. `soFin` gives finite length. Its argument, as in the [small-conductor restriction comparison](bounded-degree-descent-for-the-small-conductor-v-case.md), takes a finite abelian extension $L/k_0$ killing $\psi$ and containing $\mu_\ell$, or $\mu_4$ when $\ell=2$, so $L$ is totally imaginary. Poitou–Tate and the `LemmaK` bound on second cohomology control the restriction image over $L$. A finite generating set of $\operatorname{Gal}(L/k_0)$ and the invariant submodule over $G_L$ control the restriction kernel. The invariants have finite length since the cyclotomic image on $G_L$ is open and contains an element whose $-e$th power differs from one. Its scalar difference annihilates the invariants. Choose $N_0$ such that $\ell^{N_0}M=0$.

For each $n\ge0$, reduce $\ell^{-(n+N_0)}z$ to $A$. The local coboundary formulas scale too, so it defines a class of $M$. Multiplying by $\ell^{N_0}$ makes the class a coboundary. Lift its parameter from $A$ to $E$ and multiply by $\ell^n$. This gives $b_n\in E$ with
$$
z(g)-(\theta(g)-1)b_n\in\ell^nO_E
$$
for every $g$. If $\theta=1$ the intersection of these ideals already gives $z=0$. Otherwise choose $\theta(g_0)\ne1$ and set $b=z(g_0)/(\theta(g_0)-1)$. At $g_0$ the displayed estimate gives $|b_n-b|_\ell\le|\ell|_\ell^n/|\theta(g_0)-1|_\ell$. Passing to the limit for each $g$ proves $z(g)=(\theta(g)-1)b$. The approximate parameters needed no compatibility assumption.

When $z,\theta$ are valued in a specified integer ring $O$, cross-multiplying at $g_0$ gives $(\theta(g_0)-1)z(g)=(\theta(g)-1)z(g_0)$ in $O$. Thus the integral class is killed by a nonzero scalar.

## Lean correspondence

- [`soFin`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/ExistsAb.lean#L43) gives finiteness by restriction to an abelian extension and `LemmaK`.
- [`soVec` and `core`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/IntIffNorm.lean#L143) supply the uniform congruences and limiting argument.
- [`coc_finext` and `soBar`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/FdAdjoinRange.lean#L27) put values in a finite coefficient field. [`soCoc`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/CobDown.lean#L36) returns to integral coefficients.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
