# Shifted residues force simplicity in the lowest alcove

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $k$ be a field of prime characteristic $p$, $N\ge0$, and $\lambda_1\ge\cdots\ge\lambda_N$ a dominant integer weight. Assume
$$
\lambda_i-\lambda_j+j-i\le p\quad(1\le i<j\le N).
$$
If $N>0$, put $\nu_i=\lambda_i-\lambda_N$; for $N=0$ use the empty weight. The induced space is $\nabla_k(\nu)$ in its matrix-polynomial realization, with the row $\mathrm{GL}_N$-action with the determinant twist for $\lambda_N$. It is nonzero. Every $k$-subspace stable under this algebraic group action is zero or the full space. Here stability means stability under all invertible matrices after extending scalars to any commutative $k$-algebra. This distinction matters over finite fields.

### Reading the weight from the trace scalars

Use $c_n(\mu)$ and $r_{ni}$ from [the trace calculation](traces-of-operator-powers-detect-the-highest-weight.md). Put $a_i=\mu_i+N-i$ and $R_i(t)=\sum_{n\ge0}r_{ni}t^n$. The recurrence gives, in $k[[t]]$,
$$
(1-a_it)R_i(t)=1-t\sum_{l>i}R_l(t).
$$
Let $B_i=1-t\sum_{l\ge i}R_l$. Then $(1-a_it)B_i=(1-(a_i+1)t)B_{i+1}$. It follows that
$$
1-t\sum_{n\ge0}c_n(\mu)t^n
=\prod_{i=1}^N\frac{1-(a_i+1)t}{1-a_it}.
$$
All denominators have unit constant term, so this manipulation also holds when a shifted weight is zero in $k$.

If a second weight gives the same trace scalars, write $m,m'$ for the multiplicities of the two lists of shifted weights modulo $p$. Cross multiplication makes the identity a polynomial equality. For $y\in\mathbb F_p^\times$, the multiplicity of the factor $1-yt$ on each side gives
$$
m(y-1)+m'(y)=m'(y-1)+m(y).
$$
Thus $m-m'$ is constant along $0,1,\ldots,p-1$; the equations for $1,\ldots,p-1$ suffice. Since both lists have length $N$, the difference is zero as an integer function.

Suppose the two weights are decreasing nonnegative lists $\mu,\nu$ with $\nu_N=0$, $\mu_1\le \nu_1$ and $\nu_1+N-1\le p$. Then both shifted lists are strictly decreasing in $[0,p]$. If the largest shifted entry of $\nu$ is smaller than $p$, reduction modulo $p$ is injective on both lists. If it is $p$, the shifted list of $\nu$ has both $0$ and $p$, hence residue zero occurs twice. Strict decrease and equality of residue counts force both $0$ and $p$ in the other list as well. In both cases the sorted lists are equal, giving $\mu=\nu$.

### Applying the invariant to submodules

The full dual Weyl space is stable under row substitutions, which commute with the column conditions. For an algebraic-group submodule $M$, apply the stability law to row transpositions, the row transvection over $k[t]$, and the diagonal matrix with independent invertible entries over $k[t_1^{\pm1},\ldots,t_N^{\pm1}]$. Coefficient extraction in the transvection gives the off-diagonal $E_{ab}$; coefficient extraction on the diagonal gives the separate row-weight components. The common determinant twist shifts all diagonal exponents by the same fixed list and only multiplies a transposition by a nonzero scalar. The diagonal $E_{aa}$ preserve $M$ because they act by a scalar on each row-weight component. Therefore the three stability conditions of [the maximal-height argument](maximal-row-height-gives-a-dominant-highest-vector.md) hold for $M$, the full space, and zero.

For any strict inclusion $M_0\subsetneq M_1\subseteq\nabla_k(\nu)$ of such stable subspaces, choose $v\in M_1\setminus M_0$ with dominant weight $\mu$ highest modulo $M_0$. The row-degree bound gives $\mu_1\le\nu_1$. The traces give $C_nv=c_n(\mu)v$ modulo $M_0$ and $C_nv=c_n(\nu)v$ exactly, since $v$ is in the dual Weyl space. Because $v$ has nonzero class in $M_1/M_0$, the two scalars are equal for every $n$. The lowest-alcove condition implies $\nu_1+N-1\le p$ for $N\ge2$; the normalized $N=1$ case also satisfies it. The shifted residues now give $\mu=\nu$. So $v$ is a nonzero multiple of the highest polynomial $h_\nu$, which must belong to $M_1$ and lie outside $M_0$. Applying the same conclusion to $0\subsetneq M$ and $M\subsetneq\nabla_k(\nu)$ proves that both inclusions cannot be strict. The polynomials for $N=0$ are constants and already form a one-dimensional space.

### Lean correspondence

- [`hcVal_generating`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/TraceEPowerHighestWeightValueGeneratingSeries.lean#L78) gives the generating function. The factor argument and the boundary at $p$ are [`multiset_eq_of_series_eq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ResidueMultisetEqOfShiftedSeriesEq.lean#L135) and [`eq_of_shifted_residues_eq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/EqOfDominantWeightsLowestAlcoveLinked.lean#L21).
- [`eq_of_hcVal_eq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/EqWeightsOfTraceEPowerHighestWeightValueEq.lean#L12) combines them.
- [`IsGLSubmodule` and `InducedSimpleLowestAlcove`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/PublishedTheorems/GlobalTheta/WeylDualWeylLatticesAgreeOfLowestAlcove.lean#L13) spell out the quantification over coefficient algebras and the conclusion.
- [`good_of_isGLSubmodule`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/IsRowOperatorStableDualWeylAndGLSubmodules.lean#L35) gives stability. [`hw_mem_of_lt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/HighestWeightVectorMemOfLtStableDualWeyl.lean#L23) proves the strict-inclusion test, and [`inducedSimpleLowestAlcove`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/WeylModuleSimpleClosedLowestAlcove.lean#L33) proves simplicity.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
