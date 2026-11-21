# Log-free zero density at one fixed modulus

[Chinese proof](../zh/%E5%9B%BA%E5%AE%9A%E6%A8%A1%E6%95%B0%E4%B8%8B%E6%80%8E%E6%A0%B7%E5%BE%97%E5%88%B0%E6%97%A0%E5%AF%B9%E6%95%B0%E6%8D%9F%E5%A4%B1%E7%9A%84%E9%9B%B6%E7%82%B9%E5%AF%86%E5%BA%A6.md)

For a character $\chi$ modulo $q$, let $Z_\chi(\sigma,T)$ consist of zeros with $\sigma\le\Re\rho<1$ and $|\Im\rho|\le T$, with multiplicities $m_\chi(\rho)$.

**Proposition.** There are absolute $A,C,\eta>0$ such that for each $q\ge1$, $T\ge2$, and $1-\eta\le\sigma\le1$,
$$
\sum_{\chi\bmod q}\sum_{\rho\in Z_\chi(\sigma,T)}m_\chi(\rho)
\le C(qT)^{A(1-\sigma)}.
\tag{1}
$$

## An integrated prime mean square

Write $S_\chi(N,y;\tau)=\sum_{N<p\le y}(\log p)\chi(p)p^{-1-i\tau}$. For $U\ge1$ and $1\le N\le y\le M$ with $(2qU)^2\le N$, the [fixed-modulus prime second moment](../zh/%E5%9B%BA%E5%AE%9A%E6%A8%A1%E6%95%B0%E7%9A%84%E7%B4%A0%E6%95%B0%E5%A4%9A%E9%A1%B9%E5%BC%8F%E4%BA%8C%E9%98%B6%E7%9F%A9.md) gives
$$
\sum_{\chi\bmod q}\int_{-U}^{U}|S_\chi(N,y;\tau)|^2\,d\tau
\le C_1\sum_{N<p\le y}\frac{\log p}{p}.
$$
To bound the last sum, use $\sum_{n\le Y}\Lambda(n)\lfloor Y/n\rfloor=\log(Y!)$ with $Y=\lfloor y\rfloor$. Replacing the floors by $Y/n$ costs at most $(\log4+4)Y$ by Chebyshev's bound for $\sum_{n\le Y}\Lambda(n)$. Thus the prime sum is bounded by $\log y+C_{\rm M}$ with $C_{\rm M}=\log4+4$. Integrating in $dy/y$ from $N$ to $M$ gives
$$
\sum_\chi\int_{-U}^{U}\int_N^M|S_\chi(N,y;\tau)|^2\frac{dy}{y}\,d\tau
\le C_1(\log M+C_{\rm M})\log M.
\tag{2}
$$

## Detection intervals and their overlaps

The [small-disk result](large-derivative-from-a-zero-in-a-small-disk.md) bounds the total zero multiplicity in $|\rho-(1+i\tau)|\le r$ by $C_2(1+r\log(q(|\tau|+2)))$ for $0<r\le1/2$, provided $\chi$ is nonprincipal or $|\tau|\ge2$. The same result gives a large derivative $D_k$ for some $K\le k\le2K$ if the disk contains a zero, $L\ge\log(q(|\tau|+2))$, $1/L\le r\le r_0$, and $K\ge C_3rL$. Apply the [large-derivative mean-square bound](prime-mean-square-lower-bound-from-large-derivative.md) to $c_n=\chi(n)n^{-i\tau}$ at $1+r$. For absolute $a,b,C_4,K_0$ and adjusted $r_0$, we obtain, when also $K\ge K_0$,
$$
G_\chi(\tau):=\int_N^M|S_\chi(N,y;\tau)|^2\frac{dy}{y}
\ge r^{-3}e^{-C_4K},\qquad N=e^{aK/r},\ M=e^{bK/r}.
\tag{3}
$$

Set $U=T+1$. By the principal zero-free region at modulus $1$ and the nonvanishing of the extra Euler factors for $\Re s>0$, some absolute $\eta_1>0$ at most $1/2$ makes every principal zero with $\Re\rho\ge1-\eta_1$ have $|\Im\rho|\ge3$. Suppose $2(1-\sigma)\le r\le\min(r_0,1/2)$. Attach to each zero of $Z_\chi(\sigma,T)$ the length-$r$ interval $|\tau-\Im\rho|\le r/2$ inside $[-U,U]$. In that interval the zero is within $r$ of $1+i\tau$, and principal zeros have $|\tau|\ge2$. With $L\ge\log(q(T+3))$ the hypotheses of (3) hold on every interval if $K,r$ meet the remaining bounds.

At any fixed $\chi,\tau$, the sum of multiplicities of covering intervals is at most $C_2(1+rL)$ by the small-disk count. Therefore
$$
r^{-3}e^{-C_4K}\sum_{\rho:\,|\tau-\Im\rho|\le r/2}m_\chi(\rho)
\le C_2(1+rL)G_\chi(\tau),
$$
where the sum ranges over $Z_\chi(\sigma,T)$. Integrating gives each zero a factor $r$. If $(2qU)^2\le N$, sum over $\chi$ and use (2) to bound the count by $C_1C_2 r^2(1+rL)e^{C_4K}(\log M+C_{\rm M})\log M$. Substituting $\log M=bK/r$, this is at most $D(1+rL)e^{C_4K}K^2$ for an absolute $D$ when $K\ge1$.

## Parameters

Shrink $r_0$ to at most $1/2$ and put $\eta=\min(\eta_1,r_0/2)$. Take $L=\log(q(T+3))+1/r_0$, $r=\max(2(1-\sigma),1/L)$ and $K=\lceil E rL\rceil$ with $E=C_3+|K_0|+4/a$. These choices meet the radius and order bounds, and $aK/r\ge4L$ gives $N\ge(2q(T+1))^2$. Put $x=rL$. We have $1\le x\le2+6(1-\sigma)\log(qT)$ and $1\le K\le(E+1)x$. Use $1+x\le e^x$ and $x\le e^x$ to bound the count by
$$
D(E+1)^2\exp((C_4(E+1)+3)x).
$$
This proves (1). The squared logarithm from (2) becomes $O(K^2/r^2)$, and integrating the detection intervals supplies the compensating $r^2$. Thus the leftover polynomial factors depend only on $rL$.

## Lean correspondence

- `principal_height` and `count_le` give the height restriction and interval integration. `sum_log_div_le` and `mean_le` give (2). The Chinese note records local replay of the prime second moment used there. [Height](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LogFreeZeroDensityDirichletOneModulus.lean#L15) · [Mean upper bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LogFreeZeroDensityDirichletOneModulus.lean#L158)
- `detect`, `count_param` and `zero_density` give the lower bound, integrated count, and final choice. [Detection](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LogFreeZeroDensityDirichletOneModulus.lean#L212) · [Count](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LogFreeZeroDensityDirichletOneModulus.lean#L243) · [Conclusion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LogFreeZeroDensityDirichletOneModulus.lean#L322) · [Forwarding theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LogFreeZeroDensityDirichletOneModulusStatement.lean#L8)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
