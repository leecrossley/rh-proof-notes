# Relative error for prime powers in an arithmetic progression

[Chinese proof](../zh/%E7%AE%97%E6%9C%AF%E7%BA%A7%E6%95%B0%E7%9A%84%E7%B4%A0%E6%95%B0%E5%B9%82%E4%B8%BB%E9%A1%B9%E4%B8%BA%E4%BB%80%E4%B9%88%E6%9C%89%E7%9B%B8%E5%AF%B9%E8%AF%AF%E5%B7%AE.md)

For $M\ge3$ and a unit $b\bmod M$, let $\psi(u;M,b)=\sum_{1\le n\le u,\ n\equiv b\bmod M}\Lambda(n)$. For $h>0$, the predicate `IsExc h χ β` says $\chi^2=\chi_0$, $1-h/\log M<\beta<1$, and $L(\beta,\chi^*)=0$ for the inducing primitive character. The data `ExcData h M b θ β` say either there is no such pair and $\theta=0$ with arbitrary $\beta$, or there is such a pair $(\chi_1,\beta)$ and $\theta=\chi_1(b)\in\{-1,1\}$.

**Proposition.** There is an absolute $h_0>0$ such that for each $0<h\le h_0$ there are $c_2,c_3,C>0$ with the following property. For every such $M,b$, $\theta\in\mathbb Z$, and $\beta,u\in\mathbb R$ satisfying `ExcData` and $u\ge M^{c_2}$, let $J(u)=u-\theta u^\beta/\beta$, interpreted as $u$ when $\theta=0$. Then
$$
|\varphi(M)\psi(u;M,b)-J(u)|
\le C(e^{-c_3\log u/\log M}+e^{-\sqrt{c_3\log u}})J(u).
\tag{1}
$$

## Removing the exceptional term by character orthogonality

The [right-half explicit formula](explicit-formula-right-half-rectangle.md) gives
$$
\sum_{n\le u}\Lambda(n)\chi(n)=\mathbf1_{\chi=\chi_0}u
-\sum_{\rho\in Z_\chi(1/2,T)}m_\chi(\rho)u^\rho/\rho+O(E),
\quad E=C_{\rm e}(u/T+\sqrt u M^3)\log^2(MuT)
$$
for $2\le T\le u$. Multiply by $\overline{\chi(b)}$ and sum. Character orthogonality gives $\varphi(M)\psi(u;M,b)$ on the left. By the [exceptional-pair theorem](exceptional-zero-change-of-modulus.md), an exceptional $\beta$ belongs to the indicated zero set, is simple, is at least $7/8$, and is unique across the characters. Its contribution is exactly $-\theta u^\beta/\beta$. Thus if all remaining zeros have $\Re\rho\le1-\eta$, use $|\rho|\ge1/2$ to bound the error after division by $u$ by $ME/u$ plus twice their weighted sum of $m_\chi(\rho)u^{\Re\rho-1}$. The [weighted-zero theorem](../zh/%E9%9B%B6%E7%82%B9%E5%AF%86%E5%BA%A6%E6%80%8E%E6%A0%B7%E5%8F%98%E6%88%90%E6%98%BE%E5%BC%8F%E5%85%AC%E5%BC%8F%E7%9A%84%E5%8A%A0%E6%9D%83%E5%92%8C.md) supplies absolute $A,C_{\rm a},\eta_0>0$ such that for $u\ge(MT)^A$ this gives
$$
u^{-1}|\varphi(M)\psi(u;M,b)-J(u)|
\le ME/u+2C_{\rm a}(u^{-\eta/2}+u^{-\eta_0}).
\tag{2}
$$

## Choosing a gap that retains the size of the main term

Write $m=\log M\ge1$, $V=\log u$, $s=\sqrt V$, $T=e^{8m+s}$, $L=10m+s$, and $R=V/L$. For each fixed $B>0$, taking $c_2\ge20B+4B^2$ ensures $V\ge BL$. Take $B\ge\max(8,A,1/\eta_0)$ and enlarge it below. This gives $2\le T\le u$, $(MT)^A\le u$, and $\log(M(|\Im\rho|+2))\le L$ at height at most $T$.

The exceptional-pair theorem gives $1-\Re\rho\ge c/L$ for every remaining zero, and $\delta=1-\beta\ge c/(M^2m)$ if there is an exception. In the latter case, the [repulsion input](../zh/%E4%B8%80%E4%B8%AA%E4%BE%8B%E5%A4%96%E9%9B%B6%E7%82%B9%E6%80%8E%E6%A0%B7%E6%8A%8A%E5%85%B6%E4%BB%96%E9%9B%B6%E7%82%B9%E6%8E%A8%E7%A6%BB%E4%B8%80.md) gives another bound $1-\Re\rho\ge d\log(d/(\delta L))/L$. Let $w=1$ without an exception, or $w=\min(1,\delta L)$ with one. Set $d_0=\min(1,d/e)$, $c'=\min(c/2,d/4)$, and $K=1/d_0$. Require $R\ge4/d$.

If there is no exception or $\delta L\ge d_0$, take $\eta=c/L$. Then $Kw\ge1$ and $u^{-\eta/2}\le Kw e^{-c'R}$. Otherwise put $v=\delta L<d_0$ and take $\eta=d\log(d/v)/L$. Since $\log(d/v)\ge1$ and $dR\ge4$,
$$
u^{-\eta/2}=e^{-dR\log(d/v)/2}\le (v/d)e^{-dR/4}
\le Kw e^{-c'R}.
\tag{3}
$$
Here the exponent bound follows by retaining $\log(d/v)$ from one half of $dR\log(d/v)/2$ and $dR/4$ from the other.

With an exception let $x=\delta V\ge\delta L$. Since $\theta\le1$, $\beta\ge7/8$ and $V\ge8$,
$$
J(u)/u\ge1-e^{-x}/\beta
\ge\frac{\beta x-\delta}{\beta(1+x)}
\ge\frac{3x}{4(1+x)}\ge w/4.
$$
The lower gap and $m\le M$ give $w\ge c_{\rm w}e^{-3m}$ with $c_{\rm w}=\min(1,c)$. Both bounds hold with $w=1$ without an exception.

## The remaining errors

With this height, $ME/u=C_{\rm e}(e^{-7m-s}+e^{4m-V/2})(9m+V+s)^2$. Use $V\ge8L$ to bound the square by $4V^2$, $V/2\ge7m+s$, and $4V^2=4s^4\le1536e^{s/2}$. It follows that $ME/u\ll e^{-3m-s/2}$. Also $u^{-\eta_0}\le e^{-L}\le e^{-3m-s/2}$. Thus both errors are $O(w e^{-s/2})$.

Take $c_3=\min(1/4,c'/20,(c')^2/4)$. When $s\le10m$ we have $R\ge V/(20m)$, giving $e^{-c'R}\le e^{-c_3 V/m}$. When $s>10m$, $R\ge s/2$, giving $e^{-c'R}\le e^{-\sqrt{c_3 V}}$. Also $e^{-s/2}\le e^{-\sqrt{c_3V}}$ in both ranges. Substitute (3) and the other error bounds in (2), then use $uw\le4J(u)$ to obtain (1).

## Lean correspondence

- `orth`, `zsum`, `combine` and `struct` give the orthogonality and zero extraction. `mainLower`, `realEnd`, and `etaChoice` control the relative error. [Orthogonality](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ChebyshevPsiProgressionRelativeError.lean#L12) · [Gap selection](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ChebyshevPsiProgressionRelativeError.lean#L256)
- `psiAP_relative` combines the inputs, and `chebyshevPsiProgression_relative_error` forwards it. This argument works for every $M\ge3$. The [two-range theorem](relative-prime-number-theorem-two-ranges.md) is the separate screening route for $8\mid M$. [Assembly](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ChebyshevPsiProgressionRelativeError.lean#L294) · [Forwarding theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ChebyshevPsiProgressionRelativeErrorStatement.lean#L8)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
