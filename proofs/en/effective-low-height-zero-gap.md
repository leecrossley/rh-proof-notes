# An effective zero gap at low height

[Chinese proof](../zh/%E4%BE%8B%E5%A4%96%E9%9B%B6%E7%82%B9%E7%A6%BB%E4%B8%80%E8%87%B3%E5%B0%91%E6%9C%89%E5%A4%9A%E8%BF%9C.md)

**Proposition.** There is an absolute $c>0$ such that for every $q\ge1$, character $\chi$ modulo $q$, and zero $\rho$ of $L(s,\chi)$ with $|\Im\rho|\le1$,
$$
1-\Re\rho\ge\frac{c}{q^2\log(3q)}.
\tag{1}
$$
Here exclude $\rho=1$ for the principal character, which has a pole there. The exclusion is explicit in Lean because the function is represented as a total function.

## The real-axis derivative

Put $\ell=\log(3q)$. For nonprincipal $\chi$ first consider $\Re s\ge1-2/\ell$, $\Re s\ge1/20$ and $|s|\le2$. The initial terms up to $q$ satisfy $n^{-\Re s}\le e^2/n$. The [partial-summation tail estimate](mobius-truncation-detecting-zeros.md) states that for nonprincipal $\chi$, integer $X\ge1$ and $\Re s>0$,
$$
\left|L(s,\chi)-\sum_{n=1}^X\chi(n)n^{-s}\right|\le 2q(1+|s|/\Re s)X^{-\Re s}.
$$
For $X=q$ this is at most $82e^2$. The initial sum is bounded by $e^2(1+\log q)$, so $|L(s,\chi)|\le84e^2\ell$.

If $1-1/\ell\le\sigma\le1$, take the circle of radius $r=1/(4\ell)$ about $\sigma$. We have $q\ge2$ for nonprincipal $\chi$, hence $\ell>4/3$. On the circle, $\Re s\ge1-5/(4\ell)\ge1/16>1/20$, $\Re s\ge1-2/\ell$, and $|s|<2$. Cauchy's derivative formula gives
$$
|L'(\sigma,\chi)|\le 84e^2\ell/r=336e^2\ell^2.
\tag{2}
$$

## The gap

The [zero-free-region bounds](three-four-one-zero-free-region.md) give $1-\Re\rho>d/\log(q(|\Im\rho|+2))$ for nonprincipal $\chi$ with $\chi^2\ne\chi_0$ or $\Im\rho\ne0$, and the same with $e$ for the principal case. At height at most $1$ the denominator is at most $\ell$, so these cases give (1) for $c\le\min(d,e)$.

The remaining case is a real zero $\beta<1$ of a nonprincipal real character. If $1-\beta\ge1/\ell$, use $c\le1$. Otherwise (2) holds along the segment $[\beta,1]$. Integration starting at the zero gives $|L(1,\chi)|\le C\ell^2(1-\beta)$ with $C=336e^2$. The [square-term argument](squares-lower-bound-at-one.md) gives $|L(1,\chi)|\ge1/(36q)$, of which the Lean proof uses the weaker $a/q^{3/2}$ with $a=1/36$. Since $\ell\le2\log(2\sqrt q)\le4\sqrt q$, we obtain
$$
1-\beta\ge\frac{a}{Cq^{3/2}\ell^2}\ge\frac{a}{4Cq^2\ell}.
$$
Thus $c=\min(1,d,e,a/(4C))$ works. Using $1/(36q)$ directly in the integral also gives $1-\beta\ge1/(36Cq\ell^2)$ for the real quadratic zeros.

## Lean correspondence

- `GlobalTheory.DirichletDeriv.exists_norm_deriv_LFunction_le` applies the Cauchy estimate to `norm_LFunction_le`. [Circle bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsNormDerivLFunctionLe.lean#L23) · [Derivative](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsNormDerivLFunctionLe.lean#L61)
- `GlobalTheory.ZeroGapNearOne.exists_gap` uses the derivative bound on the real segment. `exists_dirichletLFunction_zero_gap_near_one` forwards the result. The Chinese note records a local replay of the upstream truncation estimate and a source reading of the gap and derivative arguments. [Gap](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsDirichletLFunctionZeroGapNearOne.lean#L69) · [Forwarding theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsDirichletLFunctionZeroGapNearOneStatement.lean#L8)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
