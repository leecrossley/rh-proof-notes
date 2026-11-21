# Limit traces retain the polynomial identities of representations

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E6%9E%81%E9%99%90%E8%BF%B9%E4%BB%8D%E6%BB%A1%E8%B6%B3%E6%9C%89%E9%99%90%E7%BB%B4%E8%A1%A8%E7%A4%BA%E7%9A%84%E5%A4%9A%E9%A1%B9%E5%BC%8F%E6%81%92%E7%AD%89%E5%BC%8F.md)

## Statement

Let $G$ be a group, $K=\overline{\mathbb Q}_\ell$, $d\ge0$. If $T:G\to K$ is approximable by traces of $d$-dimensional representations as in [polynomial approximation](constructing-the-limit-trace-from-dense-frobenius-values.md), then `IsPsChar d T` holds. Namely $T(1)=d$, $T(xy)=T(yx)$, and $A_{d+1}(T;g_0,\ldots,g_d)=0$ for all tuples, where $A_0=1$ and
$$
A_{m+1}(T;g_0,\ldots,g_m)
=T(g_0)A_m(T;g_1,\ldots,g_m)
-\sum_{j=1}^m A_m(T;g_1,\ldots,g_0g_j,\ldots,g_m).
$$
In the $j$th summand only the $j$th argument is replaced. No topology on $G$ is required.

## Proof

For a cyclic functional $T$, the recurrence is the sum over permutations $\sigma\in\mathfrak S_m$ of $\operatorname{sgn}(\sigma)$ times the product of $T(g_{i_1}\cdots g_{i_s})$ over the cycles $(i_1\,\cdots\,i_s)$ of $\sigma$. The cycle starting point is immaterial by cyclicity. To see the recurrence, the new index $0$ is either alone, giving the first term, or inserted before its successor $j$. Deleting it in the latter case combines $g_0g_j$ and reverses the permutation sign.

For $T=\operatorname{tr}\rho$, the first two identities are the identity matrix trace and cyclicity of matrix trace. Put $B_i=\rho(g_i)$ on $V=K^d$. The trace of $B_1\otimes\cdots\otimes B_m$ composed with a tensor permutation is the product of cycle traces, by expansion in a tensor basis, using the inverse permutation convention to match order. The alternating sum is therefore the trace against the antisymmetrizer. Its image is alternating tensors and is zero for $m>d$. This gives the third identity for actual traces.

Each identity is the vanishing of an integral polynomial $P$ in the $X_g$. For the chosen seed traces $S$ all $P(S)=0$. Applying polynomial approximation to $P$ gives $|P(T)|_\ell\le\varepsilon$ for every $\varepsilon>0$, hence zero. This is the [input to semisimple reconstruction](recovering-a-semisimple-representation-from-a-pseudocharacter.md).

## Lean correspondence

- [`IsPsChar` and `alt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/NonGaloisDescent/IsPsCharOne.lean#L9) define the identities. [`isPsChar_trace`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/DetSuccEqSubSumUpdateRow.lean#L68) proves the trace case by determinants.
- [`aeval_eq_zero_of_polyApprox` and `isPsChar_of_polyApprox_trc`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/IsPseudoCharacterOfApproximatedByTraces.lean) pass the identities to the target.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
