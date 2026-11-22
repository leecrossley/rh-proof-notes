# The character boxes give the thin bound on the chosen family

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Let $F$ be a family at parameter $\varepsilon$. Its size parameter $J$ satisfies $J\ge1$, and the scale records give $\varepsilon>0$. At scale $x$, let $D=D(x,i)$ be a candidate record with host primes $q,d$, conductor-bound integer $N_E=Q_Sqd$, and Artin map $\operatorname{art}$ on the units modulo the host conductor. The characters under consideration are the primitive Dirichlet characters $\chi$ agreeing, on integers prime to that conductor, with $\psi\circ\operatorname{art}$ for some complex character $\psi$ of the record's finite group. This condition is `IsCharED`.

Set
$$
U_1(Y)=e^{Y^{\varepsilon/5}},\qquad U_2(Y)=e^{Y^{\varepsilon/5}(\log Y)^2}.
$$
Assume `BoxesF` and `QDRowsF`. Each holds eventually, meaning for all $x$ beyond a family threshold and for every candidate at $x$. Their following parts are used.

- The boxes give a witness $Y_B\in[x^{1/J},x]$ with `BoxE`. Write $Q_S^{\rm odd}$ for the odd part of $Q_S$. For each real character in `IsCharED` of modulus $N$, if $d\mid N$, the box asserts `GoodFor` at height $8Q_S^{\rm odd} U_1(Y_B)U_2(Y_B)$. If $q\mid N$ and $d\nmid N$, it asserts `GoodFor` at height $8Q_S^{\rm odd}U_1(Y_B)$. For a height $Q$, `GoodFor` requires a primitive real character, $N\le Q$, and nonvanishing at $\Re s>1-1/400,\ |\Im s|\le Q$. The other six character box conditions in `BoxesF` have the [defining source](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/MainIn.lean#L15).
- The congruence rows give a witness $Y_R\in[x^{1/J},x]$ with $q\equiv3\bmod 8$, $d\equiv7\bmod16$, $\sqrt{U_1(Y_R)}<q\le U_1(Y_R)$, and $\sqrt{U_2(Y_R)}<d\le U_2(Y_R)$. The Kronecker character of $-d$ equals $1$ at $q$ and at every prime $p\le Y_R^{\varepsilon/5}$. The row also provides
  $$
  \log N_E\le2Y_R^{\varepsilon/5}(\log Y_R)^2.
  $$

Assume the analytic input `LitThin`. This supplies uniform positive constants in the zero-free region `adm6`, the primitive explicit formula `adm7`, and the count of zeros in a height-interval `adm11`, for all candidate records. The [thin-scale estimate](weighted-prime-sum-at-thin-scale.md) explains the analytic deduction and the role of these three inputs. The pinned proof calls the family version `proposition_six_norm_family_of_admitted`.

**Conclusion.** There are a constant $c_6>0$ and a threshold $x_0$, independent of $i,\chi,y$, such that for all $x\ge x_0$, all candidates $i$, all characters in `IsCharED`, and $y\ge e^{x^{\varepsilon/3}}/3$,
$$
|g_\chi(y)|\le y \exp(-c_6 x^{\varepsilon/8}).
$$
Here $g_\chi$ denotes the smoothed von Mangoldt sum with the appropriate main term removed. This is `ChosenThin`.

## Proof

Take $x$ above the two family thresholds and at least $2$. Since $x>1$ and $1/J>0$, each witness is greater than $1$. On $[1,\infty)$, both $t^{\varepsilon/5}$ and $(\log t)^2$ are nonnegative and increasing. Thus the row estimate gives
$$
\log N_E\le2Y_R^{\varepsilon/5}(\log Y_R)^2\le2x^{\varepsilon/5}(\log x)^2 .
$$
The prime and Kronecker conditions give `PairAt` at $Y_R$. The exception box at $Y_B$ and the upper bound on $\log N_E$ give the exact input `PropTwoSixBoxHypothesis`. This input asks for a box at some $1<Y\le x$ and the conductor bound at $x$, so $Y_B$ serves as its witness. The estimates come from the same record $D$, and the two scale witnesses can be different.

Apply the family thin-scale theorem with the constants supplied by `LitThin`. It returns $c_6>0$ and a threshold at which its implication from `PropTwoSixBoxHypothesis` holds for every candidate. Take the maximum of that threshold and the two thresholds used above. The window $y\ge e^{x^{\varepsilon/3}}/3$ and all the characters are then covered by a common $c_6$. The `Closed` form follows because the implication holds for every family that supplies the boxes and rows. One can take zero lower requirements and the parameter range $0<\varepsilon\le1$. The `ChosenQD` premise accepted by the design assembly is available there and is unused in this particular deduction.

## Lean correspondence

- [`IsCharED`, `BoxE` and `NE`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/GeneralLinearActions/FiltrationCocycleLiftCriterion.lean#L70) define the characters, boxes, and conductor-bound integer. The family inputs are [`BoxesF` and `QDRowsF`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/MainIn.lean#L26).
- [`logNE_le_of_rows`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/MainSup.lean#L18) transfers the conductor bound and [`pair_and_box_hypothesis_of_congruence_data_and_boxes`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/MainSup.lean#L48) assembles the two witnesses.
- [`proposition_six_norm_family_of_admitted`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/FirstClaimLemmaTwoFourOfLemmaTwoThree.lean#L3082) is the analytic estimate in family form. [the thin-scale family deductions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/MainSup.lean#L88) yield `ChosenThin` and its closure. The project's actual `LitThin` is supplied by [`GlobalTheory.ThinScaleLiterature.litThin`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LitThin.lean#L8), from the zero-free region, explicit formula, and zero-count theorems.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
