# A short prime window controls the column dimension

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## The numerical estimate

Let $f,k\ge1$ be integers with $2f\le 2^k$. Let $T\ge2$, $X>0$, $\Gamma\ge1$, $D^\ast>0$, and $d^\ast>0$ be real numbers. Suppose
$$
X^{fk}=\frac{D^\ast}{d^\ast},
\qquad
d=d^\ast(T^k-1)^f,
\qquad
Y\le T\le Y\left(1+\frac{1}{fk}\right),
\quad Y=X\Gamma^{-2/(fk)} .
$$
Then
$$
\frac12\le\frac{d\Gamma^2}{D^\ast}\le e.
$$
Also, if $a\le\log X\le b$, then
$$
a-\frac{2\log\Gamma}{fk}\le\log T\le b+\log2.
$$

Indeed, $d^\ast Y^{fk}=D^\ast\Gamma^{-2}$. For the upper bound, discard $-1$ before raising $T^k-1$ to the $f$-th power. Then
$$
(T^k-1)^f\le T^{fk}\le Y^{fk}\left(1+\frac1{fk}\right)^{fk}\le eY^{fk},
$$
using $1+z\le e^z$. For the lower bound, $f/T^k\le f/2^k\le1/2$. Bernoulli's inequality gives
$$
(T^k-1)^f=T^{fk}(1-T^{-k})^f\ge T^{fk}(1-fT^{-k})\ge \tfrac12Y^{fk}.
$$
Multiplication by $d^\ast\Gamma^2/D^\ast$ gives the bounds. The logarithmic inequalities follow from $Y\le T\le 2X$, since $\Gamma\ge1$.

## The dimension input on the selected family

Fix a family $F$ at parameter $\varepsilon$ and a real constant $C_0\ge e$. For each scale $x>F.x_1$ and candidate $i$, use its level data and put $D=D(x,i)$. The two generator primes are $g_0,g_1$, the chosen prime of word $u$ is $T_u$, and $f,k$ are the field-degree and column-rank parameters. A prime is split here when it has exactly $f$ places in the totally real field and all residue fields have size that prime. The large-generator condition is $g_j-1>2fk$ for at least one of $j=0,1$. Write $S_u$ for the finite set of column classes at the level of word $u$ and $M_u^0$ for the complex space of columns of the specified lowest type. Its dimension is denoted by $d_u^S$. The symbol $V_{u,\rho}$ is the column's highest-weight representation at embedding $\rho$, with dimension given by the corresponding Weyl dimension factor.

Assume the following two hypotheses of `chosenProviso_min`.

- At each $x>F.x_1$ and each candidate, if the large-generator condition holds and $g_0,g_1,T_u$ split, then
  $$
  |S_u|=\operatorname{mass}_k(D)\,I_\pi(D;g_0,g_1)\,(T_u^k-1)^f .
  $$
  Here $\operatorname{mass}_k(D)$ is the column genus mass and $I_\pi$ is the prescribed index at the two generator primes. This is `ClassNumberFormula₂`.
- There is a common threshold beyond which, for every candidate and word, the three primes split and triviality of the column stabilizers implies
  $$
  \dim_{\mathbb C} M_u^0=|S_u|\prod_\rho\dim V_{u,\rho}.
  $$
  This is `RankTiesF`, whose second implication is `Mu0Tie`.

**Conclusion.** Beyond a common threshold, for every candidate and word,
$$
C_0^{-1}\le \frac{d_u^S\Gamma_L^2}{D^\ast}\le C_0.
$$
In particular the constant $C_0=3$ used in design selection is admissible.

To prove this, first enlarge the rank-tie threshold to be at least $3$ and greater than $F.x_1$. For all candidates there the generator-size estimate `gBig_fam` gives $g_j-1>2fk$ for some $j$. The trivial-stabilizer theorem `column_stabilisers_trivial` says that for the actual level, this same large-generator condition kills every column stabilizer. Its two inputs are that the level is pro-$g_j$ at the designated places and that intersecting the conjugated level with the rational points of the definite unitary group gives the identity group when the large-generator condition holds. The source discharges the inputs by its level-continuity and definite-form lemmas. Use the resulting stabilizer triviality in the second hypothesis and substitute the cardinality in the first hypothesis. This gives
$$
d_u^S
=\underbrace{\operatorname{mass}_k(D)\,I_\pi(D;g_0,g_1)\prod_\rho\dim V_{u,\rho}}_{d_u^\ast}
 (T_u^k-1)^f .
$$
The reference $D^\ast$ and $d_u^\ast$ agree with the reference constants in the level-size record. In particular they are positive, and the record defines $X_u=(D^\ast/d_u^\ast)^{1/(fk)}$ and $T_u^\ast=X_u\Gamma_L^{-2/(fk)}$. The project's `T_win` condition is precisely
$$
T_u^\ast\le T_u\le T_u^\ast\left(1+\frac1{fk}\right).
$$
Here $T_u\ge2$ because it is prime, $\Gamma_L>1$ is the common exponential scale from the record, and $1\le f\le k$ implies $2f\le2^k$. Applying the numerical estimate proves the bounds between $1/2$ and $e$. They imply the displayed comparison since $e\ge2$ and $C_0\ge e$. Passing to the common threshold preserves all the hypotheses and proves `ChosenProviso`. The [design existence step](completing-the-design-without-reselecting-its-family.md) uses this comparison at the already selected height.

## Lean correspondence

- [`PowerProductTwoSidedBounds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/RankMulPowThreeHalvesLeFourthPower.lean#L306) states the real-variable estimate and [`mass_corollary`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/HookFormulaTorsion/OneAddInvPowLeExpOne.lean#L73) proves it.
- [`ClassNumberFormula₂` and `Mu0Tie`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/StandardLattice.lean#L453) give the exact rank hypotheses. [`level_rank_of_trivial_stabilisers`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/StandardLattice.lean#L468) multiplies the formulas. [`gBig_fam`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/JointsL.lean#L1144) gives the generator size.
- [the level and stabilizer lemmas](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/TheoremThreeFamilyOfFormalDegreeInput.lean#L17) give the applicable triviality result. [`T_win`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalRingCardinality/RhoDetPrimeEqMuTildeMulChiPow.lean#L153) supplies the short interval. [`proviso_e`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/MainSup.lean#L196) supplies the numerical hypotheses from the record.
- [`chosenProviso_min`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/TheoremThreeFamilyOfFormalDegreeInput.lean#L76) gives the family comparison. The two family hypotheses, and the proofs of the level-continuity and definite-form lemmas behind stabilizer triviality, are further inputs to this reconstruction.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
