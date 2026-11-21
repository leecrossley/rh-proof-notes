# A weighted explicit-formula sum from log-free zero density

[Chinese proof](../zh/%E9%9B%B6%E7%82%B9%E5%AF%86%E5%BA%A6%E6%80%8E%E6%A0%B7%E5%8F%98%E6%88%90%E6%98%BE%E5%BC%8F%E5%85%AC%E5%BC%8F%E7%9A%84%E5%8A%A0%E6%9D%83%E5%92%8C.md)

Let $Z_\chi(\sigma,T)$ be the zeros of $L(s,\chi)$ with $\sigma\le\Re\rho<1$, $|\Im\rho|\le T$, and let $m_\chi(\rho)$ be their multiplicities. The project calls the set `zerosBox`.

**Proposition.** There are absolute $A,C,\eta_0>0$ such that for $q\ge1$, $T\ge2$, $u\ge(qT)^A$, and $\eta\ge0$,
$$
\sum_{\chi\bmod q}\ \sum_{\substack{\rho\in Z_\chi(1/2,T)\\\Re\rho\le1-\eta}}
m_\chi(\rho)u^{\Re\rho-1}\le C(u^{-\eta/2}+u^{-\eta_0}).
\tag{1}
$$

The [fixed-modulus log-free density theorem](log-free-zero-density-fixed-modulus.md) gives a count of at most $C_1(qT)^{A_1(1-\sigma)}$ with multiplicity, for $1-e_1\le\sigma\le1$ and absolute $C_1,A_1,e_1>0$. For the full box $Z_\chi(1/2,T)$ use a coarser estimate. Each height cell $n=\lfloor\Im\rho\rfloor$ lies in the disk of radius $3$ at $2+in$, so it has total multiplicity $O(\log(q(|n|+2)))$ by the [disk count](high-log-derivatives-from-nearby-zeros.md). There are at most $4T$ cells and $|n|\le T+1$, so each character has $O(qT^2)$ zeros and the sum over characters is at most $C_2(qT)^2$.

Set $e=\min(e_1,1/2)$, $L=\log u$, $M=\log(qT)$, and $A=2A_1+4/e$. Then $L\ge2A_1M$ and $eL\ge4M$. For $d=1-\Re\rho>e$, the total contribution is at most $C_2e^{-Le+2M}\le C_2u^{-e/2}$.

For $\eta\le d\le e$, place the zero in layer $j=\lfloor L(d-\eta)\rfloor\ge0$. The weight is at most $e^{-L\eta-j}$ and $d\le x_j=\min(e,\eta+(j+1)/L)$. The density bound at $\sigma=1-x_j$ bounds the multiplicity in this layer by $C_1e^{A_1Mx_j}$. Because $L\ge2A_1 M$ the layer contributes at most $C_1 e^{1/2}u^{-\eta/2}e^{-j/2}$. Summing the geometric series and adding the far zeros proves (1) with $\eta_0=e/2$. If $\eta>e$ only the far part contributes.

## Lean correspondence

- `mem_disc` and `total_count` give the coarse count. `layers` proves the finite weighted layer bound and `sum_rpow_zeros_le` specializes it to the zeros. [Coarse count](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SumRpowZerosLe.lean#L34) · [Layers](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SumRpowZerosLe.lean#L87) · [Conclusion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SumRpowZerosLe.lean#L124) · [Forwarding theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SumRpowZerosLeStatement.lean#L8)
- `psiAP_relative` uses (1) once the exceptional term has been separated and the remaining zeros have a common real-part gap. [Application](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ChebyshevPsiProgressionRelativeError.lean#L294)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
