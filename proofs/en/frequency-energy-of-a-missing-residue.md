# The frequency energy forced by a missing residue class

[Chinese proof](../zh/%E7%BC%BA%E4%B8%80%E4%B8%AA%E5%89%A9%E4%BD%99%E7%B1%BB%E8%87%B3%E5%B0%91%E9%9C%80%E8%A6%81%E5%A4%9A%E5%B0%91%E9%A2%91%E7%8E%87%E8%83%BD%E9%87%8F.md)

Write $e(u)=e^{2\pi i u}$. Let $d\ge1$ be an integer, $S\subseteq\mathbb N$ finite, and $b_m\in\mathbb C$ for $m\in S$. Define $B_r=\sum_{m\in S,\ m\equiv r\bmod d}b_m$ and $F(h)=\sum_{m\in S}b_m e(mh/d)$.

**Orthogonality identity.**
$$
\sum_{h=0}^{d-1}|F(h)|^2=d\sum_{r=0}^{d-1}|B_r|^2.
\tag{1}
$$
Indeed $\sum_{h=0}^{d-1}e(jh/d)=d$ if $d\mid j$ and otherwise zero, by multiplying the geometric sum by $1-e(j/d)$. Group the terms of $F(h)$ by $r$ to get $F(h)=\sum_r B_r e(rh/d)$. After expanding the square and summing over $h$, only the pairs with $d\mid r-s$ contribute. As $0\le r,s<d$, this is exactly $r=s$.

**Missing-class bound.** Let $\ell$ be prime, $c\in\mathbb N$ and suppose every $m\in S$ satisfies $m\not\equiv c\bmod\ell$. Then
$$
\left|\sum_{m\in S}b_m\right|^2
\le(\ell-1)\sum_{h=1}^{\ell-1}\left|\sum_{m\in S}b_m e(mh/\ell)\right|^2 .
\tag{2}
$$
To see the exact deficit, use $d=\ell$ in (1) and let $c_*=c\bmod\ell$, $M=F(0)$. We have $B_{c_*}=0$ and $\sum_{r\ne c_*}B_r=M$. Subtract the zero-frequency term in (1) and complete the squares around $\mu=M/(\ell-1)$:
$$
\sum_{h=1}^{\ell-1}|F(h)|^2
=\ell\sum_r|B_r|^2-|M|^2
=\frac{|M|^2}{\ell-1}+\ell\sum_{r\ne c_*}|B_r-\mu|^2.
$$
Nonnegativity gives (2), with equality precisely when all $\ell-1$ other masses are equal. The calculation works for any integer $\ell\ge2$ and only requires $B_{c_*}=0$.

## Lean correspondence

- `sum_norm_sq_exp_sum_eq_mul_sum_residues` uses the root sum `sum_range_cexp_eq_ite_dvd` to prove (1). [Root sum](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ArithmeticLargeSieveOneResidueClassPerPrime.lean#L255) · [Identity](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ArithmeticLargeSieveOneResidueClassPerPrime.lean#L281)
- `norm_sum_sq_le_pred_mul_of_avoids_class` proves (2) by Cauchy–Schwarz. `norm_sum_sq_le_totient_mul_of_avoids_classes` extends the missing-class estimate to squarefree moduli. [One class](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ArithmeticLargeSieveOneResidueClassPerPrime.lean#L339) · [Squarefree moduli](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ArithmeticLargeSieveOneResidueClassPerPrime.lean#L378)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
