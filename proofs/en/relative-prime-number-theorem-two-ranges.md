# Combining the two modulus ranges in the relative prime number theorem

[Chinese proof](../zh/%E7%AD%9B%E9%80%89%E6%89%80%E7%94%A8%E7%9A%84%E7%9B%B8%E5%AF%B9%E7%B4%A0%E6%95%B0%E5%AE%9A%E7%90%86%E6%80%8E%E6%A0%B7%E5%90%88%E5%B9%B6%E4%B8%A4%E4%B8%AA%E6%A8%A1%E6%95%B0%E8%8C%83%E5%9B%B4.md) · [Reading and review status](../../STATUS.md)

Write $\psi_\chi(y)=\sum_{n\le y}\Lambda(n)\chi(n)$, $\pi(X;M,b)=\#\{p\le X:p\equiv b\bmod M\}$, and $\operatorname{Li}(X)=\int_2^X dt/\log t$. For $8\mid M$ with $M>0$, call $(\chi_1,\beta)$ a candidate if $\chi_1$ is a nonprincipal quadratic character modulo $M$, $L(\beta,\chi_1)=0$, and $1-(8\log M)^{-1}<\beta<1$.

**Theorem.** There are absolute $a>0,A,C_0$ such that for each such modulus one can fix a choice $e_M$ before choosing $X$ and $b$. Use the empty choice if there are no candidates and otherwise choose a candidate. Put

$$
P(X)=\frac{\operatorname{Li}(X)-\theta\operatorname{Li}(X^\beta)}{\varphi(M)}
$$

with $\theta=\chi_1(b)$ if $e_M=(\chi_1,\beta)$, and with the second term omitted for the empty choice. For every $X\ge2$ and natural $b$ with $\gcd(b,M)=1$ and $\log X\ge C_0\log M\log(\log M+2)$,

$$
|\pi(X;M,b)-P(X)|\le
A\bigl(e^{-a\log X/\log M}+e^{-\sqrt{a\log X}}\bigr)P(X). \tag{1}
$$

This is `PNTAPRelW` used in the [quadratic-twist cancellation](one-exceptional-quadratic-twist.md).

## The chosen zero and the prime-power error

Fix the source's zero-free-region constant $0<c_Z\le1/20$. In $\operatorname{Re}s\ge1-c_Z/\log(M(|\operatorname{Im}s|+2))$ there is at most one zero of a character modulo $M$, counted across the characters, and if present it is a simple real zero of a nonprincipal real character. See the proof of the [zero-free region and uniqueness](unique-simple-exceptional-zero.md).

Choose a candidate in this region if there is one, and otherwise any candidate if one exists. A zero in the region qualifies because $c_Z\le1/20$. Define

$$
\eta=\begin{cases}1,&e_M=\varnothing,\\
\min(1,(1-\beta)\log M),&e_M=(\chi_1,\beta),\end{cases}
\qquad
M_\chi(y)=\mathbf1_{\chi=\chi_0}y-
\mathbf1_{\chi=\chi_1}\frac{y^\beta}{\beta}.
$$

Here $\chi_0$ is the principal character and the last term is omitted without an exception. We have $0<\eta\le1$. The Siegel gap input gives for every $\epsilon>0$ a $d_\epsilon>0$ with $1-\beta\ge d_\epsilon M^{-\epsilon}$ for every real zero of every nonprincipal real character of positive modulus $M$. Taking $\epsilon=1$ gives $\eta\ge d/M$ for an absolute $d>0$.

## The smaller-modulus range

The single-character estimate `psiChiBound` gives for each $0<c_Z\le1/20$ constants $c>0,C$, uniformly for characters modulo positive $M$, $y\ge2$ and $M\le e^{c\sqrt{\log y}}$,

$$
\left|\psi_\chi(y)-\mathbf1_{\chi=\chi_0}y+\sum_{\beta\in B}y^\beta/\beta\right|
\le C y e^{-c\sqrt{\log y}},
$$

where $B$ lists precisely the zeros of $\chi$ in the region. It is empty or contains one simple real zero of a nonprincipal character. The [proof of this input](small-modulus-character-sum.md) uses the contour shift for a smoothed sum and its difference.

Put $s=\sqrt{\log y}$ and $c_A=\min(c/4,c_Z)$. In the range $\log M\le c_A s$, the region's zero, if present, is the chosen one and the main terms agree. If the chosen candidate is outside the region, the region contributes no zeros. The additional main term has $y^\beta/\beta\le2ye^{-s/2}$ since $\beta\ge1/2$ and $(1-\beta)\log(2M)>c_Z$, while $\log(2M)\le2\log M\le2c_Zs$. Sum over the at most $M$ characters. The error is at most $My(|C|e^{-cs}+2e^{-s/2})$. Using $M^2\le e^{2c_As}$ and $M^{-1}\le\eta/d$ bounds it by $(|C|+2)d^{-1}y\eta e^{-c's}$ with $c'=\min(c/2,2/5)$. Thus the total error has the factor $\eta$ even in the presence of an exceptional zero.

## The larger-modulus range

This part uses two inputs. For every $0<\kappa\le1/20$, the smoothed explicit formula `ExplicitS` provides $C>0$. For $M\ge3$, every character $\chi\bmod M$ and $T\ge2$, it gives a zero set $Z_\chi$ and positive integer multiplicities $m_\chi(\rho)$, equal to one at simple zeros. It contains only zeros with $\operatorname{Re}\rho>1-\kappa$, $|\operatorname{Im}\rho|\le T+1$, and includes all zeros with $\operatorname{Re}\rho\ge1-\kappa/2$, $|\operatorname{Im}\rho|\le T$. Each window $|\operatorname{Im}\rho-v|\le1$ has total multiplicity at most $C\log(M(|v|+2))$. With a complex constant $K_\chi$ and $S_\chi(u)=\sum_{n\le u}\Lambda(n)\chi(n)(u/n-1)$, it gives for all $u\ge2$

$$
\left|\frac{S_\chi(u)}u-K_\chi-\mathbf1_{\chi=\chi_0}(\log u-1)
+\sum_{\rho\in Z_\chi}\frac{m_\chi(\rho)u^{\rho-1}}{\rho(\rho-1)}\right|
\le C\left((MT)^C u^{-\kappa/2}+\frac{\log u\,\log^2(MT)}T\right). \tag{2}
$$

The weighted zero sum `ZeroSum` provides some $0<\kappa\le1/20$ with the following property. For each $C_1$ and $A_1\ge1$ there are $c_1>0,C_2,C_3$. Assume $8\mid M$ and that the zero sets have $\operatorname{Re}\rho>1-\kappa$, $|\operatorname{Im}\rho|\le M^{A_1}+1$ with multiplicities and unit-height upper bounds as in (2), using $C_1$. Then for $y\ge2$ and $\log y\ge C_3\log M\log(\log M+2)$,

$$
W=\sum_\chi\sum_{\rho\in Z_\chi}
(m_\chi(\rho)-\mathbf1_{(\chi,\rho)=e_M})\,y^{\operatorname{Re}\rho-1}
\le C_2\eta\, e^{-c_1\log y/\log M}. \tag{3}
$$

The indicator is zero if the choice is empty.

Use the $\kappa$ of (3) in (2), with $T=M^{12}$, $\delta=M^{-5}$, and $u=(1+\delta)y$. For both $y,u$ use the common error $E=C(M^{13C}y^{-\kappa/2}+\log(2y)\log^2(MT)/T)$. Subtract the two formulas and multiply by $y(1+\delta)/\delta$. This cancels $K_\chi$ and contributes error at most $4yE/\delta$. On the arithmetic side the coefficients are one for $n\le y$ and between zero and one for $y<n\le u$. The latter terms cost at most $(\delta y+1)\log(2y)$. For the principal term the scaled $\log(1+\delta)$ differs from $y$ by at most $y\delta$, using $\delta/(1+\delta)\le\log(1+\delta)\le\delta$.

For a zero term, the scaled difference differs from $y^\rho/\rho$ by

$$
\frac{y^\rho}{\rho}\frac{1+\delta}{\delta}
\int_1^{1+\delta}t^{-2}(t^\rho-1)\,dt .
$$

Because $\operatorname{Re}\rho<1$, integrating the derivative of $t^\rho$ gives $|t^\rho-1|\le|\rho|(t-1)\le|\rho|\delta$. The displayed error is at most $\delta y^{\operatorname{Re}\rho}$. Thus the error in $\psi_\chi(y)-\mathbf1_{\chi=\chi_0}y+\sum_{\rho\in Z_\chi}m_\chi(\rho)y^\rho/\rho$ is at most

$$
4yE/\delta+20\delta y\sum_{\rho\in Z_\chi}m_\chi(\rho)y^{\operatorname{Re}\rho-1}
+4(\delta y+1)\log(2y).
$$

Replace the zero sum by the chosen main term. If the chosen pair occurs in the zero sets one copy cancels. If missing, its real zero must have $\beta<1-\kappa/2$ by the inclusion in (2), which costs at most $2yy^{-\kappa/2}$ for one character. All remaining zeros have $|\rho|\ge1/2$. Also the exceptional contribution in the unsigned multiplicity sum is at most one. Adding the bounds gives

$$
\sum_\chi|\psi_\chi(y)-M_\chi(y)|\le
22yW+M\bigl(4yE/\delta+4(\delta y+1)\log(2y)\bigr)
+20\delta y+2yy^{-\kappa/2}. \tag{4}
$$

Here $\log M>c_A\sqrt{\log y}$, so $\log(2y)\le(1+c_A^{-2})M^2$. Increasing $C_0$ in the lower bound on $\log y$ ensures $M^{13C}y^{-\kappa/2}\le M^{-8}$, $y\ge M^5$, and $y^{-\kappa/2}\le M^{-2}$. Substituting $T,\delta$ gives $O(yM^{-2})$ for all terms of (4) other than $22yW$. For $0<c_2\le c_A^2$, $M^{-1}\le e^{-c_2\log y/\log M}$ in this range. Bound the other $M^{-1}$ by $\eta/d$ and use (3) with $c_2\le c_1$. The total is $O(y\eta e^{-c_2\log y/\log M})$.

## Combine ranges and count primes

Use the smaller of the two decay constants, $a_0>0$, and both error terms in one upper bound. This gives `PsiRel`: uniformly for $8\mid M$ and $\log y\ge C_0\log M\log(\log M+2)$ with $y\ge2$,

$$
\sum_\chi|\psi_\chi(y)-M_\chi(y)|
\ll y\eta\big(e^{-a_0\log y/\log M}+e^{-a_0\sqrt{\log y}}\big).
$$

If the threshold on $\log X$ is at least $\max(2C_0,16)\log M\log(\log M+2)$, this holds throughout $\sqrt X\le y\le X$. Character orthogonality gives the main term $(y-\theta y^\beta/\beta)/\varphi(M)$ for $\psi(y;M,b)$ and the above error divided by $\varphi(M)$. Uniformly in this range bound the decay by $E_X=e^{-a\log X/\log M}+e^{-\sqrt{a\log X}}$ with $a=\min(a_0/2,a_0^2/2)$.

Partial summation with $1/\log y$ on $[\sqrt X,X]$ converts the derivative of the main term into that of $P(y)$. Since $\log y\ge\frac12\log X$, the two endpoint errors and the integral error are $O(X\eta E_X/(\varphi(M)\log X))$. The small endpoint of the main term, the terms below $\sqrt X$, and removing the higher prime powers cost $O(\sqrt X\log X)$. For the higher powers the possible bases are at most $\sqrt X$, with $O(\log X)$ exponents per base and $\Lambda(n)/\log n\le1$.

The target main term satisfies $P(X)\ge X\eta/(2\varphi(M)\log X)$. If $\theta\le0$ or there is no exception, use $\operatorname{Li}(X)\ge(X-2)/\log X$. If $\theta=1$, integrate from $X^\beta$ to $X$ and use $X-X^\beta\ge X\eta/2$, since $(1-\beta)\log X\ge\eta$ and $0<\eta\le1$. Thus the error of partial summation is $O(E_X)P(X)$. Writing $L=\log X$, we also have $P(X)\gg X/(M^2L)$ from $\eta\ge d/M$. With $M^2\le e^{L/8}$ and $\sqrt{aL}\le 2a+L/8$,

$$
\frac{\sqrt X\log X}{P(X)e^{-\sqrt{aL}}}
\ll L^2 e^{-L/2+L/8+L/8+2a}=O(1).
$$

This absorbs the last error in (1).

## Lean references and review

- [`psi_relative_near_range`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTRangeA.lean#L161) uses [`psiChiBound`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/SiegelWalfiszAPOfSiegelLower.lean#L23) and [`etaOf_lower`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTEOf.lean#L141). The selection is in [`DeuringHeilbronnM.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/DeuringHeilbronnM.lean) and the candidate condition in [`MeanSquareHypWIff.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/MeanSquareHypWIff.lean).
- The inputs and difference are [`smoothed_explicit_formula`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTExplMain.lean#L15), [`zero_sum_bound_lossy`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTZSumL.lean#L30), and [`differenced_explicit_formula`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTSharp.lean#L69). The total error is [`psi_relative_far_range`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTBAsm.lean#L15).
- [`glue_ranges`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTGlue.lean#L22) and [`prime_count_of_psi`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PrimeCountOfPsi.lean#L12) yield [`pnt_progressions_relative_weak_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTFinal.lean#L22).

English translation draft. Further inputs are the [Siegel gap](siegel-gap-from-positive-coefficients.md), the [smoothed explicit formula](smoothed-explicit-formula-near-one.md) and the [weighted zero sum with losses](weighted-zero-sum-with-logarithmic-losses.md).
