# A common integral lattice for finitely many seed representations

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E6%8A%8A%E6%9C%89%E9%99%90%E7%BB%84%E7%A7%8D%E5%AD%90%E6%94%BE%E8%BF%9B%E5%90%8C%E4%B8%80%E6%95%B4%E7%B3%BB%E6%95%B0%E9%80%BC%E8%BF%91%E6%A0%BC.md)

## Statement

Let $G$ be compact, $r$ a continuous semisimple $a$-dimensional representation over $\overline{\mathbb Q}_\ell$, and $\rho_1,\ldots,\rho_m$ continuous $a$-dimensional seeds. Let $\Lambda$ be the $\mathbb Z_\ell$-span of $r(G)$ and $\Lambda_s$ the simultaneous image of $\mathbb Z_\ell[G]$ in the seed matrices. Over each seed's finite coefficient field take a finite free $\mathbb Z_\ell$-lattice $B_k$ of matrices containing $I$ and stable under left $\rho_k(G)$, and let $B=\prod_k B_k$. Fix $N\ge n\ge0$ and coefficients $c_k$ giving trace approximation on all $G$ of error at most $\ell^{-N-c}$ with $c$ from the [small trace lemma](small-trace-errors-give-integral-lattice-congruences.md). Assume $|\operatorname{tr}(\ell^N X)|_\ell\le\ell^{-n}$ on $\Lambda$.

For all sufficiently large $M$ there is an integral linear $P:\Lambda'_M=\Lambda_s+\ell^M B\to\Lambda$. Modulo $\ell^N$, it takes $\rho_s(H)$ to $r(H)$, is equivariant, surjective and unital. Also
$$
\left|\operatorname{tr}(PX')-\sum_k c_k\operatorname{tr}X'_k\right|_\ell\le\ell^{-n}
\quad(X'\in\Lambda'_M).
$$
Equivariance means $P(\rho_s(g)X')-r(g)PX'\in\ell^N\Lambda$.

## Construction and trace

For the existence of $B_k$, start with the standard integer lattice in the coefficient field and sum all its translates by $\rho_k(g)$. Compactness bounds the sum and it contains the standard lattice, hence is full and stable. Take all columns in this lattice.

By the elementary divisor description of a submodule of a free $\mathbb Z_\ell$-module, some $u\ge0$ gives $\Lambda_s\cap\ell^M B\subseteq\ell^N\Lambda_s$ for $M\ge N+u$. In a basis of $B$ each generator of $\Lambda_s$ is $\ell^{a_j}$ times a basis vector, and $u=\max_j a_j$ suffices. If $\rho_s(H)$ belongs to this intersection, write it as $\ell^N\rho_s(H')$. All seeds kill $H-\ell^NH'$, whose target image is in $\ell^N\Lambda$ by the small trace lemma. Thus $r(H)\in\ell^N\Lambda$.

For $X'=\rho_s(H)+Y$ with $Y\in\ell^M B$, define its image modulo $\ell^N$ to be $r(H)$. The preceding implication gives well-definedness. Equivariance follows by stability and replacing $H$ by $[g]H$. The map is onto because every target element is $r(H)$, and the unit corresponds to $H=[1]$. Choose any lift $P$ using a free basis of $\Lambda'_M$. Then $PX'=r(H)+\ell^N Z$ with $Z\in\Lambda$. The trace difference is
$$
\operatorname{tr}(\ell^N Z)+
\left(\operatorname{tr}r(H)-\sum_k c_k\operatorname{tr}\rho_k(H)\right)
-\sum_k c_k\operatorname{tr}Y_k .
$$
The first term has the assumed bound. The second has the seed approximation bound by integral linearity and the ultrametric inequality. The last is a bounded linear functional on the fixed finite product of lattices times $\ell^M$, so makes an error at most $\ell^{-n}$ for large $M$. The ultrametric inequality gives the result.

At successive precisions retain all older seeds, keep their ambient lattices, and increase $M$. Forgetting the new coordinates sends the later lattice to the earlier one and exactly commutes with group action. Both readout maps on a projected element are congruent to $r(H)$ at the earlier precision since the same $H$ works and the remainder has sufficient divisibility. This gives the [tower of approximations](operator-power-sums-pass-along-the-lattice-tower.md) after choosing bases.

## Lean correspondence

- [`latL`, `latT` and `Carries`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TupMemLatT.lean#L19) define the lattice and map conditions.
- [`layer`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsLatticeLayerCoverBasisModPow.lean#L83) gives $P$ and its trace estimate. [`cover_exists`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CoverExists.lean#L21) chooses the tower and transition matrices.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
