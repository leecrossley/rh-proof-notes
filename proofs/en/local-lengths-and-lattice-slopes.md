# How local lengths change mean and maximum lattice slopes

[Chinese proof](../zh/%E5%B1%80%E9%83%A8%E9%95%BF%E5%BA%A6%E6%80%8E%E6%A0%B7%E6%94%B9%E5%8F%98%E6%A0%BC%E7%9A%84%E5%B9%B3%E5%9D%87%E4%B8%8E%E6%9C%80%E5%A4%A7%E6%96%9C%E7%8E%87.md) · [Reading and review status](../../STATUS.md)

The mean slope of a sublattice of full rank depends exactly on its finite index. For a bound on the maximum slope it suffices to know which local ideal multiples contain the sublattice.

## Setting and formulas

Let $K$ be totally imaginary with ring of integers $R$ and $n=[K:\mathbb Q]$. Fix a basis of a finite-dimensional $K$-vector space $V$ and an invertible complex coordinate change at each infinite place. Give the resulting real space the Euclidean metric in real and imaginary coordinates. For a nonzero finitely generated $R$-submodule $A$ of $V$, let $d_A=\dim_K(KA)$, and let $\operatorname{covol} A$ be the Euclidean covolume in its real span. The slope conventions `muDef` and `muMaxDef` are

$$
\mu(A)=-\frac{2\log\operatorname{covol} A}{nd_A}-\log2+\frac{\log|\operatorname{disc}K|}{n},
\qquad
\mu_{\max}(A)=\sup_{0\ne B\subseteq A}\mu(B),
$$

with the supremum over $R$-submodules. For each nonzero prime ideal $\mathfrak p$, write $\lambda_{\mathfrak p}=\log(\mathrm N\mathfrak p)/n$ with $\mathrm N\mathfrak p=|R/\mathfrak p|$. Write $\ell_{\mathfrak p}(Q)$ for the length of $Q_{\mathfrak p}$ over $R_{\mathfrak p}$.

**Mean-slope formula.** If $0\ne N\subseteq M$ have equal $K$-rank $d$, the lengths of $M/N$ are finite and supported on a finite set. For any finite $S$ containing the support,

$$
\mu(N)=\mu(M)-\frac2d\sum_{\mathfrak p\in S}\lambda_{\mathfrak p}\ell_{\mathfrak p}(M/N). \tag{1}
$$

**Maximum-slope bound.** Let $M,N\subseteq V$ be nonzero finitely generated submodules, $I$ a nonzero fractional ideal, and $k_{\mathfrak p}\ge0$ integers supported on a finite set $S$. If $N_{\mathfrak p}\subseteq\mathfrak p^{k_{\mathfrak p}}M_{\mathfrak p}$ at every nonzero prime ideal, then

$$
\mu_{\max}(IN)\le
\mu_{\max}(M)-\frac2n\log\mathrm N(I)-2\sum_{\mathfrak p\in S}\lambda_{\mathfrak p}k_{\mathfrak p}. \tag{2}
$$

## The index from local lengths

Under the hypotheses of (1), $KN=KM$. Clear denominators in expressions for a finite set of generators of $M$ using elements of $N$. Some $0\ne a\in R$ then satisfies $aM\subseteq N$. Thus $M/N$ is finite, being finitely generated over the finite ring $R/aR$.

Let $Q$ be any finite $R$-module and take a composition series. Each simple factor is $R/\mathfrak p$ for a maximal ideal, since any nonzero element generates a simple factor and has maximal annihilator. Cardinalities multiply in short exact sequences. Localizing the series at a nonzero prime ideal $\mathfrak q$ is exact. If $\mathfrak p\ne\mathfrak q$, an element of $\mathfrak p\setminus\mathfrak q$ annihilates $R/\mathfrak p$ and becomes a unit, so the factor vanishes. If $\mathfrak p=\mathfrak q$, the factor localizes to the residue field of length one. Hence $\ell_{\mathfrak q}(Q)$ counts the $\mathfrak q$-factors. It follows that

$$
[M:N]=|M/N|=\prod_{\mathfrak p\in S}(\mathrm N\mathfrak p)^{\ell_{\mathfrak p}(M/N)}. \tag{3}
$$

The two lattices have the same real span. A fundamental domain for $N$ can be obtained from one copy of a fundamental domain for $M$ per coset of $N$ in $M$. Thus $\operatorname{covol}N=[M:N]\operatorname{covol} M$. The ranks over $\mathbb Z$ are both $nd$ and the field constants cancel in the slope difference. This proves (1).

## Multiplying by an ideal

For any lattice $A$ and nonzero integral ideal $J$, $A_{\mathfrak p}$ is free of rank $d_A$ over the discrete valuation ring $R_{\mathfrak p}$. The quotient by $JA_{\mathfrak p}$ has length $d_Av_{\mathfrak p}(J)$. By (3), $[A:JA]=\mathrm N(J)^{d_A}$. For fractional $J$, clear the denominators with $a\ne0$ such that $aJ$ is integral. Compute the covolume of $aJA$ from $A$ using $aJ$, and from $JA$ using the integral ideal $aR$. Multiplicativity of the norm cancels the factor $\mathrm N(aR)^{d_A}$ and gives $\operatorname{covol}(JA)=\mathrm N(J)^{d_A}\operatorname{covol} A$. Thus

$$
\mu(JA)=\mu(A)-\frac2n\log\mathrm N(J).
$$

For any nonzero submodule $B\subseteq JA$, $J^{-1}B\subseteq A$ and $J(J^{-1}B)=B$. Hence $\mu(B)\le\mu_{\max}(A)-(2/n)\log\mathrm N(J)$. Taking the supremum proves the corresponding upper bound for $\mu_{\max}(JA)$.

For (2) take $J=\prod_{\mathfrak p\in S}\mathfrak p^{k_{\mathfrak p}}$. The local hypotheses say $N_{\mathfrak p}\subseteq(JM)_{\mathfrak p}$ at every nonzero prime ideal. They imply $N\subseteq JM$. Indeed, for $x\in N\setminus JM$ the annihilator of its class modulo $JM$ is proper. At a maximal ideal containing the annihilator, no denominator outside that ideal can multiply $x$ into $JM$. This would contradict the local inclusion.

It follows that $IN\subseteq(IJ)M$. Use monotonicity of $\mu_{\max}$ under inclusion, the shift formula with $IJ$, and $\log\mathrm N(J)=\sum_{\mathfrak p\in S}k_{\mathfrak p}\log\mathrm N\mathfrak p$. This proves (2).

## The place-indexed formulas

In the application $N\subseteq M$ has full rank $d$, and the lattice actually used is $IN$ with $I=\prod_w\mathfrak p_w^{-\lfloor e_wg_w\rfloor}$. The input records a ramification index $e_w>0$, a local exponent $g_w$, and a length $L_w$ with $\ell_{\mathfrak p_w}(M/N)=e_wL_w$. With $\lambda_w=e_w\lambda_{\mathfrak p_w}$ and $g'_w=\lfloor e_wg_w\rfloor/e_w$, the mean-slope and ideal-shift formulas give

$$
\mu(IN)=\mu(M)+2\sum_w\lambda_wg'_w-\frac2d\sum_w\lambda_w L_w.
$$

The local inclusions for the maximum slope give $k_w=e_w\tau_w$ for nonnegative integers $\tau_w$. Applying (2) gives

$$
\mu_{\max}(IN)\le\mu_{\max}(M)+2\sum_w\lambda_w(g'_w-\tau_w).
$$

The next step combines these formulas with bounds on the lengths and the rounding error to obtain [the quotient-slope bounds](quotient-slope-bounds.md).

## Lean references and review

- [`lenLoc_eq_lenAt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/PlacesP.lean#L58), [`mu_index_sum`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/PlacesP.lean#L61) and [`index_finsupp`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SizeWindowBrackets/ChainSlopeWindows/ExistsNsmulMem.lean#L616) relate local lengths and the global index. The cardinality calculation also uses `card_eq_prod_locLen`.
- [`le_prod_smul`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/PlacesP.lean#L31) passes from local to global inclusion. `muMaxDef_mono` and `muMaxDef_fractional_le` in [`ExistsNsmulMem.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SizeWindowBrackets/ChainSlopeWindows/ExistsNsmulMem.lean) give monotonicity and the shift for maximum slopes.
- The two place-indexed formulas are [`mu_eq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/PlacesP.lean#L129) and [`muMax_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/PlacesP.lean#L171). The norm of the shift ideal is in [`log_absNorm_Iu`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/AdmissibleParameterJoins/SumLogPrimeFactorsLe.lean#L358). The predicate `LocLe` in [`PrimeDegreeVariant.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/Divisibility/PrimeDegreeVariant.lean) expresses local inclusion by denominators outside the given prime ideal.

English translation draft. The compatibility of the recorded lengths and the actual local inclusions are inputs to the application.
