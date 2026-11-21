# Missing Hodge–Tate weights control approximate invariants

[Chinese proof](../zh/%E7%BC%BA%E5%A4%B1%E7%9A%84Hodge%E2%80%93Tate%E6%9D%83%E6%80%8E%E6%A0%B7%E6%8E%A7%E5%88%B6%E8%BF%91%E4%BC%BC%E4%B8%8D%E5%8F%98%E9%87%8F.md)

## Statement

Use all the data and hypotheses of the [coinvariant estimate](weight-differences-annihilate-cyclotomic-coinvariant-torsion.md), with $i\notin J$, $A=A_i$, and $B$ the closed unit ball in $C^r$. Let $M$ be an additive subgroup with $B\subseteq M$ and $\ell M\subseteq B$. If $A(\sigma)y-y\in M$ for every $\sigma\in G_m$, then $\ell^{2+N}y\in M$, with $N$ of (1) in the coinvariant estimate. This is `prime_pow_smul_mem_of_twistedInvariant_mod_lattice`.

## Integral cocycles

Write $\delta x(\sigma)=A(\sigma)x-x$. First for any twist $i$, let $c:G_m\to B$ be a continuous cocycle with $\ell^k c=\delta x_0$, $x_0\in B$, $k\ge0$. On $H_\infty$, $A$ is the usual coordinatewise Galois action. The integral Tate cohomology theorem kills first cohomology of the unit ball by every element of the cyclotomic integer ring of norm less than one. Use $\ell$ to choose $x_1\in B$ with $\ell c=\delta x_1$ on $H_\infty$. Then $c_1=\ell c-\delta x_1$ vanishes there. Comparing $c_1(hg)=A(h)c_1(g)$ with $c_1(g(g^{-1}hg))=c_1(g)$ shows $c_1(g)$ is fixed by $H_\infty$. Also $x_2=\ell x_0-\ell^k x_1$ has $\ell^k c_1=\delta x_2$, so is fixed there. Tate's fixed-field calculation puts both in $\widehat{\mathcal O}_\infty^r$.

The coinvariant bound yields $z_0$ in that integral ring with $\ell^Nc_1(g)=A(g)z_0-z_0$. The difference $\ell^N c_1-\delta z_0$ vanishes on $g$ and on $H_\infty$. The image of $g$ generates $G_m/H_\infty$ topologically because the cyclotomic image is $1+\ell^m\mathbb Z_\ell$ and $v_\ell(\chi(g)-1)=m$ with the required bound at two. This also follows from the order at each layer by binomial valuations. The zero set of a continuous cocycle is a closed subgroup, so the difference is zero. Expanding gives
$$
\ell^{N+1}c=\delta(z_0+\ell^Nx_1),\qquad z_0+\ell^Nx_1\in B. \tag{2}
$$

## Return to the vector

Use $c(\sigma)=\ell(A(\sigma)y-y)\in B$. It is a continuous cocycle and $\ell^k c=\delta(\ell^{k+1}y)$ with integral parameter for large $k$. By (2) there is $z\in B$ with $\ell^{N+2}y-z$ genuinely fixed. On the Hodge–Tate basis, its coefficients $v_a$ obey $\chi(\sigma)^{i-u_a}\sigma(v_a)=v_a$. All $i-u_a$ are nonzero. Tate's invariant theorem for nonzero cyclotomic weights over any finite local field gives $v_a=0$. Hence $\ell^{N+2}y=z\in B\subseteq M$.

## Lean correspondence

- [`torsion_killed`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CocycleTwistCoboundaryOnBall.lean#L244) proves (2), using the [integral Tate annihilation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CyclotomicTateMaximalIdealKillsFirstCohomologyStatement.lean#L7).
- [`pow_smul_mem_of_invariant_mod`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/PrimePowSmulMemOfTwistedInvariantModLattice.lean#L254), [nonzero-weight vanishing](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TateInvariantsCyclotomicTwist.lean#L54) and [`HTBasis`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/Foundations/HTBasis.lean#L66) give the conclusion.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
