# Restricting the truncated explicit formula to the right half

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E6%8A%8A%E6%88%AA%E6%96%AD%E6%98%BE%E5%BC%8F%E5%85%AC%E5%BC%8F%E9%99%90%E5%88%B6%E5%88%B0%E5%8F%B3%E5%8D%8A%E7%9F%A9%E5%BD%A2.md)

For any character $\chi$ modulo $q\ge1$, let $\Psi_\chi(u)=\sum_{n\le u}\Lambda(n)\chi(n)$, and let $Z_\chi(\sigma,T)$ be the zeros of $L(s,\chi)$ with $\sigma\le\Re\rho<1$ and $|\Im\rho|\le T$. This set is `zerosBox`. Write $m_\chi(\rho)$ for the analytic multiplicity.

**Proposition.** There is an absolute $C>0$ such that for every such $q,\chi$ and $2\le T\le u$, the set $Z_\chi(1/2,T)$ is finite and
$$
\left|\Psi_\chi(u)-\mathbf1_{\chi=\chi_0}u+
\sum_{\rho\in Z_\chi(1/2,T)}m_\chi(\rho)\frac{u^\rho}{\rho}\right|
\le C(u/T+\sqrt u\,q^3)\log^2(quT).
\tag{1}
$$

## The reciprocal sum for primitive characters

First assume $\chi$ primitive and write $W_\chi(T)$ for the zero window with $0<\Re\rho<1$, $|\Im\rho|\le T$. The unit-window disk estimate gives at most $C_1\log(q(|v|+2))$ zeros with multiplicity in $0<\Re\rho<1$, $|\Im\rho-v|\le1$. Thus $W_\chi(T)$ is finite. For $1<|\Im\rho|\le T$, group each sign of the height by $k=\lfloor|\Im\rho|\rfloor\ge1$ and use $|\rho|\ge k$. Summing over the windows at heights $\pm k$ gives
$$
\sum_{\rho\in W_\chi(T),\ |\Im\rho|>1}\frac{m_\chi(\rho)}{|\rho|}
\le 2C_1\log(q(T+2))(1+\log T)\ll\log^2(qT).
$$
For a zero at height at most $1$, use the primitive functional equation. With parity $\chi(-1)=(-1)^a$, the completed function is $(q/\pi)^{(s+a)/2}\Gamma((s+a)/2)L(s,\chi)$, equal to a root number of modulus $1$ times the completed function of $\overline\chi$ at $1-s$. On $0<\Re s<1$ the extra factors are holomorphic and nonzero. Thus $1-\rho$ is a zero for $\bar\chi$ with the same order, since the change of variable has nonzero derivative. The [low-height gap](effective-low-height-zero-gap.md) at the reflected zero yields $|\rho|\ge\Re\rho\ge c/(q^2\log(3q))$. The total multiplicity at height at most $1$ is $O(\log(3q))$. Therefore with $U_\chi(T)=\sum_{\rho\in W_\chi(T)}m_\chi(\rho)/|\rho|$,
$$
U_\chi(1)\ll q^2\log^2(3q),\qquad
U_\chi(T)\ll q^2\log^2(3q)+\log^2(qT).
\tag{2}
$$

## Dropping the left half and changing the modulus

The [primitive explicit formula](truncated-explicit-formula-primitive.md) uses all of $W_\chi(T)$ and has error $O((u/T)\log^2(quT)+\log(qu)+U_\chi(1))$. The zeros with $\Re\rho<1/2$ contribute at most $\sqrt u\,U_\chi(T)$. Insert (2) and use $quT\ge3q$ and $\sqrt u\ge1$ to get (1) for primitive $\chi$.

For any $\chi$ modulo $q$, let $\chi^*$ be its inducing primitive character of conductor $q_*\mid q$. The [change of modulus](exceptional-zero-change-of-modulus.md) preserves the right-hand zeros and their multiplicities because the extra Euler factors are nonzero there. It also preserves principal status. Only powers of primes dividing $q$ can contribute to the difference of the arithmetic sums. Their weight is at most
$$
\sum_{p\mid q}\sum_{1\le j\le\log u/\log p}\log p
\le(\log q/\log2)\log u.
$$
Apply the primitive bound with $q_*\le q$ and absorb this difference into (1). The formula as stated uses $q^3$, while the above calculation also gives $q^2$.

## Lean correspondence

- `GlobalTheory.Mem.An.zeroCount_holds` counts a unit window and `zsumR_recip_le` handles large heights. `recip_bound` uses the symmetry and low-height gap for (2). The Chinese note records local replay of the unit-window count. [Window count](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ZeroCountHolds.lean#L7) · [Reciprocal sum](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/SumIndicatorLeZsumR.lean#L82) · [Symmetry](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/DirichletLZeroSymmetry.lean#L79) · [Low-height bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExplicitFormulaDirichletZerosRightHalf.lean#L27)
- `left_zeros` gives the $\sqrt u$ factor and `norm_sub_primitive_le` the prime-power difference. `explicit_formula_right` combines these with the closed-window formula. [Left zeros](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExplicitFormulaDirichletZerosRightHalf.lean#L96) · [Prime powers](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/LogDerivSeriesOfExplicit.lean#L321) · [Conclusion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExplicitFormulaDirichletZerosRightHalf.lean#L204)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
