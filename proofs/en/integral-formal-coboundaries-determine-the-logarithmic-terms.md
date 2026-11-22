# Integral formal coboundaries determine the logarithmic terms

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $p>2$ be prime, $K$ a complete characteristic-zero ultrametric field with $v(p)=1$, and $R$ its valuation ring. Use the integral formal group law $F$ with logarithm
$$
\ell(t)=\sum_{j\ge0}p^{-j}t^{p^{2j}},\qquad
g(t)=p^{-1}\ell(t^p)=\sum_{j\ge0}p^{-j-1}t^{p^{2j+1}}.
$$
For a one-variable series $f$ write $\delta f(x,y)=f(F(x,y))-f(x)-f(y)$. We prove two facts used in the normal form of the standard theta exponent.

1. If $f(0)=0$ and $\delta f$ is integral, then $f=a g+b\ell+I$ for $a\in R$, $b\in K$, and $I\in R[[t]]$.
2. If $H(x,y)$ vanishes on both axes and its two additivity defects for $F$ are integral, then $H=\beta\,\ell(x)\ell(y)+J$ for $\beta\in K$, $J\in R[[x,y]]$.

The group law is defined over $\mathbb Q_p$, since it is obtained using $\ell$ and its inverse. Its coefficients are integral by hypothesis, so $F(x^p,y^p)\equiv F(x,y)^p\bmod p$. The derivative $\ell'(t)$ is integral. We use the following consequence for any series $P$ with integral derivative. At integral zero-constant arguments $z,z+pW$, the difference $P(z+pW)-P(z)$ is in $pR[[x,y]]$. For a coefficient $P_m$ and a binomial term of order $k\ge1$, use $mP_m\in R$ and
$$
P_m\binom{m}{k}p^k=(mP_m)\binom{m-1}{k-1}p^k/k.
$$
The last factor has valuation $k-v_p(k)\ge1$. Applying this to $\ell$ shows that
$\ell(F(x,y)^p)-\ell(F(x^p,y^p))$ is divisible by $p$. The second term is $\ell(x^p)+\ell(y^p)$, so $\delta g$ is integral, while $\delta\ell=0$.

To prove the first claim, start by subtracting $f_1\ell$, where $f_1=[t]f$. Suppose a current remainder $f_*$ has integral coefficients below degree $n\ge2$, and its coboundary is integral. The coefficient of $x^j y^{n-j}$ in $\delta f_*$ for $0<j<n$ equals $\binom{n}{j}[t^n]f_*$ up to an integral term. The reason is that the homogeneous degree $n$ term of $F^n$ is $(x+y)^n$ and lower powers use only coefficients already integral. If $n$ is not a power of $p$, some interior binomial coefficient is a unit. Indeed take a nonzero digit at $p^k<n$ in the base-$p$ expansion of $n$, and read $\binom{n}{p^k}$ modulo $p$ by the product expansion of $(1+t)^n$. Thus the coefficient of degree $n$ is integral. For $n=p^k$, $k\ge1$, the coefficient $\binom{p^k}{p^{k-1}}$ has valuation one, by the same digit computation on $\binom{p^k-1}{p^{k-1}-1}$. Hence $[t^n]f_*\in p^{-1}R$.

For $k=2j$ subtract $p^j[t^n]f_*\cdot\ell$, and for $k=2j+1$ subtract $p^{j+1}[t^n]f_*\cdot g$. Their degree-$n$ coefficients cancel the current coefficient. Earlier coefficients in the respective series have denominator dividing $p^{j-1}$ or $p^j$, so the subtraction affects them only integrally. The coboundary remains integral because the multiplier of $g$ is integral. These corrections have multipliers of valuations at least $j-1$ or $j$, respectively. Thus the two running multipliers converge by completeness, and every fixed coefficient of the final remainder stays integral by closedness of $R$. This proves the first claim.

For the second claim, apply the first to each slice in either variable. If $h_{ij}=[x^iy^j]H$, comparison of the two slice representations gives
$$
a_j g_i+b_j\ell_i\equiv a'_i g_j+b'_i\ell_j\pmod R,
$$
where $g_i,\ell_i$ are the indicated coefficients and $a_j,a'_i\in R$. Denote the even and odd powers by $E_m=p^{2m}$, $O_m=p^{2m+1}$, so $\ell_{E_m}=p^{-m}$ and $g_{O_m}=p^{-m-1}$. Fix $i=O_m$ and let $j=E_n$ tend through those powers. The left side $a_{E_n}p^{-m-1}$ is bounded independently of $n$. Hence $b'_{O_m}p^{-n}$ is bounded, which forces $b'_{O_m}=0$. With that term zero, let $m$ increase at fixed $n$ to get $a_{E_n}=0$. For fixed $j=O_n$ take $i=O_m$ and let $m$ increase. Now the right side $a'_{O_m}p^{-n-1}$ is bounded, so $a_{O_n}=0$. If $j$ has neither kind of power, the right side is zero and taking $i=O_m$ gives $a_j=0$ as well. Interchanging the variables gives $a'_i=0$ for all $i$.

All $h_{ij}$ outside the even-power pairs are therefore integral. On even-power pairs we have
$$
p^n b_{E_n}-p^m b'_{E_m}\in p^{n+m}R.
$$
For any $n,n'$, use a common arbitrarily large $m$ and subtract the two relations. The difference $p^n b_{E_n}-p^{n'}b_{E_{n'}}$ has valuation at least $m+\min(n,n')$ for arbitrarily large $m$, so it vanishes. Write $\beta$ for their common value. It follows that $h_{E_m,E_n}\equiv\beta p^{-m-n}\pmod R$, proving the second claim.

**Lean correspondence.** The divided derivative and integral coboundary of the odd series are [`divided_derivative`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/IntegralPderivLgF.lean#L101) and [`DeIntegral_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/IntegralPderivLgF.lean#L191). The induction and its limiting coefficients are [`good_succ`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/NotDvdChoosePowMul.lean#L428) and [`exists_limit`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/NotDvdChoosePowMul.lean#L486), with the one-variable theorem at [`LemmaOne_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/NotDvdChoosePowMul.lean#L529). Comparison across both variables is [`LemmaTwo_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/LemmaTwoOf.lean#L280).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
