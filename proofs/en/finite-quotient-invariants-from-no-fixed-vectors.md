# Finite quotient-lattice invariants from the absence of fixed vectors

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E6%B2%A1%E6%9C%89%E5%9B%BA%E5%AE%9A%E5%90%91%E9%87%8F%E5%B0%B1%E8%83%BD%E6%8E%A7%E5%88%B6%E5%95%86%E6%A0%BC%E7%9A%84%E4%B8%8D%E5%8F%98%E9%87%8F%E9%95%BF%E5%BA%A6.md)

**Proposition.** Let $\mathcal O$ be a discrete valuation ring, $K$ its fraction field, and $A:\Gamma\to\mathrm{GL}_r(\mathcal O)$ a representation of any group with $r\ge0$. If $(\mathcal O^r)^\Gamma=0$, then some nonzero $c\in\mathcal O$ satisfies
$$
(K^r/\mathcal O^r)^\Gamma\subseteq c^{-1}\mathcal O^r/\mathcal O^r\simeq(\mathcal O/c\mathcal O)^r.
$$
In particular the invariant submodule has length at most $r\operatorname{ord}_{\mathcal O}(c)$ with the valuation normalized at a uniformizer.

A nonzero fixed vector of $K^r$ would give one in $\mathcal O^r$ by clearing denominators. Hence the intersection of the kernels of $A(g)-I$ on $K^r$ over $g\in\Gamma$ is zero. A finite subcollection suffices: whenever the intersection so far is nonzero, take a nonzero vector in it and choose some $g$ whose kernel fails to contain that vector. This lowers the dimension, and at most $r$ such choices give zero. Thus for some $g_1,\ldots,g_m$ the map $B:v\mapsto((A(g_j)-I)v)_j$ is injective. Take a $K$-linear left inverse $P$ and clear its denominators with $c\ne0$ so that $cP$ has entries in $\mathcal O$.

If $v+\mathcal O^r$ is invariant, all $(A(g_j)-I)v$ are in $\mathcal O^r$, so $cv=(cP)Bv$ is integral. Multiplication by $c$ on the indicated submodule gives its isomorphism with $(\mathcal O/c\mathcal O)^r$. Filtration by powers of a uniformizer gives the length bound. For $r=0$ one may take $c=1$.

In the lattice-index argument $\Gamma$ is the decomposition group at $w\mid\ell$. The large block at the good point, with its specified one-dimensional twist, acts by `WpO` on $\mathcal O^r$ and by `WKO` on the quotient. The condition `admG2` asserts vanishing of $H^0$ for the corresponding local representation after the given coefficient extension. A fixed integral vector remains fixed under the local group after mapping its coordinates to that field, where it must be zero. Injectivity of the field embedding gives the required vanishing on $\mathcal O^r$. Thus the column invariant length is finite.

## Lean correspondence

- `fix_frac_zero`, `exists_finset_ker` and `exists_killer` give the field version, finite intersection and scalar annihilator. `length_invariants_lt_top` and `GlobalTheory.FiniteTwistInvariants.main` give the length assertion. [Proof](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/LengthInvariantsLtTop.lean)
- `GlobalTheory.SelmerBoundAtPoint.finCore` uses this with the one-dimensional negative-twist result. [Application](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/SelmerLengthBoundAtPoint.lean#L15)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
