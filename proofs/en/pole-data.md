# From weighted prime sums to poles

[Chinese proof](../zh/%E4%BB%8E%E5%8A%A0%E6%9D%83%E7%B4%A0%E6%95%B0%E5%92%8C%E5%88%B0%E6%9E%81%E7%82%B9-%E7%95%99%E6%95%B0%E4%B8%BA%E4%BD%95%E4%B8%8D%E6%8A%B5%E6%B6%88.md) · [Reading and review status](../../STATUS.md)

The [Landau window lemma](landau-window.md) constrains the poles of a Laplace transform. This note constructs the transform for a finite family of Dirichlet characters and computes the residue at each pole. The multiplicities explain why taking real parts and then adding the errors with positive weights preserves the contribution from each zero.

## Statement

Let $J$ be a finite index set. For each $j\in J$ choose a modulus $N_j\ge 1$, a Dirichlet character $\chi_j$ modulo $N_j$, and a weight $a_j>0$. Assume that either $N_j=1$ or $\chi_j$ is nonprincipal. Write $\mathbf 1$ for the character of modulus $1$ and $\gamma_E$ for Euler's constant. Put
$$
S_\chi(y)=\sum_{1\le n\le y}\Lambda(n)\chi(n)(y/n-1),\qquad y>0,
$$
where $\Lambda(p^m)=\log p$ at prime powers with $m\ge 1$ and vanishes elsewhere. Define the corrected sums and the real-valued function on the logarithmic scale by

$$
\begin{aligned}
G_{\mathbf 1}(y)&=S_{\mathbf 1}(y)-y\log y+(1+\gamma_E)y,\\
G_\chi(y)&=S_\chi(y)+y\,\frac{L'(1,\chi)}{L(1,\chi)}\quad(\chi\ne\mathbf 1),\\
g(u)&=\sum_{j\in J}a_j\operatorname{Re}G_{\chi_j}(e^u).
\end{aligned}
$$

Write $Z$ for the set of $\rho$ with $\operatorname{Re}\rho>0$ for which $L(\rho,\chi_j)=0$ or $L(\bar\rho,\chi_j)=0$ for some $j\in J$. Then $g$ is measurable and has a bound $|g(u)|\le Ce^{2u}$ for $u\ge 0$ and some $C\ge 0$. Every point of the right half-plane has a punctured neighbourhood disjoint from $Z$. There exists a function $\Phi$ agreeing with

$$
\int_0^\infty g(u)e^{-su}\,du
\qquad(\operatorname{Re}s>2)
$$

and holomorphic in $\{\operatorname{Re}s>0\}\setminus Z$. In a punctured neighbourhood of any $\rho\in Z$ it has the form $\Phi(s)=c_\rho/(s-\rho)+h_\rho(s)$, with $h_\rho$ holomorphic near $\rho$ and $c_\rho\ne0$. For real $\rho\in Z$, $c_\rho$ is a positive real number.

In Lean, `CharFamily` is the character family with these weights and restrictions. The theorem `Deduction.poleData` supplies the transform and its properties.

## Integration against the ramp

Write $x_+=\max(x,0)$. The sum $S_\chi(y)$ is $\sum_{n\ge1}\Lambda(n)\chi(n)(y/n-1)_+$. Only finitely many terms can be nonzero on any bounded interval of $y$, so it is continuous there. Since $\Lambda(n)\le\log n\le n$ and $|\chi(n)|\le1$, each nonzero summand has modulus at most $y$. Thus $|S_\chi(y)|\le y^2$ for $y\ge1$. The correction is $O_\chi(y\log y+y)$ on this range. The finite weighted sum therefore satisfies the claimed measurability and growth bound.

For $\operatorname{Re}s>2$ the bound justifies absolute convergence and the substitution $y=e^u$, reducing the transform for one character to $\int_1^\infty G_\chi(y)y^{-s-1}\,dy$. For each $n\ge1$ and $\operatorname{Re}s>1$, integrate the two terms of the ramp from $n$ to infinity:

$$
\int_1^\infty (y/n-1)_+y^{-s-1}\,dy
=n^{-s}\left(\frac{1}{s-1}-\frac1s\right)
=\frac{n^{-s}}{s(s-1)}. \tag{1}
$$

For $\sigma=\operatorname{Re}s>1$, the sum of the absolute integrals after multiplication by $\Lambda(n)\chi(n)$ is bounded by $\sum_{n\ge1}(\log n)n^{-\sigma}/[\sigma(\sigma-1)]$, which converges. We may therefore sum (1) under the integral. Logarithmic differentiation of the Euler product gives

$$
-\frac{L'(s,\chi)}{L(s,\chi)}
=\sum_p\sum_{m\ge1}(\log p)\chi(p)^m p^{-ms}
=\sum_{n\ge1}\Lambda(n)\chi(n)n^{-s}.
$$

The differentiated series converges absolutely and uniformly on $\operatorname{Re}s\ge1+\epsilon$ for each $\epsilon>0$, by the same majorant. Thus the transform of $S_\chi$ is $-(L'/L)(s,\chi)/[s(s-1)]$. For nonprincipal $\chi$ write $c=(L'/L)(1,\chi)$. The transform of $cy$ is $c/(s-1)$, giving

$$
\Phi_\chi(s)=-\frac{(L'/L)(s,\chi)-sc}{s(s-1)}. \tag{2}
$$

For modulus $1$, $L(s,\mathbf 1)=\zeta(s)$. Integration by parts gives the transform of $-y\log y$ as $-1/(s-1)^2$. The transform of $(1+\gamma_E)y$ is $(1+\gamma_E)/(s-1)$. Combining these with the transform of $S_{\mathbf 1}$ gives

$$
\Phi_{\mathbf 1}(s)=-
\frac{\zeta'(s)/\zeta(s)+1/(s-1)+1-(1+\gamma_E)s}{s(s-1)}. \tag{3}
$$

## Holomorphic continuation and the residue for one character

Use the standard analytic properties of Dirichlet $L$-functions. For nonprincipal $\chi$, $L(s,\chi)$ is entire. These functions are nonzero on $\operatorname{Re}s\ge1$, with the pole of $\zeta$ at $1$ understood through its Laurent expansion $\zeta(s)=(s-1)^{-1}+\gamma_E+O(s-1)$.

For nonprincipal $\chi$ put $f(s)=L(s,\chi)$ and $\kappa=0$. For $\chi=\mathbf 1$ put $f(s)=(s-1)\zeta(s)$, with $f(1)=1$, and $\kappa=1$. In the latter case $f'(1)=\gamma_E$ and $f'/f=\zeta'/\zeta+1/(s-1)$ away from singularities. In either case $f$ is entire and $f(1)\ne0$. The two formulas become

$$
\Phi_\chi(s)=-
\frac{f'(s)/f(s)-s f'(1)/f(1)+\kappa(1-s)}{s(s-1)}. \tag{4}
$$

The numerator is holomorphic near $1$ and vanishes there, so the factor $s-1$ cancels. The remaining possible singularities in the right half-plane are at the zeros of $f$. These are isolated since $f(1)\ne0$. If $\rho$ is a zero of multiplicity $m$, write $f(s)=(s-\rho)^m q(s)$ with $q$ holomorphic and $q(\rho)\ne0$. Then

$$
\frac{f'(s)}{f(s)}=\frac{m}{s-\rho}+\frac{q'(s)}{q(s)}.
$$

The second term is holomorphic near $\rho$. The coefficient of the first term in (4) is holomorphic there, with value $-1/[\rho(\rho-1)]$ at $\rho$. Subtracting this value leaves a multiple of $s-\rho$. It follows that the only principal part is $-m/[\rho(\rho-1)(s-\rho)]$. At a point where $f$ is nonzero the transform is holomorphic and the multiplicity is taken to be zero.

## The residue of the real weighted sum

The conjugate character $\bar\chi$ is the inverse in the character group. The Dirichlet series and analytic continuation give $L(s,\bar\chi)=\overline{L(\bar s,\chi)}$. At the real point $1$ this identity conjugates the logarithmic derivative of a nonprincipal character as well. The weights and corrections in $G_\chi$ give $G_{\bar\chi}(y)=\overline{G_\chi(y)}$. Define

$$
\Phi(s)=\sum_{j\in J}\frac{a_j}{2}\bigl(\Phi_{\chi_j}(s)+\Phi_{\bar\chi_j}(s)\bigr).
$$

On $\operatorname{Re}s>2$ this is the transform of $g$ by absolute convergence and linearity. The set $Z$ is a finite union of zero sets of nonzero entire functions, restricted to the right half-plane. Thus it has no accumulation point there, and the displayed formula is holomorphic outside $Z$ in that half-plane. Values can be assigned arbitrarily at poles and at any other points where the formula does not define $\Phi$.

Now let $m_j(w)$ denote the order of the zero of $L(s,\chi_j)$ at $w$, with value zero at regular nonzero points. The order of $L(s,\bar\chi_j)$ at $\rho$ is $m_j(\bar\rho)$. Adding the principal parts computed above yields

$$
c_\rho=-\frac{1}{\rho(\rho-1)}
\sum_{j\in J}\frac{a_j}{2}\bigl(m_j(\rho)+m_j(\bar\rho)\bigr).
$$

By the definition of $Z$ at least one of these multiplicities is positive. Every weight is positive and the common factor is nonzero, so $c_\rho\ne0$. If $\rho$ is real then $0<\rho<1$ by the nonvanishing on $\operatorname{Re}s\ge1$. In that interval the common factor is positive. This gives both residue properties needed by the window lemma.

## Lean references and review

- Definitions and growth: [`Deduction.CharFamily`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/CharFamily.lean#L24) and [`Deduction.Gchi_growth`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/GchiGrowth.lean#L37).
- The ramp and the transforms: [`Deduction.mellin_ramp`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/MellinRamp.lean#L10), [`Deduction.mellin_Gchi_of_ne_one`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/mellinGchiOfNeOne.lean#L116), and [`Deduction.mellin_Gchi_modOne`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/mellinGchiModOne.lean#L115).
- The local logarithmic derivative and the single-character pole: [`Deduction.logDeriv_local`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/LogDerivLocal.lean#L9), [`Deduction.poleData_abstract`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/poleData.lean#L22), and [`Deduction.poleData_char`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/poleData.lean#L137).
- Conjugation and the finite sum: [`Deduction.Gchi_conj`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/GchiConj.lean#L38) and [`Deduction.poleData`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/poleData.lean#L248).

English translation draft checked against the Chinese proof and the pinned statements. The Chinese note records a separate Lean 4.33.1 check of eight declarations in this chain, with `propext`, `Classical.choice` and `Quot.sound` as their only axiom dependencies. See the [verification status of the original Lean project](../../STATUS.md#lean-verification--lean-核验).
