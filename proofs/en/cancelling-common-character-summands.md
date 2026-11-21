# Canceling common character summands in two representations

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E5%88%A0%E6%8E%89%E5%90%8C%E4%B8%80%E6%89%B9%E5%AD%97%E7%AC%A6%E5%90%8E%E4%B8%A4%E4%B8%AA%E8%A1%A5%E8%A1%A8%E7%A4%BA%E4%BB%8D%E7%AD%89%E4%BB%B7.md)

**Proposition.** For finite-dimensional $k$-representations $V,W$ of $G$ over a field $k$, and characters $\chi_1,\ldots,\chi_t:G\to k^\times$, possibly repeated, an equivariant isomorphism
$$
V\oplus\bigoplus_j k(\chi_j)\simeq W\oplus\bigoplus_j k(\chi_j)
$$
implies $V\simeq W$ equivariantly. Here $k(\chi)$ is the character line.

It suffices to cancel one line. Let $f:V\oplus k(\chi)\to W\oplus k(\chi)$ be the isomorphism and $e=(0,1)$. If the last coordinate of $f(e)$ is nonzero, put $v_0=0$. Otherwise put $f^{-1}(0,1)=(v_0,\alpha)$. In this case $v_0$ transforms by $\chi$, and $f(v_0,1)$ has last coordinate $1$ because the last coordinate of $f(e)$ is zero. In both cases we have a $\chi$-vector $v_0$ and $f(v_0,1)=(w_0,d)$ with $d\ne0$. The line $k(v_0,1)$ complements $V\oplus0$ and its image $k(w_0,d)$ complements $W\oplus0$. Quotient by these corresponding stable lines. The induced isomorphism takes $v$ to $w-(b/d)w_0$ if $f(v,0)=(w,b)$. Repeat for all $t$ lines. The cancellation only uses the specified direct summands.

At a good point, the [Hecke-polynomial comparison](hecke-polynomials-determine-semisimple-representations.md) gives isomorphism of the full representations over the fraction field. Canceling their common lines gives the intertwining matrix $Q$ between the two complement representations.

## Lean correspondence

- `cancel_one` chooses the vector and `cancel_fin` iterates. `main` writes the resulting isomorphism in the bases of the complements. [One line](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ComplementOfCharactersUniqueUpToConj.lean#L15) · [All lines](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ComplementOfCharactersUniqueUpToConj.lean#L107) · [Application](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ComplementOfCharactersUniqueUpToConj.lean#L191)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
