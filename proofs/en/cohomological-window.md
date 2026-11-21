# A cohomological window from the dyadic and signed bounds

[Chinese proof](../zh/%E4%B8%8A%E5%90%8C%E8%B0%83%E9%95%BF%E5%BA%A6%E6%80%8E%E6%A0%B7%E5%BE%97%E5%88%B0%E5%85%B1%E5%90%8C%E7%AA%97%E5%8F%A3.md) · [Reading and review status](../../STATUS.md)

The cohomological window is needed before choosing the data for the prime-sum estimate. The theorem `vwinAt_of_joint` combines a bound at $2$, a positive-sign bound on the same interval, and a pointwise negative-sign bound at odd primes.

## Fields and cohomological lengths

An abelian field datum $M=(m,H)$ consists of an integer $m\ge1$ and $H\le(\mathbb Z/m\mathbb Z)^\times$. For a primitive character $\psi$ modulo $m$, put $M_\psi=(m,\ker\psi)$. Given an integer $e\ge0$ and primes $q,d$, the field class for $(M,e,q,d)$ consists of number fields $E$ admitting an embedding in $\mathbb Q(\zeta_L)$, for some common multiple $L$ of $2^{e+2},m,q,d$, with image the fixed field of the subgroup of automorphisms $\zeta_L\mapsto\zeta_L^a$ satisfying

$$
a\equiv\pm1\pmod{2^{e+2}},\qquad a\bmod m\in H,\qquad
(a/q)=(a/d)=1 .
$$

The last conditions use Legendre symbols. Lean calls this `IsCompField`, or `IsChiField` for $M_\psi$. Write $N_E$ for the least positive conductor of a cyclotomic field into which $E$ embeds and $d_E=[E:\mathbb Q]$.

Use the length $l(E,\ell,j)$ of the [localization kernel](main-theorem-and-window.md#what-the-basic-window-supply-requires) for the $-j$th cyclotomic twist with coefficients $\mathbb Q_\ell/\mathbb Z_\ell$. All finiteness and bound statements quantify over every allowed choice of algebraic closure and extensions of places. Write $\mathrm{VVle}(E,t,B)$ for finiteness at all primes and $1\le j<t$, and the bound $B$ on $\sum_{\ell\in S'}(\log\ell)\sum_{1\le j<t}l(E,\ell,j)$ for every finite prime set $S'$.

For a CM field $E$ and odd $\ell$, write $l_+$ and $l_-$ for the lengths of the eigenspaces of complex conjugation with eigenvalues $(-1)^j$ and $(-1)^{j+1}$, respectively. Write $\mathrm{VV}_\pm(E,t,B)$ for the corresponding finiteness and logarithmically weighted sum bound at odd primes only. Write $V_2(E,t,B)$ for finiteness and $\sum_{1\le j<t}l(E,2,j)\le B$, with no logarithmic factor.

## Two inputs and the conclusion

Fix $C_t\ge1$. For natural-number-valued functions $e(x),t(x)$, let $\mathrm{Adm}(A_1,e,t)$ require $e(x)\ge2$, $2^{e(x)}\le x^{A_1}$ and $2\le t(x)\le x^{C_t}$ for all $x\ge2$. Let $\mathrm{Pair}(m,q,d)$ mean that $q,d$ are prime, $q\equiv3\pmod8$, $d\equiv7\pmod{16}$, and $\gcd(qd,m)=1$.

**Joint-window input.** For every primitive $\psi$ modulo $m$, every $A_1$, $0<\varepsilon<1/52$ and functions satisfying $\mathrm{Adm}(A_1,e,t)$, there are $J>0,C,P,X_0$. For every $X\ge X_0$ and pair with $\mathrm{Pair}(m,q,d)$, $q,d>2X^{C_t}+1$, $q,d>P$ and $\log(qd)\le X^{\varepsilon/(4J)}$, there is $Y\ge X^{1/J}$ with $Y^2\le X$. For every $x\in[Y,Y^2]$ and field $E$ in the class for $(M_\psi,e(x),q,d)$, it gives

$$
V_2\big(E,t(x),\exp(x^{4\varepsilon/5})\big).
$$

For CM $E$ it also gives $\mathrm{VV}_+\big(E,t(x),(N_Et(x))^C+C\exp(x^{4\varepsilon/5})\big)$ on that same interval. This is `JointWin Ct`.

**Negative-sign input.** There is $C_b$ such that for every $M=(m,H)$, admissible choice $\mathrm{Adm}(A_1,e,t)$, $x\ge2$, pair with $\mathrm{Pair}(m,q,d)$ and CM field $E$ in the corresponding class, $\mathrm{VV}_-(E,t(x),B_-)$ holds, where $o=[(\mathbb Z/m\mathbb Z)^\times:H]$, $u=N_Et(x)$ and

$$
B_-=3d_Et(x)^2\log u+
C_b\sum_{\substack{\ell\mid o\\\ell\text{ odd prime}}}
\ell d_E^2t(x)^2\bigl(\log(\ell u)\bigr)^2.
$$

This is `ThmBc Ct`.

**Conclusion.** For every primitive $\psi$, $0<\varepsilon<1/52$, and $e:\mathbb R\to\mathbb N$ with $x^{2+8\varepsilon}\le2^{e(x)}\le2x^{2+8\varepsilon}$ for all $x\ge1$, there are $J'\ge1,X_1$ as follows. For each $X\ge X_1$ and every usable pair at $U=X^{1/J'}$, there is $Y\ge U$ with $Y^2\le X$. At every $x\in[Y,Y^2]$ and for every field $E$ in the class for $(M_\psi,e(x),q,d)$,

$$
\mathrm{VVle}\big(E,\lfloor x^{C_t}\rfloor,\exp(x^\varepsilon/2)\big).
$$

The source ultimately uses $C_t=401$ for all primitive characters.

## Fit the prime pair into the joint-window hypotheses

A usable pair, `WinPair ε U q d`, has the stated prime and congruence conditions and satisfies

$$
\frac12 U^{\varepsilon/5}<\log q\le U^{\varepsilon/5},\qquad
\frac12 U^{\varepsilon/5}(\log U)^2<\log d\le U^{\varepsilon/5}(\log U)^2.
$$

Also $q\mid d+1$ and all odd primes up to $U^{\varepsilon/5}$ divide $d+1$. The divisibility requirements are used in the later host construction.

Fix $\psi,\varepsilon,e$ as in the conclusion. Set $t(x)=\lfloor x^{C_t}\rfloor$. For $x\ge2$ we have $2^{e(x)}\ge x^2\ge4$, so $e(x)\ge2$, and $2^{e(x)}\le2x^3\le x^4$ since $2+8\varepsilon\le3$. Also $2\le t(x)\le x^{C_t}$. Thus $\mathrm{Adm}(4,e,t)$ holds. Obtain $J,C,P,X_0$ from the joint-window input and take $J'=\max(J,1)$.

For $X$ sufficiently large we have $U\ge\exp(1)$, so both log-primes are greater than $U^{\varepsilon/5}/2$. The primes therefore exceed $2X^{C_t}+1$ and $\max(P,m)$ once $X$ is large, giving coprimality with $m$. On the other hand,

$$
\log(qd)\le U^{\varepsilon/5}\bigl(1+(\log U)^2\bigr)
\le U^{\varepsilon/4}\le X^{\varepsilon/(4J)}
$$

using $1+(\log U)^2=o(U^{\varepsilon/20})$ and $J'\ge J$. Thus the joint input applies to this very pair and supplies $Y\ge X^{1/J}\ge U$, $Y^2\le X$. All later thresholds can be imposed by increasing the lower bound for $X$ so that $U$ exceeds them.

## Bound the field conductor and the negative-sign term

Fix any $x$ in this window and any indicated $E$. Since $q\equiv3\pmod4$, the quadratic Gauss sum modulo $q$ has square $-q$. The automorphism indexed by $a$ multiplies it by $(a/q)$. The subgroup defining $E$ fixes it, so $E$ contains $\sqrt{-q}$ and has no real embeddings. It is abelian over $\mathbb Q$, so complex conjugation commutes with all its embeddings and its fixed field is totally real of index two. Thus $E$ is CM and both odd-prime inputs apply.

Let $L_0=\operatorname{lcm}(2^{e(x)+2},m,q,d)$. Automorphisms trivial modulo $L_0$ belong to the subgroup defining $E$. Their fixed field is $\mathbb Q(\zeta_{L_0})$, so by the minimality of the conductor

$$
1\le N_E\le L_0\le 2^{e(x)+2}mqd,\qquad d_E\le\varphi(N_E)\le N_E.
$$

The log-prime upper bound by $U^{\varepsilon/4}$ and $x\ge U$ give $\log(qd)\le x^{\varepsilon/4}$. With $u=N_Et(x)\ge1$,

$$
\log u\le\log(qd)+(2+8\varepsilon+C_t)\log x+\log(8m)\le 2x^{\varepsilon/4}
$$

for all sufficiently large $x$. The threshold is independent of $E$. Since $d_Et(x)\le u$, $t(x)\le u$ and $\log u\le u$, the first term of $B_-$ is at most $3u^3\le3u^4$. Each summand without $C_b$ is at most $\ell^3u^4$. Thus with $K=3+|C_b|\sum_{\ell\mid o,\ \ell\text{ odd prime}}\ell^3$,

$$
B_-\le Ku^4\le K\exp(8x^{\varepsilon/4}).
$$

## Add the lengths and absorb the constants

At an odd prime $\ell$, complex conjugation acts $\mathbb Z_\ell$-linearly on the localization kernel. It commutes with localization up to permutation of the places over $\ell$, which preserves the vanishing at all these places. Write $c$ for this involution and $s=(-1)^j$. Since $2$ is invertible in $\mathbb Z_\ell$, $(1+sc)/2$ and $(1-sc)/2$ are projections with sum $1$, product $0$, and images the eigenspaces of eigenvalues $s$ and $-s$. Thus the kernel is their direct sum, and its length is the sum of the two lengths. It is finite by the signed inputs.

For any finite prime set, separate the prime $2$, using its bound with the factor $\log2$. The odd primes use the direct sum and both signed inputs. The resulting upper bound on the weighted sum is

$$
\exp(x^{4\varepsilon/5})\log2
+u^C+C\exp(x^{4\varepsilon/5})+K\exp(8x^{\varepsilon/4}).
$$

Take $D=\max(8,2|C|,1)$ and $M_*=\log 2+1+|C|+K$. By the bound on $\log u$ this sum is at most $M_*\exp(D x^{4\varepsilon/5})$. Since $4\varepsilon/5<\varepsilon$, at sufficiently large $x$ we have $\log M_*+D x^{4\varepsilon/5}\le x^\varepsilon/2$. The uniform threshold for $U$ makes this true throughout the window, proving the desired bound.

## Lean references and review

- [`vwinAt_of_joint`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CMFieldExponentialBounds/AdmissibleOfPageN.lean#L41) gives the implication, and [`vwin_of_joint`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CMFieldExponentialBounds/AdmissibleOfPageN.lean#L131) uses the cutoff $401$. The inputs are in [`PrimeSetBoundDataOfPrimitiveChar.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimeSetBoundDataOfPrimitiveChar.lean).
- The two prime size estimates are [`bigpair.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CMFieldExponentialBounds/bigpair.lean) and [`logpair.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CMFieldExponentialBounds/logpair.lean). The field results are [`IsCMFieldOfIsChiField.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CMFieldExponentialBounds/IsCMFieldOfIsChiField.lean), [`ConductorBoundsOfIsChiField.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CMFieldExponentialBounds/ConductorBoundsOfIsChiField.lean), and [`LogConductorMulHeightLeOfPageN.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CMFieldExponentialBounds/LogConductorMulHeightLeOfPageN.lean).
- [`shaLen_eq_add`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LengthEqAddEigen.lean#L88) and [`vvle_of_parts`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LengthEqAddEigen.lean#L127) add the lengths. [`ErrorTermsLeSqrtExpRpow.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CMFieldExponentialBounds/ErrorTermsLeSqrtExpRpow.lean) absorbs the errors.

English translation draft. In `jointWin_of`, `ThmBab` supplies the dyadic window with auxiliary odd-prime data and `ThmHV` applies to that same window. The negative bound is pointwise. The construction in `of_four_alt` supplies these inputs through [`JointWinOfCounts.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/JointWinOfCounts.lean) and [`HVCore.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/HVCore.lean), using the equivalence of `ThmBcFree` and `ThmBc`. See also the [finite-exception window](exceptional-twist-window.md), the [positive-sign estimates](positive-sign-cohomology-bound.md) and [negative-sign estimates](negative-sign-cohomology-bound.md), and the [common cohomological and analytic window](common-window.md).
