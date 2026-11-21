# An integral power-series basis for Frobenius

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88Frobenius%E7%9A%84%E7%B3%BB%E6%95%B0%E5%B1%95%E5%BC%80%E5%8F%AF%E4%BB%A5%E5%9C%A8%E6%95%B4%E5%B9%82%E7%BA%A7%E6%95%B0%E7%8E%AF%E9%87%8C%E5%AE%8C%E6%88%90.md)

**Proposition.** Let $\ell$ be prime and $\mathcal O$ a complete DVR with $0\ne\ell$ in its maximal ideal $(\varpi)$. On $R=\mathcal O[[U]]$ let $\phi$ fix $\mathcal O$ and send $U$ to $(1+U)^\ell-1$. Each $f\in R$ can be uniquely written as $\sum_{j=0}^{\ell-1}(1+U)^j\phi(f_j)$ with $f_j\in R$. In particular $\phi$ is injective.

First define $S,T:R^\ell\to R$ by $S(h)=\sum_jU^j h_j(U^\ell)$ and $T(h)=\sum_jU^j\phi(h_j)$. Grouping coefficients by degree modulo $\ell$ gives a two-sided inverse to $S$. Modulo $\varpi$ the two maps agree because $(1+U)^\ell-1=U^\ell$ in residue characteristic $\ell$. Thus $P=S^{-1}(T-S)$ sends $\varpi^nR^\ell$ into $\varpi^{n+1}R^\ell$. Completeness and separation of $R^\ell$ follow coefficientwise, with congruence to order $n$ meaning all coefficients agree modulo $\varpi^n$. The series $\sum_{n\ge0}(-P)^n$ therefore inverts $1+P$ by multiplying its finite sums and letting the last term vanish. As $T=S(1+P)$, it is an isomorphism. The change from $U^j$ to $(1+U)^j$ is triangular over $\mathcal O$ with diagonal $1$, giving the required expansion.

## Lean correspondence

- `bijective_expand` groups the coefficients and `bijective_of_congr` lifts the mod-$\varpi$ comparison. `phi_free` gives the basis, used by `exists_coords_mem` for Frobenius extension of an ideal. [Coefficient groups](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/PhiFree.lean#L13) · [Basis](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/PhiFree.lean#L123) · [Application](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/XXPowMemOfQQPowMulMemMapPhi.lean#L9)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
