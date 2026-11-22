# Changing the orthonormal basis of a kernel

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix the host and inert prime as in [the host integrality theorem](how-inert-kernel-integrality-supplies-the-host-expansion.md), and one integral discriminant-one model $W$ of the transported host lattice. Work over $R=\mathcal O_{\mathbb C_p}$. Let $b,b'$ be two $K$-orthonormal bases of the same localized homomorphism lattice $Y_{(p)}$, and let $G$ be any formal series in the rectangular matrix-entry variables. If
$$
G(a B_b(\ell(T_j))_j)\,Q(T),\qquad
Q(T)=\prod_j A_W(T_j)^{-1}
$$
is integral, then the same expression with $b'$ is integral. Here $a$ is the scalar on logarithmic coordinates of $W$, $\ell=\ell_W$, and $A_W$ is the modified sigma correction in [the dictionary](the-curve-dictionary-transports-kernel-integrality.md). If the hypothesis for $b$ holds for every such model, the conclusion holds for every model and every $b'$.

The local curve inputs are as follows. Let $\mathcal O_{K,p}$ be the ring of integers of the completion of $K$ at the inert prime, embedded at the chosen host embedding. Write $P\oplus Q$ for the integral formal addition on $W$, $[u]P=\ell^{-1}(u\ell(P))$, and $f=-\log A_W$. For every $u\in\mathcal O_{K,p}$, $[u]$ is integral. The defect $C(P,Q)=f(P\oplus Q)-f(P)-f(Q)$ is biadditive modulo the subgroup of series $H$ with $H(0)=0$ and $\exp H\in 1+(T)R[[T]]$. Finally, for $u$ in the global ring of integers with norm prime to $p$, $f([u]T)\equiv N(u)f(T)$ in this same sense. The [good-model phase proof](integral-cm-actions-and-phase-in-the-good-model-parameter.md) supplies these three inputs by transporting the integral endomorphisms, sigma cube and prime-to-$p$ isogeny identities to the ordinary model coordinate. The norm input concerns the actual $A_W$, whose comparison with the modified sigma function is part of the dictionary.

For clarity, these inputs imply two rules for arbitrary $u\in\mathcal O_{K,p}$:
$$
f([u]P)\equiv N(u)f(P),\qquad
C([u]P,Q)\equiv C(P,[\bar u]Q).
$$
The coefficient relation is closed under limits: any coefficient of a substituted formal exponential is a polynomial in finitely many coefficients of its zero-constant exponent. It is also stable under addition, integral substitution and multiplication by a scalar in $\mathbb Z_p$. For the last assertion take a sequence of integers converging to the scalar and use that integral units can be raised to any integer power. The first rule is thus known for all units by density. For the scalar $2$, the norm rule and biadditivity give $C(P,P)\equiv2f(P)$. Expanding $C(P\oplus Q,P\oplus Q)$ now also recovers additivity of $f$ with its stated defect. For the trace rule at $u$, write
$$
C([u]P,P)\equiv\operatorname{Tr}(u) f(P).
$$
Indeed it holds when $u$ and $1+u$ are units, by subtracting the two norm terms from $f([1+u]P)$. Every residue in $\mathbb F_{p^2}$ is a sum of two residues outside $\{0,-1\}$: at most four choices for the first summand are forbidden. Lift them to write any $u$ as such a sum and use biadditivity. In the same way every $u=v+w$ is a sum of two units. Expanding $f([u]P)$ at that decomposition, the cross term is $C([v]P,[w]P)$. Subtracting this from the identity under the common unit $[v]$, or using the trace rule on $w/v$ with $[v]P$, identifies it with $N(v)\operatorname{Tr}(w/v) f(P)$. This proves the first rule for all $u$. Polarizing that rule gives $C([u]P,[u]Q)\equiv N(u) C(P,Q)$. For a unit $u$, substitute $[u^{-1}]Q$, and use $\mathbb Z_p$-linearity of the defect in the second slot (by integer multiples and density). The resulting adjoint rule extends to all $u$ by decomposition into two units.

Now write $b'_k=\sum_j b_j M_{jk}$. The entries of $M$ belong to the localized ring of integers because both lists are bases there. Orthonormality gives $\overline M^{\,t}M=1$. Every host embedding used in the entries has the same restriction to $K$, so
$$
S_j(T)=\bigoplus_k [M_{jk}]T_k
$$
in the corresponding $p$-adic embedding is an integral substitution, with $\ell(S_j)=\sum_k M_{jk}\ell(T_k)$. Consequently $B_b(\ell(S_j))_j=B_{b'}(\ell(T_k))_k$. For its effect on $Q$, expand $f(S_j)$ by repeated use of the defect. The terms with one index sum to
$$
\sum_{j,k}N(M_{jk}) f(T_k)=\sum_k f(T_k).
$$
For each $k<l$, the terms with two indices have sum
$$
\sum_j C([M_{jk}]T_k,[M_{jl}]T_l)
\equiv C\!\left(T_k,\left[\sum_j\overline{M_{jk}}M_{jl}\right]T_l\right)=0.
$$
These two cancellations prove $\sum_j f(S_j)\equiv\sum_k f(T_k)$. Since $Q=\exp(\sum f)$, the ratio $Q(T)/Q(S(T))$ is integral with constant $1$. Substitute $S$ in the integral expression for $b$ and multiply by this ratio. That gives the expression for $b'$. The same argument works for completed orthonormal frames, where the entries are in the inert quadratic valuation ring and conjugation acts by its nontrivial automorphism.

**Lean correspondence.** The ordinary basis matrix and change of variables are [`basisInv_of_unitSubst`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/InertKernelTheory/InertCoprimeLemmas/IntBasis.lean#L274) and [`unitSubst_of_loc`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/InertKernelTheory/InertCoprimeLemmas/UnitSubstOfLoc.lean#L483). The construction of $S$ and the correction factor is [`IntegralUnitSubstitution.core`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/InertKernelTheory/InertCoprimeLemmas/IntUnit.lean#L202). The extension from units and the adjoint identity are proved in [`norm_units_of_calculation`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/PowerSeriesNormUnits/NormUnitsOfCalculation.lean#L45) and [`core_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/ConjugateNormBound/BeConjNormOfIntInv.lean#L85). The single-index and pair-index cancellation is [`phGramG_holds` and `gramUnitEq_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/GlobalRankLatticeProofs/UnitTraceSumBounds/LevelRestrictionOfGroupLawHolds.lean#L29). The endomorphism integrality input is [`endomorphisms_integral_inert`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/InertKernelTheory/InertCoprimeLemmas/EndInt.lean#L307). This note proves the basis change from the stated curve inputs.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
