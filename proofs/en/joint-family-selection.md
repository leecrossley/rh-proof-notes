# Making nine arithmetic conditions hold on the same family

[Chinese proof](../zh/%E4%B9%9D%E9%A1%B9%E7%AE%97%E6%9C%AF%E6%9D%A1%E4%BB%B6%E6%80%8E%E6%A0%B7%E8%90%BD%E5%9C%A8%E5%90%8C%E4%B8%80%E4%B8%AA%E6%95%B0%E6%8D%AE%E6%97%8F%E4%B8%8A.md) · [Reading and review status](../../STATUS.md)

The pointwise estimate needs its arithmetic and geometric data to satisfy several bounds simultaneously. Choosing a new family for each bound would give no single family on which to apply the estimate. The selection theorem `topDesWin` combines the lower requirements before selecting the family.

## Combining finitely many lower requirements

For each $\varepsilon>0$, consider families $F$ indexed by real scales $x$ and finite sets of candidates. Each record contains field, lattice, group and weight data. Each family has a set of available scales $W_F$ and constant lists $c_{\rm pre}(F)$, $c_{\rm out}(F)$, $c_{\rm mid}(F,H)$, $c_{\rm last}(F)$, where $H$ is a height exponent.

A lower requirement $A=(a,t,m,l)$ comprises a real number $a$ and functions $t,m,l$ from finite real lists to reals. The condition `FamP.Large` means that every entry of $c_{\rm pre}$ is at least $a$, every entry of $c_{\rm mid}$ is at least $m(c_{\rm out})$, and every entry of $c_{\rm last}$ is at least $l(c_{\rm out}\mathbin{+\!\!+}c_{\rm mid})$, with concatenation denoted by $+\!\!+$. The component $t$ is retained in the record. The size condition here uses the three displayed groups of bounds.

Suppose $P_j(F,H)$ for $1\le j\le k$, with $k\ge1$, are properties on a class $\mathcal D$. For each $j$, assume there is $\varepsilon_j>0$ such that for every $0<\varepsilon\le\varepsilon_j$ there is a requirement $A_j$ for which every $(F,H)$ in the class meeting $A_j$ satisfies $P_j(F,H)$. This is the quantifier pattern `Closed`. For any $\varepsilon$ in the common range with upper endpoint $\min_j\varepsilon_j$, choose the $A_j$. Take the maximum of their real lower bounds and the pointwise maxima of their function bounds. If a family and height exponent meet the resulting requirement, evaluating the bounds at that family's own lists verifies each original requirement. All the properties hold on that one pair. This is the finite iteration of `Closed.and`.

## Inputs to the family selection theorem

Fix family classes $\mathcal C,\mathcal C',\mathcal E$ and real parameters $C_{\rm abs},C_0,e_D,e_L$. Assume $\mathcal C'\subseteq\mathcal C$ and $\mathcal C'\subseteq\mathcal E$, and assume that every family in $\mathcal E$ eventually satisfies `HypV` on all candidates. This is the localization-kernel length bound $\mathrm{VVle}(E,t,\sqrt b)$ on the candidate's host field.

The existence hypothesis supplies $\varepsilon_E>0$. For each $0<\varepsilon\le\varepsilon_E$ and every lower requirement $A$, it gives $F\in\mathcal C'$ and $H\ge0$ meeting $A$, with the following additional properties. These are the hypotheses of `DesignExists (WithTw (WithSm 𝒞′)) C0`.

- Smoothness and twisting. At sufficiently large scales, for every candidate and word $u$ indexing its local lattices, every prime factor of $D_\Gamma$ is at most $2fN(m)+1$. At places where a local label differs from the reference label, the chosen twists satisfy the specified integrality and cohomological conditions and agree with the twisting data at the conjugate places. See [the smoothness condition](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/SmoothDesignExistence/DGamSmooth.lean) and [`TwGood`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/TwGood.lean).
- Chosen scales and lattice data. For the height $H$, `ChosenE` requires three positive uniform constants that make seven conditions hold on every candidate at every sufficiently large scale. They control the number of thick points, vertices and bad orbits, the three quadratic-character estimates, the small-weight prime sums, the ratio of the rank to the determinant scale, and the lower bound on the number of words. See the [seven precise conditions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/Chosen.lean).
- Two size conditions. After a common threshold, `TuSize` requires $b^{m/2}\le T_u$ and $\log T_u\le C_Tmx^\varepsilon$ at every candidate and word. The constant $C_T$ depends on the family. Likewise `DGamSize` requires a uniform constant and threshold with $\log D_\Gamma\le C fN(m)\log(fN(m))$ for all such candidates and words.

Let $\mathcal D=\mathrm{Des}(\mathcal C,C_0)$ consist of the families in $\mathcal C$ that satisfy smoothness, twisting, `ChosenE` for some height, and the two size conditions. The existence input gives a family in $\mathcal D\cap\mathcal E$ and a witnessing height.

The theorem takes nine `Closed` properties on $\mathcal D$. Their [exact statements](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalTheoremInputs.lean) are used in the following roles:

1. `LinkN` compares the sum of local divisibility indices with the total cohomological length.
2. With the two size conditions, `LinkDIVt` turns the twisting localization coverage `LinkEta` and an aggregate divisibility bound `DIVinN` into the global data `LinkDIV`.
3. `LinkEta` gives the localization coverage.
4. `LinkIRR` bounds the relative dimension lost by a projection, giving $0\le\delta\le\exp(-x^{e_z/7})$ at sufficiently large scales.
5. `SmallLevelRankEq` identifies the local comparison ranks with the common target rank.
6. If the chosen height satisfies `ChosenE`, `NuFullF` gives finitely generated full-rank quotient lattices and `MuRank` supplies the positive comparison rank.
7. `LinkG` supplies local inclusions, quotient length bounds, count increments and uniform comparisons of the translations.
8. Under `TuSize`, `LinkS` supplies three estimates for the approximate orthogonality of the complex matrices, controlling the block and off-diagonal errors by $\exp(-x^{\varepsilon/8})$.
9. Under both size conditions, `LinkGLOBAL` uses `ChosenE`, `LinkG`, `LinkS`, `LinkIRR`, `LinkDIV` and `LinkMu` to supply constants $K,c_{HH},e_K,C_L,x_0$ and `ChainTied` data at every $x\in W_F$ with $x\ge x_0$.

The [`ChainTied` data](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/TieGlobal.lean) specify the common finite group and the candidate for each translation. They identify the lattices, weights and main term with those of the pointwise estimate and impose the required errors, cutoffs and sizes. The divisibility and loss exponents are bounded by the fixed $e_D,e_L$.

## Use the existence hypothesis once

**Conclusion.** Under these inputs there is $\varepsilon_1>0$ such that for every $0<\varepsilon<\varepsilon_1$ there is one family $F\in\mathcal E$ and there are constants $K,c_{HH},e_K,C_L,x_0$ supplying `ChainTied` at every $x\in W_F$ with $x\ge x_0$, with the stated loss exponents.

Apply the lower-requirement lemma to the nine closed properties. Use the minimum of their common bound on $\varepsilon$ and $\varepsilon_E$ as $\varepsilon_1$. For an admissible $\varepsilon$, take the common requirement and pass it to design existence. That single application chooses $F,H$. Because $F\in\mathcal D$ and the requirement is satisfied, all nine properties apply. Because $F\in\mathcal E$, the length bound is available.

Apply `divinN_of_hypV` to the length bound, property 1 and the rank equality in property 5 to obtain `DIVinN`. Property 2 applied to that bound and the coverage from property 3 gives `LinkDIV`. Next `linkMu_of_linkDIV` uses `LinkDIV`, the full-rank and positive-rank conclusions of property 6, and the two size conditions to give `LinkMu`. This controls the use of the unrounded local exponents in place of the slope change from fractional-ideal multiplication. For all sufficiently large candidates and words, the substitution costs at most $CX''$.

Now properties 7, 8 and 4 give `LinkG`, `LinkS` and `LinkIRR`. Supply those three and the two just derived to property 9. It gives the common threshold and the data at all qualifying scales. Each application used the original $F$.

In the RH route `shape_closed_link_n_of_green` uses $C_{\rm abs}=2,C_0=3,e_D=2,e_L=0$. The [pointwise argument](translation-averaging.md) then has exponent $1/2+(2+0+7)\varepsilon=1/2+9\varepsilon$. With the loss exponents fixed, the [window argument](main-theorem-and-window.md) can choose $\varepsilon$ after fixing the real part of a putative zero.

## Lean references and review

- Size and closure quantifiers are [`FamP.Large`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/ParamsHeightRankConstant.lean#L138), [`FamP.large_sup`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/ParamsHeightRankConstant.lean#L147), [`Closed.and`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/ParamsHeightRankConstant.lean#L163) and [`DesignExists`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/ParamsHeightRankConstant.lean#L187).
- See [`DesignExistsDes.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/SmoothDesignExistence/DesignExistsDes.lean) for the family classes and [`DivinNOfHypV.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/DivinNOfHypV.lean) for the cohomological implication. The rounding and size estimates use [`MuTuOfTuSize.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/MuTuOfTuSize.lean) and [`SumLogPrimeFactorsLe.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/AdmissibleParameterJoins/SumLogPrimeFactorsLe.lean).
- The construction is [`UpperTheory.Top.topDesWin`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/DesWin.lean#L11). The main caller is [`shape_closed_link_n_of_green`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/TopShape.lean#L33), with its existence input supplied through [`LinkEx.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/LinkEx.lean).

English translation draft. Separate notes describe [the length-to-divisibility implication](cohomology-and-divisibility-loss.md) and [the slope change under fractional-ideal scaling](local-lengths-and-lattice-slopes.md).
