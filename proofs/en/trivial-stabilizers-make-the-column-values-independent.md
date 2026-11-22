# Trivial stabilizers make the column values independent

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Setup and statement

Let $G$ be the unitary group of the column's Hermitian space of dimension $k$ over the host CM field, with totally real base $F$. Write $G_f$ for its finite adelic points and $G(F)$ for its rational points. At the specified level let $U\subseteq G_f$ be the level subgroup, with character $\xi:U\to\mathbb C^\times$. Let $C$ index a system $y_c$ of representatives for $G(F)\backslash G_f/U$. Assume each rational stabilizer $G(F)\cap y_cUy_c^{-1}$ is trivial.

For a finite list of embeddings $\rho$ of the CM field, an archimedean frame is a tuple $Z=(Z_\rho)$ of invertible complex $k\times k$ matrices. The lowest-type value space $V$ is a space of complex functions on the frames. At each embedding it has a dominant integral weight $\lambda_\rho$ and determinant exponent $s_\rho$. Its functions are of the form
$$
Z\longmapsto \prod_\rho\det(Z_\rho)^{s_\rho}\,P(Z),
$$
where $P$ is in the polynomial space spanned by the product of the corresponding tableau bases. The definition is `ValC`. This space is stable under left translation of the frames by any tuple of invertible matrices. In the polynomial model the translation acts by substituting $g_\rho Z_\rho$ and multiplying by $\prod_\rho\det(g_\rho)^{s_\rho}$. The polynomial span is invariant under this block action.

An adelic form of this type is a function $A(g,Z)$ on $G_f$ and frames with $A(g,\cdot)\in V$ and transformation law
$$
A\big(\gamma g u,\gamma_\infty Z\big)=\xi(u)\,A(g,Z)
\quad(\gamma\in G(F),\ g\in G_f,\ u\in U).
$$
Here $\gamma_\infty$ is the tuple of its matrices under the embeddings. The space `FiC` is the space obtained by taking the values of these forms on the $y_c$. Then
$$
\mathrm{FiC}=\prod_{c\in C} V.
\tag{1}
$$
For a word $u$ of the actual record $D$, the column comparison `ColsTiedSym` identifies its lowest-type space $M_u^0$ with `FiC` of its level-zero adelic data. If the stabilizers in the record are trivial, the comparison identifies them with the above stabilizers and gives
$$
\dim_{\mathbb C}M_u^0=|C|\prod_\rho\dim V_{u,\rho},
\tag{2}
$$
where the factors use the record's Harish-Chandra parameters. Formula (2) is `Mu0Tie`.

## Extension from the representatives

Each $g\in G_f$ has a decomposition $g=\gamma y_c u$. If $g=\gamma' y_{c'}u'$ is another, the double coset forces $c=c'$, and then
$$
(\gamma')^{-1}\gamma=y_c u'u^{-1}y_c^{-1}\in G(F)\cap y_cUy_c^{-1}.
$$
It follows that $\gamma'=\gamma$ and $u'=u$. Thus one can take arbitrary independent $v_c\in V$ and set
$$
A(\gamma y_cu,Z)=\xi(u)\,v_c(\gamma_\infty^{-1}Z).
\tag{3}
$$
This lies in $V$ at each $g$ by stability under left translation. Replacing $g$ by $\eta g u_0$ replaces $\gamma,u$ by $\eta\gamma,uu_0$. If the frame is simultaneously replaced by $\eta_\infty Z$, the input to $v_c$ in (3) stays the same and the character contributes $\xi(u_0)$, as required. Taking $\gamma=u=1$ gives $A(y_c,Z)=v_c(Z)$. Restriction of an admissible form already lands in $\prod_c V$, so this proves (1).

For the actual column record, the level-zero identification of frames gives an invertible change of variables on the original functions on $C$ and its archimedean domain. The membership equivalence `Mu0_iff` identifies the image of $M_u^0$ with the restricted adelic forms. The comparison of stabilizer maps is what allows triviality in the original record to be used in (3).

The determinant twisting in the definition of $V$ is nonzero on frames, and the invertible matrices form a nonempty Zariski-open subset of each matrix space. Evaluating a polynomial there is injective. Hence $V$ has the dimension of the polynomial span, namely the product over embeddings of the tableau counts. At each embedding, with the indexed entries $w_a=\lambda_{\rho,a}+k-1-a$ up to a common shift, the count is
$$
\frac{\prod_{0\le a<b<k}(w_a-w_b)}{\prod_{j=0}^{k-1}j!}.
$$
The Lean proof uses its Weyl dimension formula for the tableau count. The sequence used in the column record has entries that differ from the proof's sequence by the constant $(k-1)/2$. The Vandermonde product uses only their differences, so the dimensions agree. Finally, (1) is a product of $|C|$ copies of $V$, with $C$ finite in the record. Taking dimensions gives (2).

## The family application

Assume for each $F$ in a class and each sufficiently large scale and candidate there is a tied level-two record, with the same candidate's column data as above. This is the relevant part of `SecondChernLinkedClass`. Enlarge the common threshold to exceed $F.x_1$ and use (2) at every word of each candidate. The source also supplies the splittings of the two generator primes and of every word prime in the totally real field. These splittings and (2) give `RankTiesF`. The [short prime window](a-short-prime-window-controls-the-column-dimension.md) then uses this rank formula alongside the class-number formula.

## Lean correspondence

- [`fnOf` and `ValC`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/HermitianForms/IsLocBasis.lean#L40) define the archimedean function space and [`AdFun` and the restriction defining `FiC`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/HermitianForms/IsLocBasis.lean#L106) give the transformation rule.
- [`valC_eq` through `valC_tr`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/GlobalRankLatticeProofs/UnitTraceSumBounds/RankConditionsOfLayerTwo.lean#L45) compare the polynomial and function spaces, and [`fiC_eq_pi`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/GlobalRankLatticeProofs/UnitTraceSumBounds/RankConditionsOfLayerTwo.lean#L109) gives the extension (3).
- [`finrank_lowest_forms_space`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/GlobalRankLatticeProofs/UnitTraceSumBounds/RankConditionsOfLayerTwo.lean#L230), [`card_ssIdx_eq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/GlobalRankLatticeProofs/UnitTraceSumBounds/RankConditionsOfLayerTwo.lean#L258) and [`mu0Tie_of_sym`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/GlobalRankLatticeProofs/UnitTraceSumBounds/RankConditionsOfLayerTwo.lean#L284) supply the level-zero comparison, simultaneous shift of the Weyl parameters, and dimension formula. The tableau formula is [`weylDim_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/InputsWeyl.lean#L42).
- [`rankTiesF_of_C2S_alt` and its closure form](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/ClosedRankTiesFC2S.lean#L12) use (2) on the tied layer-two family. The two prime splittings are applied by [`rank_conditions_iff_lowest_space`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/GlobalRankLatticeProofs/UnitTraceSumBounds/LwRankTies.lean#L15). The level-zero comparison data and their construction are inputs to (2).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
