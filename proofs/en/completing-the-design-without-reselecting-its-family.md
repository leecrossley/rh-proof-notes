# Completing the design without reselecting its family

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Setting and statement

Fix a class $\mathcal C$ of families $F$ at small parameters $\varepsilon>0$. A family contains a finite set $I_F(x)$ of candidates at each real scale $x$. A claim that holds *eventually for every candidate* means that there is $x_0$ such that the claim holds at every $x\ge x_0$ and every $i\in I_F(x)$. Write $F$ is large for $(K,H)$ if its constant lists satisfy the lower requirement $K$ at height exponent $H$, as in the [nine-condition selection](joint-family-selection.md#combining-finitely-many-lower-requirements). For two such requirements, $K\vee K'$ takes their pointwise maxima. Largeness for $(K\vee K',H)$ is equivalent to largeness for both $(K,H)$ and $(K',H)$.

Fix $C_0\in\mathbb R$ and a threshold function $c_T\colon\mathbb R^2\to\mathbb R$. Assume `DesignChoices`: there is $\varepsilon_0>0$ such that for every $0<\varepsilon\le\varepsilon_0$ and every requirement $K$, one can choose $F\in\mathcal C$, a height $H\ge0$, and two constants $C_5,C_b>0$ with the following properties.

- $F$ is large for $(K,H)$. At the chosen height it satisfies the thick-set lower bound, the prescribed top-count bounds, the weighted bound on bad tops with constant $C_b$, the three quadratic-character estimates with constant $C_5$, and the lower bound on the number of words. These are the predicates `ThickSetEventually`, `ChosenTT`, `ChosenBad`, `ChosenQD`, and `ChosenCode`, with the exact defining inequalities given in the source below.
- Families carry two kinds of data for the character estimates. `BoxesF` supplies each candidate's six character boxes and its exceptional-character box at some scale $Y$ with $x^{1/J}\le Y\le x$. `QDRowsF` supplies the prime-size and congruence conditions on the two host primes $q,d$ and the field-size bound at a scale in the same interval. Each claim is eventual, and each can initially use its own $Y$. The final design proof below uses them as supplied.
- At every sufficiently large $x$ and every candidate and word, the denominator $D_\Gamma$ divides the Minkowski number $M(2fN(m))$, where $f$ is the field-degree parameter and $N(m)$ the dimension parameter. Also $c_T(\varepsilon,C_{YL})\le C_{Tu}$, where $C_{YL}$ and $C_{Tu}$ are two family constants.
- The tame characters have the `TameDistinctF` property, described below. The family height constant $C_F$ equals $H$, its number of words is eventually at most $C_0\Gamma_L^2 x^H+1$, and $C_{YL}\le9$.

Assume the following three properties are closed on $\mathcal C$. Closure means that for all sufficiently small positive $\varepsilon$ there is a lower requirement $K'$ such that the property holds for every $F\in\mathcal C,H$ large for $(K',H)$.

1. If $c_T(\varepsilon,C_{YL})\le C_{Tu}$, then eventually every candidate and word satisfies $b^{m/2}\le T_u$ and $\log T_u\le C_{Tu}m x^\varepsilon$. This is `TuSize`.
2. Eventually every candidate satisfies the normalized mass comparison
   $$
   C_0^{-1}\le \frac{d_u^S\Gamma_L^2}{D^\ast}\le C_0
   \quad\text{for every word }u,
   $$
   where $d_u^S$ is the dimension of the word's lowest-type space, $\Gamma_L$ the exponential scale used in the word count, and $D^\ast$ the reference normalization from the candidate. This is `ChosenProviso`.
3. Given `BoxesF`, `QDRowsF`, and `ChosenQD` for some positive $C_5$, there is $c_6>0$ such that eventually, for every candidate's character $\chi$ in the class `IsCharED`,
   $$
   \left|g_\chi(y)\right|\le y\,e^{-c_6 x^{\varepsilon/8}}
   \qquad\bigl(y\ge e^{x^{\varepsilon/3}}/3\bigr).
   $$
   Here $g_\chi$ is the [smoothed von Mangoldt sum with its main term removed](weighted-prime-sum-at-thin-scale.md). This eventual estimate is `ChosenThin`.

**Conclusion.** There is $\varepsilon_1>0$ such that for every $0<\varepsilon\le\varepsilon_1$ and every $K$, one $F\in\mathcal C$ and height $H\ge0$ meet $K$, the seven chosen conditions, `TuSize`, and `DGamSize`. The last condition means that, eventually for all candidates and words, $\log D_\Gamma\le C fN(m)\log(fN(m))$ for a uniform real constant $C$.

## Proof

Combine the three closures at the same $\varepsilon$ by the pointwise maximum of their lower requirements. Write $K'$ for this common requirement. Choose $\varepsilon_1$ to be the minimum of the three closure ranges and the existence range. For an admissible $\varepsilon$, apply `DesignChoices` once, with the requirement $K\vee K'$.

The resulting $F,H$ meet $K$ and all the supplementary lower requirements. Its numerical input $c_T(\varepsilon,C_{YL})\le C_{Tu}$ now gives `TuSize`. Its character boxes, congruence rows and quadratic-character estimates give $c_6>0$ and `ChosenThin`. The three positive constants $C_5,c_6,C_b$ witness the seven chosen conditions on the same family and height. Five of the conditions came with the choice, and the other two are the mass comparison and thin-scale estimate.

The denominator estimate uses positivity and the assumed divisibilities. Put $A=fN(m)\ge2$ in a candidate. Then $D_\Gamma\le M(2A)$, and the [Minkowski bound](minkowskis-order-bound-and-the-auxiliary-denominator.md) gives
$$
\log D_\Gamma\le\log M(2A)\le4A\log(4A)\le12A\log A.
$$
All occurrences of $D_\Gamma$ share the eventual threshold for the divisibility hypothesis, so this gives `DGamSize` with $C=12$.

## Strengthening the class in the actual call

In the main application the initial class is $\mathcal A$ with the good-twisting condition `TwGood`. Each choice already supplies divisibility of the denominators, the tame-character condition, the boxes, the congruence rows, and $C_{YL}\le9$. The tame-character condition applies at both generator primes and their indicated field places. It requires that $1$ and every value and inverse of the tame character list be distinct, that they remain distinct after taking the prime-to-$\ell$ parts away from the specified bad set, and that the character values be squares.

These five additional properties define the subclass `WithChN $\mathcal A$`. The prime factors of the Minkowski number $M(n)$ are at most $n+1$. Thus every prime factor of $D_\Gamma$ is at most $2fN(m)+1$, proving `DGamSmooth` for the same $F$. The existence statement `DesignChoices` therefore holds on the smaller class
$$
\{F\in\mathrm{WithChN}(\mathcal A):\ \mathrm{DGamSmooth}(F),\ \mathrm{TwGood}(F)\}.
$$
The quantifiers, original witnesses, and all the bounds stay the same. This is the class on which the supplementary closures in the main route are applied.

## Lean correspondence

- [`DesignChoices`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/DesignExistsOfChoices.lean#L22) is the initial choice, and [`DesignExists`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/ParamsHeightRankConstant.lean#L187) is the resulting existence statement. The precise character input and chosen inequalities are in [the definitions of the boxes and rows](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/MainIn.lean#L10) and [the definitions of the chosen conditions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/Chosen.lean#L15).
- [`designExists_of_choices`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/DesignExistsOfChoices.lean#L54) combines the closures and applies the one choice. [`dGamSize_of_dvd`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/DesignExistsOfChoices.lean#L46) uses the quantitative denominator estimate.
- [`WithChN` and `designChoices_upN`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/ClassOfRecordOfChoice.lean#L34) give the subclass and its witness data. [`dGamSmooth_of_dvd`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/AdmissibleParameterJoins/DGamMink.lean#L18) proves the smoothness assertion. [`TameDistinct`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/AlignN.lean#L10) records the precise bad-set convention.
- The closure inputs and initial choice are explicit hypotheses here. [`designExists_of_tuSize_aux4n_litThin`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/LinkEx.lean#L15) supplies the intermediate witnesses for the selection used in `topDesWin`.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
