# Trace decomposition and the cyclotomic Tate operator

[Chinese proof](../zh/%E5%88%86%E5%9C%86%E5%A1%94%E4%B8%8A%E7%9A%84%E8%BF%B9%E5%88%86%E8%A7%A3%E6%80%8E%E6%A0%B7%E6%9E%84%E9%80%A0Tate%E7%AE%97%E5%AD%90.md)

## Statement

Let $\ell$ be prime, $K_0/\mathbb Q_\ell$ finite unramified, $K_i=K_0(\mu_{\ell^i})$ and $O_i$ its ring of integers. Let $O_\infty$ be the closure of their union in $\mathbb C_\ell$. For $j\ge1$, define $X_j$ as the closure of finite sums of $X^{(i)}=\sum_{a=1}^{\ell-1}\zeta_i^aO_{i-1}$ for $i>j$, with $\zeta_i$ primitive of order $\ell^i$. Changing the primitive root groups the same powers modulo $\ell$ with unit factors from $O_{i-1}$. Then $O_\infty=O_j\oplus X_j$ and $X_j\cap K_j=0$. If $g$ fixes $K_j$ with $v_\ell(\chi(g)-1)=j$, and $j\ge2$ for $\ell=2$, take $\pi=\zeta-1$ for a primitive $\ell$th root. There is an $O_j$-linear $S:X_j\to X_j$ with
$$
(g-1)Sx=S(g-1)x=\pi x,\qquad |Sx|_\ell\le\ell |x|_\ell.
$$
This is used in [the perturbation argument](weight-differences-annihilate-cyclotomic-coinvariant-torsion.md).

## The integral complement

Take compatible roots. The polynomial $\Phi_{\ell^i}(1+X)$ is Eisenstein over $O_0$, with constant $\ell$ and mod-$\ell$ polynomial $X^{\ell^{i-1}(\ell-1)}$. Thus $\zeta_i-1$ is a uniformizer. For $i\ge2$, $(1+X)^\ell-\zeta_{i-1}$ is Eisenstein over $O_{i-1}$. The first $\ell$ powers of $\zeta_i-1$ give an integral basis because the valuations of the summands in this basis are distinct modulo the relative ramification index. Binomial change of basis gives $1,\zeta_i,\ldots,\zeta_i^{\ell-1}$. The normalized trace $\ell^{-1}\operatorname{Tr}_{K_i/K_{i-1}}$ is identity on $O_{i-1}$ and kills the other powers by the $\ell$th-root sum. Thus it gives the integral splitting at each layer.

Iterating trace gives compatible projections $P_j:O_m\to O_j$ with kernels the sum of the successive complements, commuting with $g$. If $|x|\le\ell^{-k}$, then $\ell^{-k}x$ is integral and so its projection is integral. Hence $|P_jx|\le\ell^{-k}$, giving uniform continuity. Extend by completion. For each limit point $x$, $x-P_j x\in X_j$ by approximation at finite layers. The projection vanishes on $X_j$ and is identity on $O_j$, giving uniqueness and $X_j\cap K_j=0$. Each layer complement is stable under $O_j$ and $g$ by the root power formula, so the closure is stable.

## The operator

On a generating term $x=\zeta_i^a c$, $1\le a<\ell$, $c\in O_{i-1}$, put $b=i-j-1$. The valuation formula gives $v_\ell(\chi(g^{\ell^b})-1)=i-1$. This power fixes $K_{i-1}$ and multiplies $\zeta_i^a$ by a primitive $\ell$th root $\eta$. Thus $\pi/(\eta-1)$ is a unit of $O_1$. Put $z=\zeta_i^a(\pi/(\eta-1))c$ and $y=\sum_{k=0}^{\ell^b-1}g^k z$. This is in $X^{(i)}$ and $(g-1)y=g^{\ell^b}z-z=\pi x$. Sum such solutions. They are unique on the finite-layer complement, because $g$ generates each finite cyclotomic quotient over $K_j$ by the same valuations, so its fixed elements lie in $K_j$. Uniqueness gives linearity and $S(g-1)x=\pi x$ by applying $g-1$ to both sides.

If $|x|\le\ell^{-k}$, then $\ell^{-k}x$ remains in the integral finite-layer complement by trace linearity. The resulting integral solution, scaled back, has norm at most $\ell^{-k}$. Choosing the integer cutoff just above $|x|$ gives $|Sx|\le\ell|x|$. Applied to differences, this extends $S$ to the closed complement, preserving the identities and $O_j$-linearity.

## Lean correspondence

- [`Xlev_form` and the trace decomposition](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TateDecompositionCompletedCyclotomicIntegers.lean#L184), [layer splitting](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TateDecompositionCompletedCyclotomicIntegers.lean#L251) and [completion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TateDecompositionCompletedCyclotomicIntegers.lean#L371) give the direct sum.
- [`gen_root`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsTateOperatorLevelComplement.lean#L185), [`solve_alg`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsTateOperatorLevelComplement.lean#L216), [`est_pow`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsTateOperatorLevelComplement.lean#L296) and [`exists_tate_operator_bound`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsTateOperatorLevelComplement.lean#L405) give the solution and norm.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
