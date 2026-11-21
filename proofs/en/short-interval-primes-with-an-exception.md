# A short-interval lower bound with an exceptional prime-counting term

[Chinese proof](../zh/%E4%BE%8B%E5%A4%96%E9%9B%B6%E7%82%B9%E5%AD%98%E5%9C%A8%E6%97%B6%E6%80%8E%E6%A0%B7%E4%BC%B0%E8%AE%A1%E7%9F%AD%E5%8C%BA%E9%97%B4%E9%87%8C%E7%9A%84%E7%B4%A0%E6%95%B0.md)

Let $C_0,C_{\rm r},c_{\rm r},c_{\rm b}>0$, $B\ge4$, $\theta\in\{-1,0,1\}$ and $\beta\in\mathbb R$. Set
$$
H(Y)=\operatorname{Li}(Y)-\theta\operatorname{Li}(Y^\beta),\qquad
R(Y)=C_{\rm r}(e^{-c_{\rm r}\log Y/\log B}+e^{-c_{\rm r}\sqrt{\log Y}})
$$
for the scales below, where $\operatorname{Li}(y)=\int_2^y dt/\log t$ for $y>1$. If $\theta=0$, omit the second main term.

**Proposition.** Take $C_0'=\max(C_0,60,2/c_{\rm b})$ and $c=1/100$. Let $1\le G\le B$, $\pi_1,\pi_2:\mathbb R\to\mathbb N$ and $\eta:\mathbb R\to\mathbb R$. For $\theta\ne0$ require $1/2\le\beta<1$ and $1-\beta\ge c_{\rm b}/(B^2\log B)$. Assume $\pi_2(Y)\le2\sqrt Y$ for $Y\ge1$, $0\le\eta(Y)\le3\log B$ for all $Y$, and
$$
|G(\pi_1(Y)+\pi_2(Y)+\eta(Y))-H(Y)|\le R(Y)H(Y)
\quad(Y\ge B^{C_0}).
\tag{1}
$$
Here $H$ is taken with the stated integral main terms when their arguments exceed $1$. For all $X\ge B^{C_0'}$, $H(X)\ge cB^{-5}X/\log X$. For every real $h\le1$ with $R(X)\le h/100$ and $B^7\le hX^{1/3}$,
$$
\pi_1(X(1+h))-\pi_1(X)\ge c h B^{-6}X/\log X,
\tag{2}
$$
where the difference is taken in $\mathbb R$.

## The same derivative factor for the increment and the total

We may set $\beta=1/2$ when $\theta=0$. With $d=1-\beta>0$, $H'(t)=F(t)/\log t$ for $F(t)=1-\theta t^{-d}$. The derivative is nonnegative, and $H(t)\ge0$ for $t\ge4$ because $2\le t^\beta\le t$. Given $Z\ge1$, if $\theta=1$ assume $d\log Z\ge1/B^2$. There is then a $W$ with
$$
1/(2B^2)\le W\le1,\qquad F(t)\ge W\ (t\ge Z),\qquad F(t)\le2W\ (1\le t\le Z^2).
\tag{3}
$$
For $\theta=0,-1$ use $W=1$. For $\theta=1$ use $W=1-Z^{-d}$. The lower bound follows from $1-e^{-v}\ge v/(1+v)$, and the upper comes from monotonicity and $F(Z^2)=(1-Z^{-d})(1+Z^{-d})$.

Since $\log X\ge(2/c_{\rm b})\log B$, in the $\theta=1$ case $d\log X\ge2/B^2$. Apply (3) first with $Z=\sqrt X$, and integrate to obtain $H(X)\ge (X-\sqrt X)/(2B^2\log X)\ge X/(4B^2\log X)$. This gives the stated bound on $H$.

Now put $X'=X(1+h)$, so $0<h\le1$ and $X'\le2X\le X^2$. Use (3) with $Z=X$ and put $U=WhX/\log X$. Integrating the lower bound on $[X,X']$ gives $H(X')-H(X)\ge U/2$. Integrating the upper bound on $[4,X']$ gives $H(X')\le6+2W\operatorname{Li}(X')$ using $H(4)\le2\operatorname{Li}(4)\le6$. For $Y\ge1296$, splitting the integral at $\sqrt Y$ gives $\operatorname{Li}(Y)\le(3/2)\sqrt Y+2Y/\log Y\le3Y/\log Y$. Indeed $\log Y\le4Y^{1/4}$ and $Y^{1/4}\ge6$. Consequently $hH(X')\le6h+12U$.

## Subtracting the two estimates

As $R$ decreases and $H$ increases, the error in subtracting (1) at the two endpoints is at most $2(h/100)H(X')\le0.12h+0.24U$. The $\pi_2(X),\eta(X)$ terms can be kept with favorable sign, leaving cost at most $G\pi_2(X')+G\eta(X')$. Write $z=X^{1/12}\ge B^5\ge1024$. Then $3\log B\le z$, $\sqrt{X'}\le(3/2)z^6$, and $0.12h+G\pi_2(X')+G\eta(X')\le4Bz^6$. As $hz^4\ge B^7\ge B^3$ and $\log X\le12z$,
$$
4Bz^6/U\le8 B^3\log X/(hz^6)\le 96/z\le0.12.
$$
After subtracting the errors from $U/2$, we obtain $G(\pi_1(X')-\pi_1(X))\ge0.14U$. Since $G\le B$ and $W\ge1/(2B^2)$ this gives the stronger bound $0.07hX/(B^3\log X)$ and proves (2).

## Arithmetic progressions

Apply [the progression case of the relative prime number theorem](relative-error-from-prime-powers-to-primes.md) with $m\ge3$ and unit $a\bmod m$. Take $B=4m$, $G=\varphi(m)$, $\pi_1(Y)=\pi(Y;m,a)$, and $\pi_2=\eta=0$. The gap $c_{\rm S}/(m^2\log m)$ implies $c_{\rm S}/(B^2\log B)$. The threshold increases when replacing $m$ by $B$, and the error only becomes larger upon changing the denominator to $\log B$ and choosing $c_{\rm r}=\min(c_3',\sqrt{c_3'})$. Thus (2) supplies `PrimesAPInterval`: for $X\ge(4m)^{C_0'}$, $h\le1$, $R(X)\le h/100$, $(4m)^7\le hX^{1/3}$, the number of primes $p\equiv a\bmod m$ in $(X,X(1+h)]$ is at least $c h(4m)^{-6}X/\log X$.

## Lean correspondence

- `gl2a4_weight`, `Emain_lower_bound` and `Li_le_three_mul_div_log` provide the derivative and cumulative bounds. [Weights](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/HookFormulaTorsion/PrimesInProgressionCountLowerBound.lean#L156) · [Main term](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/HookFormulaTorsion/PrimesInProgressionCountLowerBound.lean#L212) · [Logarithmic integral](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/HookFormulaTorsion/PrimesInProgressionCountLowerBound.lean#L343)
- `exceptional_zero_contribution_bound` estimates the increment and `shortIntervalLowerBound` packages the result. [Increment](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/HookFormulaTorsion/GlobalBoundRefinements.lean#L51) · [Conclusion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/HookFormulaTorsion/GlobalBoundRefinements.lean#L222)
- `primesAPInterval_of_primesRel` and `shortIntervalImpliesProgressions_statement` specialize to progressions. [Change of parameters](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/PrimesAPIntervalOfPrimesRel.lean#L12) · [Interval count](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/HookFormulaTorsion/GlobalBoundRefinements.lean#L366)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
