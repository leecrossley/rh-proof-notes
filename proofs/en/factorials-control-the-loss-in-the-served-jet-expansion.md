# Factorials control the loss in the served jet expansion

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Use the variables of the [phase decomposition](a-frobenius-phase-splits-into-pure-top-and-mixed-terms.md) and the integral phase $h$ there. Suppose the original series $F$ is in `InClass` for $p,h$. This means it is coefficientwise a sum $\sum_{i\ge0}p^{-i}h^i U_i$ with each $U_i$ integral, where the coefficient of total degree $d$ uses only $i\le d$. The zero constant term of $h$ makes the indicated sum valid, and the class is preserved by the integral linear substitution separating $Z,V$. Fix a product of lower minors $Q$, homogeneous of degree $L=\sum_s L_s$ with degree $L_s$ in each block $s$, and top multiindex $e=(e_{s,b})$, supported in $T$. The new differential polynomial is $V^e Q(Z)$. Pairing it with the transformed series equals pairing the original framed differential polynomial with $F$, since a linear substitution on the series transposes to the corresponding linear substitution on the differential polynomial. This follows by the chain rule for each linear differential operator. Write $D=|e|+L$, $a_s=\sum_b e_{s,b}$. Only degree $D$ matters. [`InClass`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/OddLogRelation.lean#L76) · [`EntryStar_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/NormLeOfDvd.lean#L309)

Expand $h^i$ with the four groups of summands from the phase decomposition. Let $\alpha,\beta$ be the pure and mixed multiplicities, $A=|\alpha|$, $B=|\beta|$, and $z,y$ the counts of integral high-lower-degree summands and $p$-integral correction summands. Then $i=A+B+z+y$. Their product uses top powers at least the sum of the prescribed pure and mixed powers. Any term contributing to the pairing must fit the full top multiindex $e$. The $p^y$ factor cancels that part of the explicit denominator, leaving only $p^{-(A+B+z)}$.

For the mixed lower linear forms, the pairing obeys
$$
\langle Q,(\textstyle\prod_k \ell_k^{\beta_k})G\rangle
=\Bigl(\prod_k\beta_k!\Bigr)\langle D_{\mathbf b}^{[\beta]}Q,G\rangle ,
$$
where $\ell_k(Z)=\sum_x b_{k,x}Z_x$ and $D_{\mathbf b}^{[\beta]}Q=[u^\beta]Q(Z+\sum_k u_k\mathbf b_k)$. One proves it on monomials by expanding the binomial coefficients and using $\langle Z^n,F\rangle=n![Z^n]F$. The Hasse polynomial has integral coefficients. Each direction lies in one slot, so a remaining exponent $n$ has $L-B$ lower degree, with its degree in slot $s$ at most $L_s$. Any nonzero contribution has $|n|\ge pz$, since each high-lower-degree factor uses at least $p$ of those powers. The multinomial coefficient in the expansion of $h^i$, multiplied by $\prod_k\beta_k!$, is divisible by $B!$: it equals $B!$ times the multinomial first grouping the mixed summands into a single class of size $B$. Therefore the valuation of any such contribution is at least
$$
v_p(e!)+v_p(B!)+v_p(n!) - A-B-z,
$$
with $e!,n!$ denoting products of coordinate factorials. If the total jet is nonzero, the ultrametric inequality lets us retain one nonzero contribution of maximal norm. [Conditions on a contributing monomial](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/NormNatCastLeOfDvd.lean#L386) · [One multinomial term](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/NormNatCastLeOfDvd.lean#L397) · [`TermBound_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/NormNatCastLeOfDvd.lean#L495)

It remains to bound the three factorials. Write $\ell_p(x)$ for the base-$p$ digit length of a nonnegative integer, with $\ell_p(0)=0$. Counting multiples of powers of $p$ in a factorial gives $v_p(x!)=(x-s_p(x))/(p-1)$, with digit sum $s_p(x)\le(p-1)\ell_p(x)$. Use this on $e_{s,b}\le a_s$ and on each $n_{s,a,b}\le L_s$. For the middle factorial $B!$, decompose $B=\sum_{s,e'}i_{s,e'}$ by source and shift. Its valuation dominates the sum of $v_p(i_{s,e'}!)$ by the multinomial integrality. Nonzero counts satisfy $p^{2e'+1}i_{s,e'}\le a_s$. There are at most $\ell_p(a_s)$ nonzero $e'$ at $s$, each with $\ell_p(i_{s,e'})\le\ell_p(a_s)$. Thus the total digit loss is at most
$$
\Delta=\sum_s \bigl(N_1\ell_p(a_s)+N_0N_1\ell_p(L_s)\bigr)
+\sum_{s\in T}\ell_p(a_s)^2 ,
$$
where the letter matrix has $N_0$ rows and $N_1$ columns. Since $|e|+B+|n|=D$, the three factorials contribute at least $D/(p-1)-\Delta$. Finally $z\le L/p\le\gamma L$ for $\gamma=p/(p^2-1)$, and $1/(p-1)=\gamma+\rho$ for $\rho=1/(p^2-1)$. Hence the valuation is at least
$$
\gamma|e|-A-B-\Delta+\rho D .
$$
This is `EntryStar`, with the degree and nonvanishing conditions just proved, and is the input to [the three parity bounds](odd-shifts-and-column-capacities-give-the-three-served-jet-bounds.md). [The factorial digit bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/ABArith.lean#L35) · [`gainFactorialInequality`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/ABArith.lean#L103) · [Recovering the required norm](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/NormLeOfDvd.lean#L202)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
