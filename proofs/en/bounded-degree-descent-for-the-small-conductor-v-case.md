# Bounded-degree descent for the small-conductor V case

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E5%B0%8F%E4%BA%8C%E8%BF%9B%E5%AF%BC%E5%AD%90%E7%9A%84V%E7%B1%BB%E5%8F%AA%E9%9C%80%E4%B8%8B%E9%99%8D%E5%88%B0%E6%9C%89%E7%95%8C%E6%AC%A1%E6%95%B0%E7%9A%84%E5%9F%9F.md)

## Statement

Fix a primitive Dirichlet character $\chi$ of modulus $Q$ and order $o$. Take a [host](choosing-among-seven-positive-sign-length-estimates.md) $h$ of base character $\chi$ and modulus $N$, and an integer $t$ with $h.\mathrm{Big}(t)$. Choose an algebraic closure of $\mathbb Q$, an odd prime $\ell\in B_\chi$, an allowed finite $\ell$-adic integer ring $O$, and an $O$-valued character $\psi$ modulo $N$ trivial on $H$ and with $\psi(-1)=-1$. Write $c_2=c_2(\psi)$ for the conductor exponent of its two-power component and $n_0=v_2(\ell^{f_0}-1)$ as in the [two-power estimates](two-adic-depths-in-cases-ii-and-iii-have-polynomial-height.md). Assume
$$
2^{c_2}<R_1,\qquad R_1=16o(\ell Q)^2\,4^{n_0}.
$$
Assume global Poitou–Tate duality, local finiteness and local Tate duality, and [`LemmaK` with constant $C_K$](assembling-the-small-index-second-cohomology-bound.md). There is an integer $C$ depending only on $\chi,C_K$ for which the [localization kernel $V_{\ell,1}(\psi)$](cases-ii-and-iii-share-the-rank-four-length-method.md) has finite length and
$$
\frac{\operatorname{length}_O V_{\ell,1}(\psi)}{v_O(\ell)}\log\ell\le(\ell N)^C.
$$
This is `CountVs`.

## Finding the field

Put $b=\max B_\chi$, which is defined since $3\in B_\chi$. The order of the two-primary component divides $2^{c_2}$. At each odd prime power the host conditions make the order divide $o$ or $2$. Consequently $\operatorname{ord}\psi\mid 2o\,2^{c_2}$. Because $2^{n_0}<\ell^{\varphi(4o)}$, the small-conductor bound gives
$$
\ell\operatorname{ord}\psi\le 2o\bigl(16o(bQ)^2 b^{2\varphi(4o)}\bigr)b=:D_0.
$$
This depends only on $\chi$.

In $E=\mathbb Q(\mu_{\ell N})$ take the fixed field $L$ of the common kernel of $\psi$ and the action on $\mu_\ell$. Then $L/\mathbb Q$ is abelian, contains $\mu_\ell$, and kills $\psi_G$ on $G_L$. The degree $d$ is bounded by the product of the orders of the two images, hence $d\le\ell\operatorname{ord}\psi\le D_0$. It is totally imaginary. The cyclotomic discriminant satisfies $|\operatorname{disc}E|\le(\ell N)^{[E:\mathbb Q]}$. The tower formula, with relative discriminant norm at least one, gives $|\operatorname{disc}L|\le(\ell N)^d$.

## Bounding the two contributions to length

On restriction to $G_L$, the coefficient twist becomes cyclotomic of weight $-1$. Inflation–restriction embeds the kernel into the first cohomology of $\operatorname{Gal}(L/\mathbb Q)$ with values in the invariant module. A cocycle is determined by its values on a generating set of at most $D_0$ elements. The invariant estimate in the [restriction-loss argument](../zh/%E9%99%90%E5%88%B6%E5%88%B0%E5%88%86%E5%9C%86%E5%B1%82%E6%97%B6%E4%B8%A2%E5%A4%B1%E7%9A%84%E4%B8%8A%E5%90%8C%E8%B0%83%E6%80%8E%E6%A0%B7%E4%BC%B0%E8%AE%A1.md) bounds the normalized length of the invariant module by $2N$ at weight $1$. Thus the normalized kernel length is at most $2D_0N$.

For the image, base change multiplies $\mathbb Z_\ell$-length by $v_O(\ell)$. The Poitou–Tate comparison `shaLeV` bounds the weight $-1$ localization kernel over $L$ by the $\mathbb Z_\ell$-length of $H^2(G_{L,\{\ell\}},\mathbb Z_\ell(2))$, where ramification is allowed only above $\ell$ and at infinity. Set $K=\lceil C_K\rceil_{\mathbb N}$. `LemmaK` makes this group finite and bounds its log cardinality by
$$
\operatorname{kBound}(K,1,d,|\operatorname{disc}L|)
=\exp\big((2d)^K\log(2|\operatorname{disc}L|)\big).
$$
Log cardinality is length times $\log\ell\ge1/2$. For $X=\ell N\ge2$, the bound on $\operatorname{kBound}$ is at most $X^{(2D_0)^K(D_0+1)}$. Therefore the normalized length is at most $2X^{(2D_0)^K(D_0+1)}+2D_0N$. Multiply by $\log\ell\le X$ and absorb $2(1+D_0)$ into a power of $X$. The exponent $C=(2D_0)^K(D_0+1)+D_0+3$ suffices.

## Lean correspondence

- [`vsOrd`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/PowTotientConductor.lean#L26) bounds the degree needed. [`vsField`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/VsField.lean#L24) constructs $L$.
- [`Win.disc`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LayeredIsomorphisms/Imports.lean#L6) handles the tower discriminant, and [`Chr.upV`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CharacterLevelBounds/LiftGens.lean#L24) compares lengths on restriction.
- [`Win.klen`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LayeredIsomorphisms/Klen.lean#L23) converts cardinality to length. [`countVs`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/CountVs.lean#L86) chooses the exponent.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
