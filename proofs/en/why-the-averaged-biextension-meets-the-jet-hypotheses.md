# Why the averaged biextension meets the jet hypotheses

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

The [local jet estimate](prime-powers-in-the-jet-coefficient-bound.md) assumes a coefficient-field condition, torus invariance, a restriction on low bidegrees, and two integrality conditions. This note derives all four from the construction of the averaged biextension.

## The hypotheses to prove

Use the setting of [the biextension average](why-root-of-unity-averaging-preserves-the-biextension.md), with $K,p,\sigma,d,F,\lambda,b_0,\zeta,\omega_i,\omega_i^*$, and write $b=\overline b$ for the mean. For this result we need the assumptions there on $K,p,\sigma,d,F,\zeta$ and `F1` on $b_0$, and only `OwOK` on the two lists: they have a finite common index set and consist of integral elements fixed by $\sigma^d$. We need neither the trace-duality equations nor `F2`.

The desired condition `BHyp`, with coefficient field $K$, is the conjunction of the following.

1. All coefficients of $b$ belong to $K$.
2. $b(t_\zeta Z)=b(Z)$.
3. Every nonzero monomial coefficient has positive even degree and positive odd degree, and the pair of degrees is different from $(1,1)$. Here each degree is the sum of the exponents on the slots of that parity.
4. In two families of orbit variables, write $b(e,o)$ for the series with the even slots filled by $e$ and the odd slots by $o$. Define the two defects
   $$
   \begin{aligned}
   \partial_E b(e,e';o)&=b(e+e',o)-b(e,o)-b(e',o),\\
   \partial_O b(e;o,o')&=b(e,o+o')-b(e,o)-b(e,o').
   \end{aligned}
   $$
   Each becomes equivalent to zero after the cyclic letter-log substitution in the two alphabets. In other words, its exponential after that substitution is integral and has constant term $1$.

For the even defect use $e$ and $o$ from the first alphabet and $e'$ from the second. For the odd defect use $e$ and $o$ from the first and $o'$ from the second. These are `de1` and `de2` in Lean. Only the variables of the split parity have to be duplicated. [Bidegrees, defects and the BHyp conditions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GaussJetBounds/Statement.lean#L48)

## Which monomials survive

The coefficients belong to $K$ because all formal operations take place in $K$. The torus action by $\zeta$ permutes the summands of the average, giving exact invariance before logarithmic substitution. If $b_0$ vanishes on both axes, then $\widetilde b$ does as well when either all even slots or all odd slots are set to zero. The corresponding monomials remain absent under the scaling and averaging.

A monomial of bidegree $(1,1)$ is $Z_sZ_t$ for one even index $s$ and one odd index $t$. Scaling by $t_\zeta$ multiplies it by $\zeta^{p^s-p^t}$. The exponent $p^s-p^t$ is nonzero, and its absolute value is less than $p^d-1$ since $0\le s,t<d$. Thus the multiplier is different from $1$, so exact invariance makes its coefficient zero. Equivalently, the geometric series over the cyclic group vanishes. [Invariance and low-bidegree vanishing](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/GaussSumParity/KummerThetaLogarithms/SubstZeroOfConstantCoeff.lean#L416)

## Additivity after substituting the two alphabets

First consider $\widetilde b$. In each summand, write $E$ and $E'$ for the even linear forms in the first and second alphabets after applying cyclic logarithms, and $O$ for the odd form in the first alphabet. The even defect is the sum over the indices $i$ of
$$
B(E+E',O)-B(E,O)-B(E',O),\qquad
B(G,H)=b_0(\lambda^{-1}(G),\lambda^{-1}(H)).
$$
By the [cyclic shift calculation](finding-integral-points-from-formal-logarithms.md), each individual $E,E',O$ satisfies `IP`. Their inverse logarithms are integral. The first additivity relation proved from `F1` therefore makes the displayed difference equivalent to zero. The odd defect is handled by the second additivity relation, using the two odd forms $O,O'$ and the even form $E$. Equivalence to zero is stable under finite sums, giving the two claims for $\widetilde b$. [The two defects of the sum of biextensions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/GaussSumParity/KummerThetaLogarithms/BiextensionHypothesesOfConditions.lean#L147)

Now consider $\widetilde b(t_u Z)$ for $u=\zeta^k$. It is the same formula for $\widetilde b$ with $(\omega_i^*,\omega_i)$ replaced by $(u\omega_i^*,u^{-1}\omega_i)$, by the Frobenius calculation for roots of unity. The new elements are still integral and fixed by $\sigma^d$, so the two defect results just proved still hold. Taking a defect is linear in $b$, as is the letter-log substitution. Thus each defect of $b$ after substitution is $1/(p^d-1)$ times a sum of series equivalent to zero. The unit-root coefficient recursion for the exponential of an average proves that they remain equivalent to zero. Every defect has zero constant term, and exponentiation commutes with the zero-constant substitution, so these are exactly the integral exponential conditions in item 4. [Transport of the defect bounds to the mean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/GaussSumParity/KummerThetaLogarithms/BiextensionHypothesesOfConditions.lean#L288)

The proof allows extension to a larger valued field by applying an isometric field embedding to the coefficients. The displayed identities and the integral bounds remain true under this map, and the coefficients still belong to the image of $K$. The discreteness of the norm on the coefficient field, when required by the jet estimate, follows from the hypothesis `UnrOK` on $K$.

In the application `BeStd` chooses such a mean over the completed unramified field. This field is contained in `Wfrac`, the closure of the $\mathbb Q_p$-algebra generated by the same prime-to-$p$ roots of unity. Indeed the algebra is a field before taking its closure, since the generators are algebraic, and contains the field generated by those roots over $\mathbb Q$ as well. This proves the coefficient condition `B1`. The invariance for the chosen primitive $\zeta$ gives invariance for its powers, hence for every root of order dividing $p^d-1$, which is `B2`. The two parity degrees are precisely those of `B3`. Finally `B4` uses the same two defects after interchanging the order of the orbit and copy indices, from $(\mathrm{copy},s)$ to $(s,\mathrm{copy})$. Renaming variables commutes with the exponential and with the cyclic substitution, so the integral unit conditions persist in the unit ball of `Wfrac`. [B1 through B4 for the standard mean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/StandardSeriesBConditionsLargePrime.lean#L145)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
