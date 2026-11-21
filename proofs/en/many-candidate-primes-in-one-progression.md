# Supplying many candidate primes in a single progression

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E4%BF%9D%E8%AF%81%E4%B8%80%E4%B8%AA%E5%90%8C%E4%BD%99%E7%B1%BB%E9%87%8C%E6%9C%89%E8%B6%B3%E5%A4%9F%E5%A4%9A%E7%9A%84%E5%80%99%E9%80%89%E7%B4%A0%E6%95%B0.md)

Let integers $m\ge3$, $a\ge0$ have $\gcd(a,m)=1$. For $X>0$ put
$$
\mathrm{PP}(m,a;X)=\{p:p\text{ prime},\ \sqrt X<p\le X,\ p\equiv a\bmod m\}.
$$
Fix $C_0,C_{\rm r},c_{\rm r},c>0$ and set $R(B,Y)=C_{\rm r}(e^{-c_{\rm r}\log Y/\log B}+e^{-c_{\rm r}\sqrt{\log Y}})$. Assume `PrimesAPInterval`: for all such $m,a$ and real $Y,h$ satisfying
$$
Y\ge(4m)^{C_0},\quad h\le1,\quad R(4m,Y)\le h/100,\quad (4m)^7\le hY^{1/3},
$$
the number of primes in that progression in $(Y,(1+h)Y]$ is at least $c h(4m)^{-6}Y/\log Y$. The [short-interval proof](short-interval-primes-with-an-exception.md) supplies this hypothesis.

**Proposition.** For every $0<\epsilon<1$ there exists $x_0$ such that for every $x\ge x_0$, $m,a$ as above, and $X>0$ satisfying
$$
\tfrac14(\log x)^2\log m\le\log X,\qquad x^{\epsilon/6}\le\log X,
\tag{1}
$$
one has $\#\mathrm{PP}(m,a;X)\ge X^{9/10}$.

Put $B=4m$, $L=\log X$, and choose
$$
K_0=\max(2C_0,400C_{\rm r}/c_{\rm r},120),\qquad
L_0=\max(3,2(200C_{\rm r}/c_{\rm r})^2,1600/c).
$$
Suppose first $L\ge L_0$ and $L\ge K_0\log B$. Take $Y=X/2$, $h=1$. Then $\sqrt X\le Y$ and $L/2\le\log Y\le L$. We have $Y\ge B^{C_0}$ and $\log Y\ge21\log B$, giving $B^7\le Y^{1/3}$. Both exponents $c_{\rm r}\log Y/\log B$ and $c_{\rm r}\sqrt{\log Y}$ are at least $200C_{\rm r}$, so by $e^t\ge1+t$ each addend of $R(B,Y)$ is at most $1/200$. Hence the short-interval bound gives $\#\mathrm{PP}(m,a;X)\ge cB^{-6}X/(2\log Y)\ge cB^{-6}X/(2L)$.

From $L\ge120\log B$ we get $B^6\le e^{L/20}$. From $e^{L/20}\ge L^2/800$ and $L\ge1600/c$ we also get $L\le(c/2)e^{L/20}$. Substituting both yields the lower bound $X^{9/10}$.

Finally take $x_0=\exp(\max(12K_0+1,6L_0/\epsilon))$. If $x\ge x_0$, then (1) gives $L\ge x^{\epsilon/6}\ge L_0$. Since $4m\le m^3$, the other half of (1) and $(\log x)^2\ge12K_0$ give $L\ge3K_0\log m\ge K_0\log B$. Both preceding hypotheses hold uniformly in $m$.

## Lean correspondence

- `PrimesAPInterval`, `PP` and `PrimesInProgressionCountLowerBound` give the definitions. [Definitions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/SmoothedRemainderRealIntegralFormula.lean#L126)
- `gl2a4_exp_small` and `gl2a4_log_le_exp` bound the error and logarithm. `gl2a4_count_core` uses $Y=X/2$, and `primesInProgressionCountLowerBound` verifies the thresholds from (1). [Core](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/HookFormulaTorsion/PrimesInProgressionCountLowerBound.lean#L643) · [Conclusion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/HookFormulaTorsion/PrimesInProgressionCountLowerBound.lean#L745)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
