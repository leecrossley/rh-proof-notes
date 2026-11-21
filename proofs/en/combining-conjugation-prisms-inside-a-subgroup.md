# Combining conjugation prisms inside a subgroup

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E6%8A%8A%E4%B8%80%E7%BB%84%E5%85%B1%E8%BD%AD%E6%A3%B1%E6%9F%B1%E7%A7%BB%E5%9B%9E%E5%AD%90%E7%BE%A4.md)

## Statement

Let $A$ be a commutative ring, $C,D,G$ groups, and $H\le G$. Use bar chains with trivial coefficients in $A$. Take $r\ge1$ and an $r$-cycle $z$ on $C$. Fix $\rho:D\to G$ and for a finite index set $I$ take homomorphisms $d_t:C\to D$, coefficients $n_t\in A$, and elements $g_t\in G$. Fix $t_0\in I$. Assume $\sum_t n_t(d_t)_*z$ is a boundary on $D$, each $g_t$ centralizes $\rho d_t(C)$, both $\rho(D)$ and $g_{t_0}^{-1}\rho(D)g_{t_0}$ lie in $H$, and $g_t^{-1}g_{t_0}\in H$ for all $t$. If $\mathcal P_g$ is the prism from the identity to conjugation by $g^{-1}$, there is an $(r+1)$-cycle on $H$ whose image differs from $\sum_t n_t\mathcal P_{g_t}((\rho d_t)_*z)$ by a boundary in $G$. In `CChain`, the [integral lattice construction](building-a-global-cycle-from-a-twisted-principal-divisor.md) uses $G$ allowing denominators and $H$ preserving the integral lattice.

## Prism identities

On homogeneous tuples modulo simultaneous left multiplication take
$$
\mathcal P_g[v_0,\ldots,v_s]
=\sum_{i=0}^s(-1)^i[v_0,\ldots,v_i,v_i g,\ldots,v_s g].
$$
The product simplex prism has paired interior faces and sides $-\mathcal P_g\partial$. The end obtained by right translation, when left multiplied by $g^{-1}$, is the conjugation end. Hence
$$
\partial\mathcal P_g+\mathcal P_g\partial=(\operatorname{Ad}_{g^{-1}})_*-1.
$$
For two steps use $\Delta^s\times\Delta^2$ with layers $v_i,v_ig,v_igg'$. Triangulate by order-preserving paths with product orientation. Internal faces cancel, and on a cycle the sides from $\partial\Delta^s$ cancel. Reading the three edges and left translating the second layer gives, for $\partial u=0$,
$$
\mathcal P_{gg'}u-\mathcal P_gu-\mathcal P_{g'}(\operatorname{Ad}_{g^{-1}})_*u
\quad\text{is a boundary}.
$$
The constructions commute with homomorphisms by their tuple formulas.

## Constructing the cycle

Take $b$ on $D$ with $\partial b=\sum_t n_t(d_t)_*z$. Put $g_\ast=g_{t_0}$, $\rho_H=\rho$ with target $H$, $\sigma_H(d)=g_\ast^{-1}\rho(d)g_\ast$, and $k_t=g_\ast^{-1}g_t\in H$. The centralizer condition gives $k_t^{-1}\sigma_Hd_t(c)k_t=\rho_Hd_t(c)$. Define
$$
y=(\sigma_H)_*b-(\rho_H)_*b+\sum_t n_t\mathcal P_{k_t}((\sigma_Hd_t)_*z).
$$
The first two terms have boundary the difference of the $\sigma_H$ and $\rho_H$ images of the sum of cycles. The prism terms have the opposite boundary by the first identity. Thus $y$ is a cycle on $H$.

In $G$, the first two terms are congruent modulo boundaries to $\mathcal P_{g_\ast}(\rho_*\partial b)$ by the first identity. After inserting $\partial b$, each term pairs with the corresponding $k_t$ prism. The second identity replaces their sum by $\mathcal P_{g_\ast k_t}=\mathcal P_{g_t}$ on that cycle modulo boundaries. This gives the required image class.

## Lean correspondence

- [`CChain`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/LatticeBlockClasses/CBlockValAlt.lean#L9) and [`cChain`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/LatticeBlockClasses/CChain.lean#L8) give the construction.
- [`SPrism` and `SPrismMul`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/LemmaKOfSteps.lean#L28) state the identities, proved in [the prism](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/SPrism.lean) and [prism composition](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/SPrismMul.lean) files. They carry homogeneous chains to inhomogeneous chains and build the composition homotopy by coning.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
