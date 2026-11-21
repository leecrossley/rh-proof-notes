# The Hecke average contracts mean-zero functions

[Chinese proof](../zh/%E9%9B%B6%E5%9D%87%E5%80%BC%E7%9A%84Hecke%E5%B9%B3%E5%9D%87%E4%B8%BA%E4%BB%80%E4%B9%88%E6%94%B6%E7%BC%A9.md)

## Statement

Let $L$ be totally imaginary, $R=O_L$, $\pi$ prime with $|R/(\pi)|\ge25$, and $N\ge3$. Write $G_\infty=\prod_w\mathrm{GL}_N(\mathbb C)$, $S=\prod_w\mathrm{SL}_N(\mathbb C)$, $\Gamma=\mathrm{GL}_N(R)$, and let $D$ be a finite Haar measure fundamental domain in $S$ for $\mathrm{SL}_N(R)$. Let $T$ be the normalized Hecke average at $q_N=\operatorname{diag}(\pi,1,\ldots,1)$. If $f:G_\infty\to\mathbb R$ is continuous, left invariant under $\Gamma$ and the center, and square integrable with mean zero on $D$, then $Tf$ has the same properties and
$$
\int_D(Tf)^2\,d\mu\le (2/5)^2\int_D f^2\,d\mu.
$$
The [invariant-form argument](hecke-iteration-represents-cycle-integrals-by-invariant-forms.md) uses `SGap` with the relaxed constant $3/5$.

## Hecke as a projection

Use the [three lattice groups](three-lattice-stabilizers-give-the-hecke-indices.md) $K_0,K_1,K_2$ in $S$. Choose $q_1\in S$ by multiplying $q_N$ at each place by a complex scalar giving determinant one. Then $D_0=D$ and $D_1=q_1^{-1}D_0$ are domains for $K_0$ and $K_1$ of equal volume, and similarly choose $D_2$. The function $w(x)=f(q_1x)$ is $K_1$-invariant with mean zero on $D_1$ and the same square integral there as $f$ on $D_0$. On $S$ the Hecke average is
$$
v(x)=[K_0:E_{01}]^{-1}\sum_{c\in E_{01}\backslash K_0}w(cx).
$$
Indeed a diagonal element of $J=\Gamma\cap q_N^{-1}\Gamma q_N$ with the same determinant can be removed from any $\Gamma$ representative, leaving one in $K_0$. On $K_0$ the intersection is $E_{01}$. Center invariance replaces $q_N$ by $q_1$. The finite average is continuous on $G_\infty$, preserves center invariance term by term, and preserves $\Gamma$ invariance by permutation of cosets.

On a domain $D_B$ for $B=K_0\cap K_1\cap K_2$, use the Hilbert space of square-integrable $B$-invariant classes. Denote the invariant subspace for $H\supseteq B$ by $W(H)$. By [domain unfolding](two-double-cosets-bound-correlation-by-one-fifth.md) the finite coset average projects orthogonally to $W(H)$. Since $w$ is already $E_{01}$-invariant, $v$ is its projection to $W(K_0)$ by successive averaging. The integral of $v$ on $D_B$ equals that of $w$, which is $[K_1:B]$ times its zero integral on $D_1$.

## Angle and mean zero

Use $W_1=W(E_{01})$, $W_2=W(E_{02})$, $W_3=W(E_{12})$. The [correlation estimate](two-double-cosets-bound-correlation-by-one-fifth.md) gives the pair angle $1/5$ by comparing $E_{01}$ with $E_{02}$ inside $K_0$, $E_{12}$ with $E_{01}$ inside $K_1$, and $E_{12}$ with $E_{02}$ inside $K_2$. The common spaces used are $W(K_0),W(K_1),W(K_2)$, respectively. The double coset and index hypotheses are exactly the three-lattice calculation.

A class in the triple intersection is invariant almost everywhere under each edge group, also on $S$ by countable translations of the domain. $E_{01}$ and $E_{02}$ generate $K_0$ since any element of $E_{02}\setminus E_{01}$ supplies the other double coset. Similarly $E_{12},E_{01}$ generate $K_1$. Their generated group is dense. The almost-everywhere invariance lemma `AEConst` gives that a measurable function on the locally compact second countable group $S$ invariant almost everywhere under each element of a dense subgroup is constant almost everywhere. One can truncate, convolve with compactly supported continuous functions to obtain invariant continuous functions, and use an approximate identity to recover the original function. Thus $v$ is orthogonal to the intersection by mean zero.

Now $v\in W_1\cap W_2$ and $w\in W_1\cap W_3$. The [three-space estimate](three-projections-yield-the-two-fifths-angle.md) gives $|\langle v,w\rangle|\le(2/5)\|v\|\|w\|$. But this inner product is $\|v\|^2$ by projection. The norms on $D_B$ convert to those on $D_0,D_1$ with equal index factors, since these domains have equal volumes and unfold $D_B$. This gives the asserted contraction and transfers the zero mean to $D_0$.

## Lean correspondence

- [`SGap`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/SBridgeAlt.lean#L118), [`sGap_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/SGapOf.lean#L13) and [`sGap_of_parts`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/SGapOfParts.lean) give the contraction and its use with constant $3/5$.
- [`gapAbs_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/PGapAbs.lean#L12) gives the projection comparison, with [almost-everywhere invariance](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/PAEConst.lean#L80).
- [Three groups and density](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/Arith.lean), [index calculations](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/PArith.lean) and [the dense generated group](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/IntegralTransvectionMemSlIntegersConjugateZero.lean) supply the arithmetic input.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
