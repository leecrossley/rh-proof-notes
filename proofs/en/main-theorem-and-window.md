# How the main theorem uses the window estimate

[Chinese proof](../zh/%E4%B8%BB%E5%AE%9A%E7%90%86%E5%A6%82%E4%BD%95%E4%BD%BF%E7%94%A8%E7%AA%97%E5%8F%A3%E4%BC%B0%E8%AE%A1.md) · [Reading and review status](../../STATUS.md)

The source proves nonvanishing in the right half-plane for every primitive Dirichlet character. It applies a window criterion to a weighted sum attached to the powers of one character at a time. Here we trace the passage from the pointwise estimates and the two window constructions to this criterion, then through change of modulus and the zeta functional equation.

## A window for the powers of one character

Fix a primitive character $\psi$ of modulus $N\ge1$ and order $o$ in the character group modulo $N$. For $0\le j<o$, take the unique primitive character inducing $\psi^j$. Let $\mathcal L_\psi$ be the set obtained after removing duplicates. This is the cyclic layer `Level.cyc ψ`. It contains $\psi$ and the trivial character $\mathbf1$ of modulus $1$. Using the corrected sums $G_\chi$ defined in the [pole calculation](pole-data.md), let

$$
G_{\mathcal L}(y)=G_{\mathbf1}(y)
+\frac1{3o+1}\sum_{\chi\in\mathcal L_\psi\setminus\{\mathbf1\}}
\operatorname{Re}G_\chi(y).
$$

The weights are from `Level.wt`. A general layer can assign weight one to one distinguished nontrivial character as well. The cyclic layer has no such distinguished character.

**Conditional claim.** Fix $\lambda>1$, $B\in\mathbb R$ and $\varepsilon_1>0$. Assume that for every $0<\varepsilon<\varepsilon_1$ and every real $T$, some $Y\ge T$ satisfies $G_{\mathcal L}(y)\le y^{1/2+B\varepsilon}$ throughout $[Y,Y^\lambda]$. Then $L(s,\psi)\ne0$ for every $\operatorname{Re}s>1/2$.

For $\beta=\operatorname{Re}s>1/2$ let $d=\frac12\min(\beta-1/2,1/2)$ and $\theta=1/2+d$. Set $\varepsilon=\min(\varepsilon_1/2,d/(|B|+1))$. Then $\theta<\beta$, $\theta<1$ and $B\varepsilon\le d$. By selecting windows with $Y\ge1$, the assumed bound implies $G_{\mathcal L}(y)\le y^\theta$ on arbitrarily late windows. The [Landau window lemma](landau-window.md), with [the pole data](pole-data.md), rules out any zero of any character in the family with real part greater than $\theta$. In particular $L(s,\psi)\ne0$.

## The order of the choices

The main application takes $\lambda=3/2$. For a primitive $\psi$, the pointwise condition `GChi ψ` asks for two properties of a candidate. The distribution and explicit-formula condition `EAtH` is to hold for the cyclic layer, with log-derivative constant $4$. The candidate's field $E$ and cutoff $t$ must satisfy the cohomological length estimate $\mathrm{VVle}(E,t,\sqrt b)$, where $b$ is its scale.

In `(GChi ψ).cls λ`, a family $F$ has a set $W_F$ containing arbitrarily late complete windows $[Y,Y^\lambda]$. Above the family's threshold $x_1$, every candidate at an available point $x$ meets both requirements, and has actual scale $x$ and the precision parameter $\varepsilon$ of the family. By taking the threshold $x_1+1$, the length requirement gives the eventual uniform bound `HypV`. The first requirement gives `EFamC`, the eventual uniform explicit-formula condition. It uses constant $4$ and threshold $x_1+1$ as well.

The construction interface `TopG` applies for $\lambda>1$ and a pointwise requirement $P$. It assumes the basic window supply `HostExW λ P.req` and an eventual length bound on every candidate in every family of the corresponding class. It supplies fixed $e_D,e_L,\varepsilon_1$, with $\varepsilon_1>0$. For each $0<\varepsilon<\varepsilon_1$ one can then choose a family $F$ in the class, constants $K,c_{HH},e_K,C_L$, and a threshold $x_0$. At each $x\in W_F$ with $x\ge x_0$ the result supplies `ChainTied` data. These put the lattices, local arithmetic data and prime-sum parameters on the same candidate, with losses controlled by the fixed $e_D,e_L$.

Take $P$ to be `GChi ψ` and use the basic window supply from the next section. On the resulting family, `EFamC` holds on every sufficiently large candidate. At each sufficiently large $x$ in $W_F$, `tiedCore_of_chainTied` extracts a candidate satisfying `CoreAtH` from the supplied `ChainTied` data. The same candidate therefore satisfies both requirements for the [pointwise estimate](translation-averaging.md). After taking the maximum of the relevant thresholds, `core_gm` gives

$$
G_{\mathcal L}(x)\le x^{1/2+(e_D+e_L+7)\varepsilon}.
$$

The loss exponents precede the choice of $\varepsilon$, so the conditional claim applies with $B=e_D+e_L+7$. In the main construction the fixed choices are $e_D=2,e_L=0$, yielding $1/2+9\varepsilon$. The window property allows $Y$ to exceed every fixed threshold. This gives right-half-plane nonvanishing for every primitive character.

## What the basic window supply requires

For a number field $E$ and prime $\ell$, let $S$ be the finite places of $E$ over $\ell$. Make the allowed choices of algebraic closure, extensions of the places and cyclotomic character. Write $G_{E,S}$ for the Galois group of the maximal extension unramified outside $S$ at finite places and $G_v$ for the chosen local decomposition groups. Write $l_{E,\ell,e}$ for the length over $\mathbb Z_\ell$ of the kernel of

$$
H^1(G_{E,S},\mathbb Q_\ell/\mathbb Z_\ell(-e))
\longrightarrow
\prod_{v\in S}H^1(G_v,\mathbb Q_\ell/\mathbb Z_\ell(-e)).
$$

The coefficient module is twisted by the $-e$th power of the cyclotomic character. The condition $\mathrm{VVle}(E,t,B)$ quantifies over all allowed choices of local data. It requires all these lengths to be finite for $1\le e<t$, and for every finite set $S'$ of rational primes it requires $\sum_{\ell\in S'}(\log\ell)\sum_{1\le e<t}l_{E,\ell,e}\le B$.

The statement `VWin` starts with a primitive $\psi$, $0<\varepsilon<1/52$, and a natural-number-valued function $e(x)$ with $x^{2+8\varepsilon}\le2^{e(x)}\le2x^{2+8\varepsilon}$ for every $x\ge1$. It supplies $J\ge1$ and $X_0$. For each $X\ge X_0$ and every admissible pair $(q,d)$ at $U=X^{1/J}$ there is $Y\ge U$ with $Y^2\le X$. For every $x\in[Y,Y^2]$ and every indicated cyclotomic subfield $E$ it gives

$$
\mathrm{VVle}\big(E,\lfloor x^{401}\rfloor,\exp(x^\varepsilon/2)\big).
$$

The pair consists of primes with $q\equiv3\pmod8$, $d\equiv7\pmod{16}$ and
$U^{\varepsilon/5}/2<\log q\le U^{\varepsilon/5}$,
$U^{\varepsilon/5}(\log U)^2/2<\log d\le U^{\varepsilon/5}(\log U)^2$.
The prime $q$ and all odd primes up to $U^{\varepsilon/5}$ must divide $d+1$. An indicated field embeds as the fixed field of the following subgroup in a cyclotomic field $\mathbb Q(\zeta_M)$ with $2^{e(x)+2},N,q,d\mid M$. An automorphism $\zeta_M\mapsto\zeta_M^a$ belongs to this subgroup if $a\equiv\pm1\pmod{2^{e(x)+2}}$, $\psi(a)=1$, and $(a/q)=(a/d)=1$.

The construction `supplyChi` uses `supplyOfAdm`. It joins the [cohomological window](cohomological-window.md), the [auxiliary-prime estimates](prime-pair-selection.md) and the existence of admissible rank data supplied by `admissibleClassesTwistedChar`. For each $0<\varepsilon<1/52$ it chooses $C_{T2},C_8,C_5,c_6,C_b,x_0$, with $C_8\ge1$ and $C_5,c_6,C_b>0$, and a family of scale windows. At each scale in the family above $x_0$ there is a candidate $(R,H,q_0)$ with the rank and host properties in `RankVal` and `HostGood` and satisfying `GChi ψ`. We use that construction as an input here. The [common-window proof](common-window.md) explains why the two kinds of estimates can be used together.

## Change of modulus and reflection

Let $\chi$ be any character modulo $N\ge1$ and $\chi^*$ its inducing primitive character. For $\operatorname{Re}s>1/2$, excluding $s=1$ when $\chi$ is principal, the formula for raising the modulus is

$$
L(s,\chi)=L(s,\chi^*)\prod_{p\mid N}(1-\chi^*(p)p^{-s}).
$$

It follows from the Euler products in their half-plane of absolute convergence, and then by analytic continuation. A factor for a prime dividing the primitive conductor is one. If $\chi^*$ is principal then $\chi$ is principal as well, so the exception covers the possible pole. Every factor is nonzero since $|\chi^*(p)p^{-s}|\le p^{-\operatorname{Re}s}<1$, and the primitive factor is nonzero by the preceding argument. This yields `EveryCharacter`.

Taking modulus $1$ gives $\zeta(s)\ne0$ for $\operatorname{Re}s>1/2$ and $s\ne1$. If $s$ were a nontrivial zero to the left, then $s\ne0$ because $\zeta(0)=-1/2$. Put $z=1-s$. We have $\operatorname{Re}z>1/2$, $z\ne1$, and

$$
\zeta(s)=\zeta(1-z)=2(2\pi)^{-z}\Gamma(z)\cos(\pi z/2)\zeta(z).
$$

The constant, complex power and gamma factors are nonzero. If the cosine vanished then $z=2k+1$ with $k\in\mathbb Z$ and $k\ge0$ by $\operatorname{Re}z>1/2$. The case $k=0$ gives $s=0$, and $k\ge1$ gives a trivial zero $s=-2k$. Thus the cosine is nonzero. The right-hand zeta value is nonzero as well, a contradiction. All nontrivial zeros lie on the critical line.

## How the main declaration obtains the construction inputs

The definite-side construction in `every_character_of_theta_integrals_local_matching` uses `green_of_regular` for the finite-field character formulas. It combines this with equality of theta integrals, local matching, covolume bounds and existence of local Langlands parameters. The theorem `zero_free_all_of_green_v_win` obtains `TopG` through `shape_closed_link_n_of_green` and `forall_goal_of_shape_of_hyps`, using `supplyChi` for the other window input.

The theorem `everyCharacter_of_row` passes the Galois representation compatibility statement `Row0b` to this construction and uses `vwin_of_row` to obtain `VWin`. At the top level, `galoisLocalGlobalStrong_recParameter` supplies this compatibility. It attaches a continuous semisimple $\ell$-adic representation of the same dimension to a regular algebraic polarized cuspidal representation over a CM field, with the specified weights and compatibility at finite places. The project obtains it from `galoisRepresentations_of_thetaLift` using `tLiftK` and the geometric realization in the weight-one case.

## Lean references and review

- The final theorem is [`riemannHypothesis`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Main.lean#L4), which calls [`rhOfAll`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Supplements/Kernels/MainTheorems.lean#L9). Specialization and reflection are [`rh_of_every`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GammaFactorNonvanishing/CritLine.lean#L29) and [`rh_of_right`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GammaFactorNonvanishing/RhOfRight.lean#L5).
- The window interface and its use are [`TopG`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/ZeroFreeAllOfTopG.lean#L12), [`zeroFreeAll_of_topG`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/ZeroFreeAllOfTopG.lean#L26), and [`level_gm_le_on_family_scales`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/PrimitiveCosets/LevelGmLeOnFamilyScales.lean#L28).
- The length bounds and basic supply are [`VVle`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/ExistsPageN.lean#L12), [`VWinAt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/ExistsPageN.lean#L44), [`VWin`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/ExistsPageN.lean#L49), and [`supplyChi`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/SupplyChi.lean#L8). Change of modulus is [`imprimitive`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/Imprimitive.lean#L5).
- The assembly calls are [`everyCharacter_of_row`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/MainConclusion.lean#L7), [`every_character_of_literature_of_vWin`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/EveryCharacterOfLiteratureOfVWin.lean#L810), [`every_character_of_theta_integrals_local_matching`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/SiegelEisensteinSecondTermHypotheses.lean#L69), and [`TopPlug.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/TopPlug.lean).
- The representation input is stated in [`WeightsConjBis.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/TypeConditions/WeightsConjBis.lean), supplied in [`RowSrc.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/IntegralStructures/RowSrc.lean#L6) and constructed via [`GaloisRepresentationsOfThetaLift.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/IntegralStructures/GaloisRepresentationsOfThetaLift.lean).

English translation draft. The final declaration has no extra hypothesis. The exposition above treats the stated construction interface and basic window supply as inputs to the deduction, and locates how the project supplies each.
