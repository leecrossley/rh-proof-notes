# An elliptic quotient keeps cancellations in a theta translate sum

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $q$ be split in the CM base of discriminant $-d$, with $d$ prime and $d\equiv7\bmod16$. Use its good curve model, multiplicative chart of scale $\omega$, and normalized even theta $\theta$, whose zeros lie in $1/2+\mathcal O$ and with $\theta(0)=1$. Let $s_1,\ldots,s_m,t$ be complex torsion parameters modulo $\mathcal O$ killed by integers prime to $q$, and $a\ge0$, $c_j\in\mathbb C_q$, and $B\ge0$. Write $U_s$ for Heisenberg translation, and $\widehat G$ for the chart Taylor series with coefficient embedding $\iota$. If
$$
S(X)=\sum_j c_j\,\widehat{U_{s_j}\theta}(X)^a
$$
has every coefficient of norm at most $B$, the same is true of $\sum_j c_j\,\widehat{U_tU_{s_j}\theta}(X)^a$. The proof uses the following curve estimates. [The split CM isogeny](a-split-cm-isogeny-forces-integrality-of-the-even-theta-series.md) gives the integral chart series of the base theta. If the translating point is outside $1/2+\mathcal O$, its theta translate also has integral chart series. The quotients after clearing period denominators have their poles on the corresponding half-period cosets. [The elliptic bounded-series translation lemma](a-pole-free-residue-disc-preserves-the-elliptic-coefficient-bound.md) applies when the elliptic function and its translate are analytic at zero and the translated series has finite coefficient bound. Pole avoidance for the original function is its remaining local hypothesis. In this application the corresponding pole avoidance for the translate supplies its finite coefficient bound. It says translation by a point outside that disc preserves an upper bound on the coefficients. A prime-to-$q$ torsion parameter inside the disc is zero modulo the period lattice.

### Keeping the same sum through translation

Choose a common denominator $L>0$ prime to $q$ for all $s_j,t$, so $Ls_j,Lt\in\mathcal O$. Put $t'=t/L$. For now suppose $t\notin1/2+\mathcal O$. Form one elliptic function containing the entire linear combination,
$$
\phi(z)=\sum_j\iota^{-1}(c_j)\left(\frac{U_{s_j}\theta(Lz)}{\theta(Lz)}\right)^a.
$$
The common denominator makes all the ratios elliptic. The chart for $\theta(Lz)$ is integral with constant $1$, so its inverse also has integral coefficients, by solving its product with the original series degree by degree. Substitution by $(1+X)^L-1$ and its inverse are integral. Hence dividing the rescaled $S$ by this common power shows that the chart of $\phi$ has coefficient bound $B$. In particular this incorporates cancellations among the original terms.

The elliptic function $\phi$ is analytic near zero, and $\phi(z+t')$ is also analytic there because $\theta(t)\ne0$. The scaled quotient pole theorem gives the avoidance of the small residue disc for both functions, using the two excluded half-period cases $0$ and $t$. If $t'$ is small, it is a period because $L^2t'=Lt\in\mathcal O$ and $L$ is prime to $q$. Otherwise apply the elliptic translation lemma. In both cases $\phi(z+t')$ has the same coefficient bound. Multiplying by the integral chart of $U_t\theta(Lz)^a$ now gives the bound for the rescaled target sum, since the translation on each term is multiplication by the same Heisenberg factor and shift of its argument. Undo the scale $L$ by the inverse integral substitution.

### When the translating point is a half-period

Suppose $t\in1/2+\mathcal O$. If $Nt\in\mathcal O$ for a positive integer $N$ prime to $q$, then $N/2\in\mathcal O$, hence $N$ is even. Therefore $t/2$ still has order prime to $q$, since $N^2t/2=(N/2)(Nt)$ is integral. Moreover $t/2\notin1/2+\mathcal O$, since twice that coset is contained in $\mathcal O$. Apply the preceding estimate twice with translating point $t/2$. After the first application the translates can be written in the same form by absorbing the Heisenberg phases into the $c_j$ and replacing $s_j$ by $s_j+t/2$. The inequality concerns the entire sum at each step. The two equal translations compose to $U_t$, since the alternating self-pairing of $t/2$ is zero. This proves the full assertion.

### Lean correspondence

- [`translate_bd`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/TranslateCoprimeOrderNotIncreaseThetaCombNorm.lean#L114) follows the elliptic quotient and proves the bound in the first case.
- [`norm_law`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/NormTranslatePowerCombLeCoprimeTranslation.lean#L51) treats the half-period using the two successive translates.
- [`thetaLaws_unit_period`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/ThetaLawsUnitPeriod.lean#L56) uses this inequality, together with the [torsion shift](the-torsion-shift-extends-to-prime-to-p-theta-translates.md), in the chart laws for the moment argument.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
