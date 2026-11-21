# Hermitian forms bound matrix group torsion

[Chinese proof](../zh/Hermitian%E5%BD%A2%E5%BC%8F%E6%80%8E%E6%A0%B7%E7%BB%99%E7%9F%A9%E9%98%B5%E7%BE%A4%E7%9A%84%E6%89%AD%E7%BB%93%E8%AE%BE%E4%B8%8A%E7%95%8C.md)

## Statement

Let $L$ be totally imaginary of degree $n$ and absolute discriminant $D$. For $e\ge1$, $1\le N\le4e+6$ and $0\le m\le2e+1$, the torsion in $H_m(\mathrm{GL}_N(O_L),\mathbb Z)$ is finite and
$$
\log|\operatorname{Tor}H_m(\mathrm{GL}_N(O_L),\mathbb Z)|
\le \exp\big((2en)^{24}\log(2D)\big).
$$
This is `torsAll`. The [small-index count](assembling-the-small-index-second-cohomology-bound.md) uses `STors` at $N=4e+6$.

## The complex

Use the space $\mathcal H$ of Hermitian matrices at one embedding from each complex conjugate pair. For $0\ne y\in O_L^N$ set $Q_h(y)=\sum_w y_w^*h_w y_w$, and let $\mathcal R$ consist of $h$ satisfying $Q_h(y)\ge1$ for all such $y$. These forms are positive definite at all places. Let $\mathcal P$ be the positive semidefinite cone. A vertex $v$ is determined by its shortest vectors: if $Q_k(y)=0$ for all $y$ with $Q_v(y)=1$, then $k=0$. An ordered $(p+1)$-tuple of vertices, repetitions allowed, is a simplex when a real functional strictly positive on $\mathcal P\setminus\{0\}$ attains its minimum on $\mathcal R$ at each listed vertex. Congruence $g\cdot h=(g^{-1})^* h g^{-1}$ preserves these conditions, and the differential deletes vertices with alternating signs.

For exactness, use the convex nerve theorem in the form that a cover of a nonempty convex space by closed convex sets whose intersections with the hull of any finite collection of points are locally finite has acyclic augmented ordered nerve. Here the space is the open cone of strictly positive functionals and the set for $v$ consists of functionals minimized at $v$. The lemmas `good`, `cone_finite` and `exists_vert` give the cover and the finite hull condition. Thus `sx_exact` supplies the exact permutation complex for the [orbit-and-stabilizer bound](finite-orbits-and-stabilizers-bound-homology-torsion.md).

## Orbit and stabilizer estimates

Set $d=nN$, $I_0=D^N d^d$, and $R_0=N^NI_0^2$. The orbit bound in degree $p$ is
$$
A_p=I_0^{1+dN}\big((2R_0+1)^d+1\big)^{dN(p+1)} .
$$
Indeed `sx_basis` makes the common shortest vectors span $L^N$ by the simultaneous minimum condition. Choose $N$ of them as columns of an invertible $A$ over $L$ with entries in $O_L$. For each vertex $h$, the diagonal entries of $A_w^*h_w A_w$ are at most one, since they are nonnegative and sum over the places to one for each column. Hadamard gives determinant at most one at each place. Their product is $|N_{L/\mathbb Q}\det A|\prod_w\det h_w$. The lattice volume estimate `detlow` gives $\prod_w\det h_w\ge I_0^{-1}$, so the norm of $\det A$ is at most $I_0$. Hermite reduction `hnf` supplies at most $I_0^{1+dN}$ representatives for such $A$ under left multiplication. For a fixed representative, `nearvx` gives at most $((2R_0+1)^d+1)^{dN}$ vertices with its columns as shortest vectors. It bounds the possible shortest vectors by $(2R_0+1)^d$ using inverse matrices and integral coordinates, then specifies a vertex with at most $\dim\mathcal H\le dN$ independent equations. Taking one vertex for each slot gives $A_p$.

A vertex stabilizer acts faithfully by permuting its finite set of shortest vectors, since it contains a basis over $L$. A simplex stabilizer is a subgroup of the first vertex stabilizer. Reduction modulo three is injective on any finite subgroup. In fact if $u=1+3^aX\ne1$ with $a\ge1$ maximal, then powers prime to three leave the first nonzero layer unchanged by binomial expansion. Cubing raises that layer exactly one, because $u^3-1\equiv3^{a+1}X\bmod 3^{a+2}$. Thus no nontrivial element of the congruence kernel can have finite order. The stabilizer size is at most $s=3^{nN^2}$.

## Constants

Use $A=A_m$ since $A_p\le A_m$ in the required degrees. In `orbnum`, with $B=2Dd$, the inequalities $I_0\le B^{2d}$, $N^N\le B^d$, and $2R_0+1\le B^{5d+2}$ give $A\le B^{12(m+1)d^3N}$, using $N\le d$. With $b=m+2$, log torsion is at most $A\log(m+2)+mAs^m\log s$. Put $a=12(m+1)(nN)^3N\log(2DnN)$ and $\sigma=2nN^2$. Then $A\le e^a$, $s\le e^\sigma$, and $\log(m+2)\le m+1$, $\log s\le s$, $2m+1\le e^{2m}$ give log torsion at most $\exp(a+(m+1)\sigma+2m)$.

For $u=en\ge1$, $Y=\log(2D)\ge0.69$, use $nN,N\le10u$, $m+1\le4u$, and $\log(2DnN)\le Y+nN-1\le16uY$. The three terms in the exponent are bounded by $7680000u^6Y$, $1200u^6Y$ and $12u^6Y$, respectively. Their sum is at most $(2u)^{24}Y$, as required.

## Lean correspondence

- [`Sx`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HermiteNormalForms/SmulNeZeroLat.lean#L76), [`sx_exact` and `tors_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HermiteNormalForms/Assembly.lean#L14), and [convex nerve exactness](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ConvexNerveComplexes/NerveConvex.lean) give the complex.
- [`sx_basis` and `orb`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HermiteNormalForms/ColsMinSmul.lean#L13), [`orbnum`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HermiteNormalForms/Orbnum.lean#L80), [determinant bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HermiteNormalForms/DetPull.lean), [`hnf`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HermiteNormalForms/Hnf.lean), and [`nearvx`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HermiteNormalForms/Nearvx.lean) give the orbit count.
- [`stab`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HermiteNormalForms/ImportsAlt.lean), [`mink3`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HermiteNormalForms/Mink3.lean) and [`torsfree`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HermiteNormalForms/Torsfree.lean#L48) bound finite stabilizers.
- [`exponent_le`, `torsAll` and `sTors`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/ExponentLe.lean#L6) give the final quantitative form.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
