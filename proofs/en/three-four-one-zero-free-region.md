# The three-four-one inequality and the zero-free region

[Chinese proof](../zh/%E4%B8%89%E5%9B%9B%E4%B8%80%E4%B8%8D%E7%AD%89%E5%BC%8F%E6%80%8E%E6%A0%B7%E7%BB%99%E5%87%BA%E6%97%A0%E9%9B%B6%E7%82%B9%E5%8C%BA%E5%9F%9F.md)

**Proposition.** There are absolute constants $c,c'>0$ such that, for every $q\ge1$, the following bounds hold. If $\chi$ is nonprincipal modulo $q$ and $\rho=\beta+i\gamma$ is a zero of $L(s,\chi)$ with $\chi^2\ne\chi_0$ or $\gamma\ne0$, then
$$
\beta<1-\frac{c}{\log(q(|\gamma|+2))}.
\tag{1}
$$
If $s\ne1$ is a zero of the principal-character function $L(s,\chi_0)$, then
$$
\Re s<1-\frac{c'}{\log(q(|\Im s|+2))}.
\tag{2}
$$

## Positive combinations of log derivatives

For $\sigma>1$, let $D_\chi(\sigma,t)=-\Re (L'/L)(\sigma+it,\chi)$. The Euler product gives
$$
-\frac{L'}{L}(s,\chi)=\sum_{n\ge1}\Lambda(n)\chi(n)n^{-s}.
$$
Indeed the logarithm is given by the series with terms $\chi(p)^k p^{-ks}/k$. The series and its termwise derivative converge locally uniformly for $\Re s>1$. On integers $n$ coprime to $q$, set $z=\chi(n)n^{-it}$. The identity $3+4\Re z+\Re(z^2)=2(1+\Re z)^2$ holds for $|z|=1$. On the other integers all the character values vanish. Summing with weights $\Lambda(n)n^{-\sigma}$ gives
$$
3D_{\chi_0}(\sigma,0)+4D_\chi(\sigma,t)+D_{\chi^2}(\sigma,2t)\ge0.
\tag{3}
$$
For real characters $\chi,\psi$, the analogous pointwise inequality $(1+\chi(n))(1+\psi(n))\ge0$ on the units gives $D_{\chi_0}+D_\chi+D_\psi+D_{\chi\psi}\ge0$ at $(\sigma,0)$. Taking $\psi=\chi$ gives $D_{\chi_0}(\sigma,0)+D_\chi(\sigma,0)\ge0$.

## One-sided bounds from the local disk formula

Use the [local log-derivative formula](local-log-derivative-from-disk-zeros.md) with center $3/2+it$, outer radius $1$, evaluation radius $2/3$, and zero cutoff radius $5/6$. For nonprincipal $\chi$, partial summation gives $L(z,\chi)=z\int_1^\infty A(u)u^{-z-1}\,du$ on $\Re z>0$, where $A(u)=\sum_{n\le u}\chi(n)$ has $|A(u)|\le q$. The upper bound $q|z|/\Re z$ on the outer disk, together with $|L(3/2+it,\chi)|\ge\zeta(3/2)^{-1}\ge1/3$ from the inverse Euler product, bounds the log of the relative growth by $O(\log(q(|t|+2)))$.

For $\zeta$, apply the disk formula to $F(z)=(z-1)\zeta(z)$, with $F(1)=1$. Partial summation gives $|\zeta(z)-z/(z-1)|\le |z|/\Re z$ for $\Re z>0$, $z\ne1$. On the outer disk this gives $|F(z)|\le 5(|t|+2)^2$, and the center has $|F(3/2+it)|\ge1/6$. Thus the error for $\zeta$ is $O(\log(|t|+2))$, with the additional term $+\Re(1/(s-1))$ in the negative log derivative.

Every zero $w=\alpha+i\vartheta$ has $\alpha\le1$ by nonvanishing in the Euler half-plane. Hence for $\sigma>1$ the real part of $1/(\sigma+it-w)$ is nonnegative. The nonprincipal estimate, for $1<\sigma\le2$, therefore allows retaining any set $S$ of zeros from the radius-$5/6$ disk:
$$
D_\chi(\sigma,t)\le C_1\log(q(|t|+2))
-\sum_{w\in S}m_w\Re\frac1{\sigma+it-w}.
\tag{4}
$$
Here $m_w$ is the analytic multiplicity. For the principal character, $L(s,\chi_0)=\zeta(s)\prod_{p\mid q}(1-p^{-s})$. The log derivative of each extra factor has modulus at most $\log p$ for $\sigma>1$, since $p^{-\sigma}\le1/2$. Their total is at most $\log q$. Dropping the zero terms gives
$$
D_{\chi_0}(\sigma,t)\le \Re\frac1{\sigma+it-1}+C_0\log(q(|t|+2)).
\tag{5}
$$

## Nonprincipal zeros

Let $\delta=1-\beta>0$, using nonvanishing on $\Re s\ge1$, and let $\ell=\log(q(|\gamma|+2))>1/2$. First assume $\delta\le1/21$ and take $\sigma=1+8\delta$. The zero $\rho$ lies in the radius-$5/6$ disk at height $\gamma$. By (4) and (5),
$$
D_{\chi_0}(\sigma,0)\le (8\delta)^{-1}+C_0\ell,\qquad
D_\chi(\sigma,\gamma)\le -(9\delta)^{-1}+C_1\ell.
$$
Also $\log(q(2|\gamma|+2))\le2\ell$.

- If $\chi^2\ne\chi_0$, apply (4) with no selected zero at height $2\gamma$. Inserting all three bounds in (3) gives $(4/9-3/8)/\delta\le(3C_0+6C_1)\ell$.
- If $\chi^2=\chi_0$ and $2\gamma^2>81\delta^2$, use (5) at height $2\gamma$. Its pole term is $8\delta/(64\delta^2+4\gamma^2)\le4/(81\delta)$. Now (3) gives $(4/9-3/8-4/81)/\delta\le(5C_0+4C_1)\ell$. The numerator is $13/648$.
- If $\chi^2=\chi_0$, $\gamma\ne0$ and $2\gamma^2\le81\delta^2$, then $\rho$ and $\bar\rho$ are distinct zeros because $L(\bar s,\chi)=\overline{L(s,\chi)}$. The squared distances of both from $3/2$ are at most $(1/2+1/21)^2+81/(2\cdot21^2)<(5/6)^2$. Each contributes at least $9\delta/(81\delta^2+\gamma^2)\ge2/(27\delta)$ to the sum in (4) at $t=0$. Combining with $D_{\chi_0}+D_\chi\ge0$ gives $(4/27-1/8)/\delta\le(C_0+C_1)\ell$. The numerator is $5/216$.

The three bounds imply $1/\delta\le K\ell$ for $K=300(C_0+C_1)$. When $\delta>1/21$ we already have $\delta>1/(42\ell)$. Thus $c=\min(1/(2K),1/42)$ works in (1).

## Principal zeros

For a zero $\beta+i\gamma$ of $\zeta$ with $|\gamma|\ge1$, put $\ell=\log(|\gamma|+2)\ge1$, $K=9C_\zeta+5$, and $\Delta=1/(2K)$, where $C_\zeta$ is the disk error constant. Suppose $\beta\ge1-1/(28K\ell)$ and take $\sigma=1+\Delta/\ell$. Then $\beta\ge2/3$, permitting us to retain that zero at height $\gamma$. In (3) for modulus $1$, retain the pole at height zero and the selected zero at height $\gamma$. Each of the pole contributions at heights $\gamma$ and $2\gamma$ is at most $\sigma-1$. The errors are bounded by $9C_\zeta\ell$ and the weighted high pole terms by $5\ell$. Thus
$$
\frac{4}{\sigma-\beta}\le\frac{3}{\sigma-1}+K\ell=7K\ell.
$$
Multiplying by $\sigma-\beta$ would give $4\le7K(\Delta+1/(28K))=15/4$, a contradiction.

For $|\gamma|\le1$, $F=(s-1)\zeta(s)$ is continuous and nonzero on $\{1+it:|t|\le1\}$, using nonvanishing on the line and $F(1)=1$. Compactness supplies one $\eta>0$ such that all zeros of $\zeta$ in that height range have real part at most $1-\eta$. Each extra principal Euler factor has zeros only on $\Re s=0$. Since $\log(q(|t|+2))>1/2$, the choice $c'=\min(1/(28K),\eta/2,1/2)$ now proves (2). The [real exceptional-zero argument](unique-simple-exceptional-zero.md) treats the real quadratic zeros left by (1).

## Lean correspondence

- `three_four_one` and `neg_sum_logDeriv_nonneg` give the Euler-product inequalities. [Three-four-one](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LogDerivativeBound.lean#L76) · [Product of two real characters](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/NegSumLogDerivNonneg.lean#L42)
- `logDeriv_LFunction_local` and `logDeriv_riemannZeta_local` supply the disk formulas, and `PrincipalLogDeriv.neg_re_logDeriv_le` gives the principal bound. [Dirichlet](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LogDerivDirichletLFunctionLocalZeroSum.lean#L17) · [Zeta](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LogDerivRiemannZetaLocalZeroSum.lean#L87) · [Principal](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/NegReLogDerivPrincipalLFunctionLe.lean#L98)
- `inv_le_log` gives the three-case calculation, and `zero_free_region` assembles (1). The principal argument is in `ZeroFreePrincipal`. [Cases](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LFunctionConjEqZero.lean#L173) · [Region](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LFunctionConjEqZero.lean#L290) · [High height](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ZeroFreePrincipal.lean#L128) · [Low height](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ZeroFreePrincipal.lean#L239) · [Principal reduction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ZeroFreePrincipal.lean#L281)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
