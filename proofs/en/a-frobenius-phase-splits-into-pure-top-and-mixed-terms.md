# A Frobenius phase splits into pure top and mixed terms

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix an odd prime $p$, a nonarchimedean normed field $K$ with $\|p\|=p^{-1}$, and an even cyclic slot set $S=\mathbb Z/(2\nu)$, $\nu\ge1$. Take integral scalars $u_s,\xi_{s,a}$ and a top-slot set $T$. With matrix variables $X_{s,a,b}$ define
$$
S_{s,a,b}(X)=\sum_{\ell\ge0}(-1)^\ell X_{s-2\ell,a,b}^{p^{2\ell}},
\qquad
h(X)=\sum_{s,a,b}u_s S_{s,a,b}(X)^p S_{s+1,a,b}(X).
$$
The series are well-defined coefficient by coefficient because the degrees tend to infinity. Replace $X_{s,a,b}$ by $Z_{s,a,b}+\xi_{s,a}V_{s,b}$ at $s\in T$, and by $Z_{s,a,b}$ otherwise. The $V$'s are top variables and the $Z$'s are lower variables. For every finite total degree cutoff $D$, the new $h$ agrees through degree $D$ with a finite sum of pure top monomials, monomials in the top variables times linear forms in the lower variables, an integral series all of whose monomials have lower degree at least $p$, and $p$ times an integral series. We identify the two explicit parts. [The substitution and the two monomial types](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/StatementE.lean#L88) · [`HhDecomp`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/StatementE.lean#L124)

Choose $E$ so $D<p^{2E}$. Delete $\ell\ge E$ from every $S$; zero-constant substitutions and multiplication cannot lower the total order of the omitted tail. Denote $V_{s,b}\xi_{s,a}$ by $T_{s,a,b}$ when $s\in T$, zero otherwise. In the integral coefficient ring modulo $p$, the $p^n$-th power of any sum is the sum of the $p^n$-th powers. Thus the first factor $S_{s,a,b}^p$ is congruent to
$$
\sum_{i<E}(-1)^i\bigl(Z_{s-2i,a,b}^{p^{1+2i}}+T_{s-2i,a,b}^{p^{1+2i}}\bigr).
$$
The second factor has the analogous sum with slots $s+1-2k$ and exponents $p^{2k}$. Oddness of $p$ preserves each sign. All discarded congruence errors are $p$ times a coefficientwise integral series. [The two Frobenius congruences](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/EDecomp.lean#L92) · [Truncating the cyclic sums](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/EDecomp.lean#L157)

A term using a $Z$ from the first factor has lower degree at least $p$. The same holds when the second factor contributes a $Z$ with $k\ge1$. The surviving pure terms take a $T$ from each factor and have top exponents $p^{1+2i}$ and $p^{2k}$ in the indicated two slots and a common column. The sole type of mixed term of lower degree below $p$ takes $T_{s-2i,a,b}^{p^{1+2i}}$ on the first side and $Z_{s+1,a,b}$ on the second side with $k=0$. At fixed $s_0=s-2i,i,b$, summing over rows $a$ makes its lower linear form
$$
\sum_a \xi_{s_0,a}^{p^{1+2i}} Z_{s_0+2i+1,a,b}.
$$
Its scalar factor is $u_{s_0+2i}(-1)^i$. Both explicit types have integral coefficients. The remaining terms have exactly the two stated forms, so this proves the decomposition. It supplies the high-cost and mixed factors used in [the factorial bound for the jet](factorials-control-the-loss-in-the-served-jet-expansion.md). [`decomposition_of_hh`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/EDecomp.lean#L498)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
