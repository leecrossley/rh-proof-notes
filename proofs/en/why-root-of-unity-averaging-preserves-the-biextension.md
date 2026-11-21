# Why root-of-unity averaging preserves the biextension

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Setting and statement

Use the field $K$, the prime $p>2$, the integral ring $\mathcal O$, the Frobenius lift $\sigma$ and the logarithm $\lambda$ from [Finding integral points from formal logarithms](finding-integral-points-from-formal-logarithms.md). In particular the norm of a nonzero element is a power of $p$, with $\lVert p\rVert=p^{-1}$. Use the integral formal group law $F(x,y)=\lambda^{-1}(\lambda(x)+\lambda(y))$. For two series $A,B$ in the same finite set of variables, write $A\sim B$ when their constant terms agree and $\exp(A-B)$ has integral coefficients. The exponential here is the ordinary formal exponential, distinct from the inverse $\lambda^{-1}$. This is Lean's `Simeq`. Series equivalent to zero are closed under addition and negation, because their exponentials are integral units with constant term $1$.

Take $b_0(x,y)\in K[[x,y]]$. The two hypotheses on it are as follows.

- `F1` requires divisibility by $xy$ and additivity modulo $\sim$ in each argument for the law $F$. In the first argument this is $b_0(F(x,x'),y)-b_0(x,y)-b_0(x',y)\sim0$, and in the second it is $b_0(x,F(y,y'))-b_0(x,y)-b_0(x,y')\sim0$.
- `F2` requires that for every $c\in\mathcal O$ fixed by $\sigma^2$,
  $$
  b_0([c](x),y)\sim b_0(x,[\sigma(c)](y)),\qquad [c](x)=\lambda^{-1}(c\lambda(x)).
  $$
  Lean quantifies over series satisfying $\lambda(e(x))=c\lambda(x)$ and the corresponding equation for $\sigma(c)$, with zero constant term. These series are unique by inversion.

Fix even $d\ge2$. Take two lists $\omega_i,\omega_i^*$, $1\le i\le d/2$, of integral elements fixed by $\sigma^d$ and satisfying
$$
\sum_{s\ \mathrm{even}}\sigma^s(\omega_i\omega_j^*)=\delta_{ij}
$$
with $0\le s<d$. These conditions are `OwOK` and `TrDual`. In additive variables $Z_s$, put
$$
E_c(Z)=\sum_{s\ \mathrm{even}}\sigma^s(c)Z_s,\qquad
O_c(Z)=\sum_{s\ \mathrm{odd}}\sigma^s(c)Z_s,\qquad
\widetilde b(Z)=\sum_i b_0\bigl(\lambda^{-1}(E_{\omega_i^*}(Z)),\lambda^{-1}(O_{\omega_i}(Z))\bigr).
$$
Set $m=p^d-1$. For an $m$-th root of unity $u\in K$, let $t_u$ act by $Z_s\mapsto u^{(-1)^s p^s} Z_s$. With a primitive $m$-th root $\zeta\in K$ define the average
$$
\overline b(Z)=m^{-1}\sum_{k=0}^{m-1}\widetilde b(t_{\zeta^k}Z).
$$
These are `beTil` and `beMean`. The claim is that for **every** family $L_s$ of zero-constant series in finitely many variables satisfying `ShiftType`,
$$
\widetilde b(t_u L)\sim\widetilde b(L)\quad(u^m=1),\qquad
\overline b(L)\sim\widetilde b(L).
$$
The statement about $t_u$ is `TilInvariantL`. Its averaged consequence is `MeanSimeqL`. [Biextension series and their hypotheses](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/GaussSumParity/TrDual.lean#L26) · [Statements for substitution and averaging](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/GaussSumParity/BiextensionPointsIntegral.lean#L13)

## Moving scalar multiplication between the two arguments

For additive series $G,H$ satisfying `IP`, let $B(G,H)=b_0(\lambda^{-1}(G),\lambda^{-1}(H))$. Their inverse logarithms are integral by the integral part lemma. All `Simeq` relations are preserved by substitution of integral series of zero constant term, since substitution commutes with formal exponentiation and preserves integral coefficients. In the `F1` defect for the first argument, substitute $\lambda^{-1}(G),\lambda^{-1}(G'),\lambda^{-1}(H)$. The addition $F$ gives $\lambda^{-1}(G+G')$, by its defining property. This proves $B(G+G',H)\sim B(G,H)+B(G',H)$. For the second argument substitute the integral points $\lambda^{-1}(G),\lambda^{-1}(H),\lambda^{-1}(H')$ in the second defect. This proves additivity there. The same reasoning with `F2` yields
$$
B(cG,H)\sim B(G,\sigma(c)H)\quad(c\in\mathcal O,\ \sigma^2(c)=c).
$$
Closure of `IP` ensures that all these inputs, including $\sigma(c)H$, satisfy the integral part condition. [Additivity and scalar transfer in logarithmic coordinates](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/GaussSumParity/KummerThetaLogarithms/SubstFirstCoboundaryThree.lean#L305)

## Trace-dual expansions

For $x$ fixed by $\sigma^d$ put $c_{ij}(x)=\sum_{s\ \mathrm{even}}\sigma^s(x\omega_i^*\omega_j)$. It is fixed by $\sigma^2$ by cycling the even $s$'s. If $x$ is integral then so is $c_{ij}(x)$. We have
$$
x\omega_i^*=\sum_j c_{ij}(x)\omega_j^*,\qquad
x\omega_j=\sum_i c_{ij}(x)\omega_i .
$$
To see the two expansions, use the square matrices $A_{j,s}=\sigma^s(\omega_j)$ and $C_{s,i}=\sigma^s(\omega_i^*)$ with $s$ running over the even indices. The duality equations say $AC=1$, hence $CA=1$. For the first expansion, insert the sum over $s$ defining $c_{ij}(x)$ in its right side. The sum over $j$ gives $(CA)_{0,s}$ and leaves only $s=0$, giving $x\omega_i^*$. In the second expansion the sum over $i$ instead gives $(CA)_{s,0}$, leaving $x\omega_j$. [Trace-dual expansions from the two inverse matrices](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/GaussSumParity/KummerThetaLogarithms/TilInvariantLOf.lean#L150)

For $u^m=1$, both $\sigma(u)$ and $u^p$ are units and $m$-th roots of unity congruent modulo $p$. The quotient is an $m$-th root $v\equiv1\bmod p$. The sum $1+v+\cdots+v^{m-1}$ is congruent to $m$ modulo $p$ and is a unit, since $m\equiv-1\bmod p$. In the identity $0=v^m-1=(v-1)(1+\cdots+v^{m-1})$ this gives $v=1$. Consequently $\sigma^s(u)=u^{p^s}$, and $\sigma^d(u)=u$. Thus the torus substitution on the even and odd forms replaces $\omega_i^*$ by $u\omega_i^*$ and $\omega_i$ by $u^{-1}\omega_i$, respectively. [Frobenius on the prime-to-(p) roots of unity](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/GaussSumParity/KummerThetaLogarithms/ExponentialSpecification.lean#L148) · [Torus substitution on the parity forms](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/GaussSumParity/KummerThetaLogarithms/SubstZeroOfConstantCoeff.lean#L211)

## The invariance after logarithmic substitution

Write $c_{ij}=c_{ij}(u)$. On the even form the first expansion gives $E_{u\omega_i^*}(L)=\sum_j c_{ij}E_{\omega_j^*}(L)$, since $\sigma^s c_{ij}=c_{ij}$ for even $s$. Each of the even and odd forms under consideration satisfies `IP` by the cyclic shift calculation, also for the integral fixed elements $u\omega_i^*,u^{-1}\omega_i$. Applying additivity and scalar transfer now gives
$$
\begin{aligned}
\sum_i B(E_{u\omega_i^*}(L),O_{u^{-1}\omega_i}(L))
&\sim\sum_{i,j} B(c_{ij}E_{\omega_j^*}(L),O_{u^{-1}\omega_i}(L))\\
&\sim\sum_j B\!\left(E_{\omega_j^*}(L),\sum_i \sigma(c_{ij})O_{u^{-1}\omega_i}(L)\right).
\end{aligned}
$$
The second expansion gives $\omega_j=\sum_i c_{ij}u^{-1}\omega_i$, and in the odd form $\sigma^s c_{ij}=\sigma(c_{ij})$. The second argument is therefore $O_{\omega_j}(L)$. This proves $\widetilde b(t_u L)\sim\widetilde b(L)$. [Proof of invariance after substitution](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/GaussSumParity/KummerThetaLogarithms/TilInvariantLOf.lean#L213)

Finally each difference in the average is equivalent to zero, so their sum $\Psi$ has integral exponential. Dividing $\Psi$ by $m$ preserves this property. Indeed $V=\exp(\Psi/m)$ has constant term $1$ and satisfies $V^m=\exp(\Psi)$; its degree-$n$ coefficients in this equation are $m$ times those of $V$ plus expressions in lower degrees. Since $m$ is a unit, induction gives integrality of $V$. This recovers the averaging step for the integer $m$. Lean obtains the same closure using its module rule for integral exponential classes. The result gives an integral factor when the mean replaces the sum of the original $b_0$'s in the theta expansion. [Averaging the equivalence](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/GaussSumParity/KummerThetaLogarithms/TilInvariantLOf.lean#L302)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
