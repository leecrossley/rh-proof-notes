# The selected twists supply the missing design estimates

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Let $\mathcal A$ be a family class and $c_T\colon\mathbb R^2\to\mathbb R$ a threshold function. Use the following classes of families:

- $\mathrm{WithTw}(\mathcal A)$ adds the good-twisting property `TwGood`.
- $\mathcal B=\mathrm{WithTw}(\mathrm{WithSm}(\mathrm{WithChN}(\mathcal A)))$ adds five further witness properties and denominator smoothness. The five are the divisibility of the auxiliary denominators by their Minkowski numbers, the tame-character separation condition, the family character boxes, the family congruence rows, and the numerical cap $C_{YL}\le9$. See [the design completion lemma](completing-the-design-without-reselecting-its-family.md#strengthening-the-class-in-the-actual-call).

Assume:

1. The Minkowski divisibility assertion for finite subgroups of $\mathrm{GL}_n(\mathbb Q)$ in all dimensions implies `DesignChoices` for $\mathrm{WithTw}(\mathcal A)$ with constants $C_0=3,c_T$. The detailed quantifiers and data in `DesignChoices` are in the [design completion lemma](completing-the-design-without-reselecting-its-family.md#setting-and-statement).
2. For each $\varepsilon$ and $F\in\mathcal A$, there is a selection function for the full layer-two twisting record, with one threshold $x_{\mathrm{sel}}$. At every $x>F.x_1$ with $x\ge x_{\mathrm{sel}}$, it assigns that record to every candidate. This is the `TwistSelection $\mathcal A$` input. The records include columns, theta and kernel data with the necessary compatibility, local rows, a joint comparison of the local and global maps, and self-dual host data.
3. For every $\varepsilon$ and $F\in\mathcal A$, the eventual compatibility conditions collectively called `Duty` hold. They comprise fixed local pages and their window, the bound on the first modulus, tame distinctness, the chosen wall condition, usage of the prescribed tuples, and the coherent twists at all places. The [exact conjunction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/ClassOfRecordOfChoice.lean#L77) records the scope of each condition.
4. The implication $c_T(\varepsilon,C_{YL})\le C_{Tu}\Rightarrow\mathrm{TuSize}(F)$ is closed on $\mathcal B$. Here `TuSize` is the pair of bounds $b^{m/2}\le T_u$ and $\log T_u\le C_{Tu}m x^\varepsilon$, eventually for all candidates and words.
5. The property that the [class-number formula](a-short-prime-window-controls-the-column-dimension.md#the-dimension-input-on-the-selected-family) holds for all $x>F.x_1$ and all candidates is closed on $\mathcal B$.
6. The thin-scale analytic input `LitThin` holds. It supplies uniform versions of the zero-free region, primitive explicit formula, and unit-interval zero count used in the [thin-scale estimate](the-character-boxes-give-the-thin-bound-on-the-chosen-family.md).

**Conclusion.** The class $\mathcal B$ has `DesignExists` with constant $3$. In particular, there is an $\varepsilon_0>0$ such that for every $0<\varepsilon\le\varepsilon_0$ and every lower requirement $K$, some $F\in\mathcal B$ and $H\ge0$ are large for $(K,H)$ and have the seven chosen bounds, the two word-prime size bounds, and the uniform logarithmic bound on the auxiliary denominators.

## Proof

First, apply [Minkowski's theorem](minkowskis-order-bound-and-the-auxiliary-denominator.md) to the choice implication. Each chosen family already comes with the five pieces of data defining `WithChN`. The prime support of its denominator follows from the support of the Minkowski number. Thus these same choices witness `DesignChoices` on $\mathcal B$.

For $F\in\mathcal B$, its underlying class membership gives $F\in\mathcal A$. Apply the selection function at the scale of each candidate, keeping the threshold $x_{\mathrm{sel}}$. The level and column comparison in that record gives the tied data at every such scale. The fixed-page, first-modulus and tame-distinctness components of `Duty` give alignment of this same family. Together the recursive record and these alignments give `SecondLayerFamilyClass`. Forgetting the extra coefficients and maps of the recursive data leaves the tied level-two record `SecondChernLinkedClass`. The [dimension proof for independent column values](trivial-stabilizers-make-the-column-values-independent.md#the-family-application) gives `RankTiesF` from this record.

The rank ties therefore hold for every $F\in\mathcal B$. Their closure can be restricted to $\mathcal B$, since every family in $\mathcal B$ has the needed tied record. Combine it with the assumed closure of the class-number formula. The combined lower requirement makes both hold on the same $F,H$. The [short-window calculation](a-short-prime-window-controls-the-column-dimension.md) gives
$$
\tfrac13\le d_u^S\Gamma_L^2/D^\ast\le3
$$
for all sufficiently large candidates and all their words, since $3\ge e$. This is the closure of `ChosenProviso` on $\mathcal B$.

The [character-box argument](the-character-boxes-give-the-thin-bound-on-the-chosen-family.md) supplies the closure of `ChosenThin`. There are now three supplementary closures on $\mathcal B$: word-prime size, normalized mass comparison, and the thin-scale estimate. Apply [design completion](completing-the-design-without-reselecting-its-family.md#proof). The common requirement is imposed before the one application of `DesignChoices`. Thus the three closures and the size and character bounds produced by the choice all hold on the chosen family and at its chosen height.

The [nine-condition selection](joint-family-selection.md) uses this resulting existence theorem. Its actual caller takes $\mathcal A$ here to be the intersection of the ambient family class with the target class for the chosen Dirichlet character. Passing to that intersection keeps the selected witnesses for the target class throughout.

## Lean correspondence

- [`designExists_of_tuSize_aux4n_litThin`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/LinkEx.lean#L15) proves the statement, using the concrete Minkowski theorem, the strengthened class, and the three closures.
- [`TwistSelectionFunctions` and `TwistSelection`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/TSelF.lean#L15) give the quantifiers of selection. [`tied_families_of_choice_alt` through `layerTwoFamilyClass_of_linked_aligned`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/ClassOfRecordOfChoice.lean#L14) assemble the aligned records and [`SecondLayerFamilyClass.c2s`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/LayerTwoFamilyClass.lean#L34) forgets the extra kernel structure.
- [the use in `shape_closed_link_n_of_green`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/TopShape.lean#L50) restricts the choices and the two geometric closures to the intersection with the target class. The selection function, the class-number and word-prime size closures, and the original `DesignChoices` implication are explicit inputs here.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
