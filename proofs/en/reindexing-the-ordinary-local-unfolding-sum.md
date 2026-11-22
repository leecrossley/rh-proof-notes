# Reindexing the ordinary local unfolding sum

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix one ordinary step $i<m-2$ and a bad place $P$ of the Hermitian field $E$. Suppose $q=\operatorname{Norm}(P)$ is a rational prime and has valuation one at $P$. Let $\mathcal O=\mathcal O_{E,P}$ and let $K$ be the coefficient field. The source and target dimensions of the unextended spaces are $a,b$. The unfolding uses $c+1$ extra source coordinates and $c$ extra target coordinates, where $c=m-2-i\ge1$. For any base map $x:E^a\to E^b$ it produces a scalar $\Xi_P(x)$ by summing over the free entries of a larger matrix.

We prove the local change-of-variables step. A left or right parabolic move that preserves the moved lattice of large matrices and acts on the local test function with a known character gives the corresponding character on $\Xi_P$. In particular, if the induced move on $x$ is $x\mapsto x_*$, the local test function transforms by $\Phi(\sigma Y)\,a_0=b_0\Phi(Y)$, and the additive argument increases by $\eta$, then
$$
\Xi_P(x_*)\,a_0=\psi(\eta)^{-1}b_0\,\Xi_P(x).
$$
The test function includes its fixed source and target conjugating matrices and their common normalizing scalar. The function $\psi$ is defined on $E$ and is multiplicative with respect to addition on $q^{-D}\mathcal O$, with value $1$ on $\mathcal O$, for an integer $D\ge1$. Its values on $q^{-D}\mathcal O$ are nonzero. A reciprocal outside this domain is interpreted using the field convention $0^{-1}=0$. The character identity is used only in the stated additive domain. The support and stability hypotheses on the test function and finite sums are given below.

### The affine space of large matrices

Write $e'_0,\ldots,e'_c$ for the extra source basis vectors and $e_0,\ldots,e_{c-1}$ for the extra target basis vectors, with the convention $e_c=0$. Let $U_j$ in the target be the original $E^b$ together with the extra directions of index less than $j$. Use $U'_j$ for the same flag in the source. A large matrix $Y_x(t)$ has these columns:

- On the original $E^a$ it is the inclusion of $x$ in $E^b$.
- It sends $e'_0$ to $e_0$.
- It sends $e'_j$ to $e_j+z_j$ with $z_j\in U_j$ for $1\le j\le c$.

The vector $t$ consists of the coordinates of all the $z_j$. Its coordinate space is $E^d$ for $d$ free entries. Write $U(t)=Y_x(t)-Y_x(0)$, independent of $x$. A parabolic move $r$ on the target preserves each $U_j$, fixes $e_0$, and has $r e_j-e_j\in U_j$. It induces an automorphism $g$ of $E^b$. Postcomposition by $r$ therefore sends the displayed affine space for $x$ to the one for $gx$. The inverse move gives the reverse map. For a parabolic move on the source with the corresponding conditions, precomposition sends the space for $x$ to the one for $xg$. In this case use $Y_x(U'_j)\subseteq U_j$, which follows from the displayed columns. The induced map $t\mapsto Tt$ on the free entries is affine and bijective in either case. In particular,
$$
Y_{x_*}(Ts)-Y_{x_*}(Tt)=\sigma U(s-t).
$$

The additive argument $C(Y)$ sums the coefficient of $e_j$ in $Y e'_{j+1}$ for $0\le j<c$. In a target move, the coefficient of $e_j$ of the part in $U_{j+1}$ is unchanged, and the $e_{j+1}$ column of $r$ adds the coefficient of $e_j$ in $r e_{j+1}$. The last such addition is zero by $e_c=0$. In a source move, $r e'_{j+1}-e'_{j+1}$ lies in $U'_{j+1}$, and its coefficient of $e'_j$ contributes exactly its coefficient to $e_j$ after applying $Y_x(t)$. The earlier coordinates contribute zero there. The shift in $C$ is thus constant on the affine space and is the sum of the adjacent superdiagonal entries on the extra coordinates of $r$. This is the row-character argument called `n1Arg` in Lean.

### Making the parameter substitution in a finite box

Let $L_0$ be the standard lattice of all integral large matrices. The support lattice $H$ consists of the maps from the moved source lattice to the moved target lattice at $P$. Assume $q^{m_0}L_0\subseteq H\subseteq q^{-m_0}L_0$ for an integer $m_0\ge0$. Such an $m_0$ exists because the two lattices have integral bases up to finite powers of $q$: compare the bases and their inverses with the standard bases. The additional inputs are that $\Phi$ vanishes outside $H$, is invariant under additions in $qH$, and that $C(H)\subseteq q^{-D}\mathcal O$. Assume also $\sigma H=H$. These conditions are on all large matrices.

For $A\ge m_0$ and $B\ge m_0+D$, use the free-coordinate box $L_A=q^{-A}\mathcal O^d$ modulo $L_B=q^B\mathcal O^d$. Coordinate representatives are $k/q^A$ for $0\le k<q^{A+B}$. In fact the digits $0,\ldots,q-1$ represent the residue field. Subtract the first digit and divide by the uniformizer $q$ repeatedly. The difference of distinct representatives has an integer numerator whose absolute value is less than $q^{A+B}$, so agreement modulo $L_B$ forces equality. The normalized finite sum is
$$
q^{-Bd}\sum_{t\bmod L_B\ \text{in }L_A}
\Phi(Y_x(t))\psi\bigl(-C(Y_x(t))\bigr).
$$
The definition of $\Xi_P$ also divides this by a fixed relative volume of the target unipotent subgroup. The same relative volume occurs on both sides. The project assumes stabilization of the normalized sum when $A,B$ increase past the specified depths, so we may enlarge both to satisfy the stated inequalities.

The intermediate periods are
$$
M=\{u\in E^d\mid U(u)\in q^D H\}.
$$
Indeed $L_B\subseteq M\subseteq L_A$ by the two bounds on $H$ and the coordinate description of $U$. The summand is zero outside $L_A$, because a matrix in the support has all its entries in $q^{-m_0}\mathcal O$. It is invariant under $M$. For the test function this follows from $q^D H\subseteq qH$. If the test function is nonzero, the exponent changes by $-C(U(u))\in\mathcal O$, and $\psi$ is trivial there. The affine bijection $T$ sends differences in $M$ to differences in $M$ in both directions, because $\sigma H=H$.

Write $I_x(t)=\Phi(Y_x(t))\psi(-C(Y_x(t)))$. If $\Phi(Y_x(t))\ne0$, both $C(Y_x(t))$ and $C(\sigma Y_x(t))$ belong to $q^{-D}\mathcal O$. Their difference $\eta$ is in the same additive group, and the character law gives
$$
a_0 I_{x_*}(Tt)=b_0\psi(\eta)^{-1} I_x(t).
$$
When $\Phi(Y_x(t))=0$ both sides of this equality vanish by the assumed transformation of the test function. Set $f=a_0 I_{x_*}$. Both $f$ and $f\circ T$ vanish outside $L_A$, for $f\circ T$ by the pointwise identity. The map of $M$-cosets induced by $T$ bijects the nonzero cosets of $f\circ T$ with those of $f$, and all such cosets lie in $L_A$. Each $M$-coset in $L_A$ contains exactly $[M:L_B]$ classes modulo $L_B$. Their sums over the box are therefore equal. Summing the pointwise identity and multiplying by the common normalization proves the local law with shift $\eta$.

In the ordinary chain the two moved lattices are $h\Lambda_{\rm src}$ and $h'\Lambda_{\rm tgt}$, where $\Lambda_{\rm src},\Lambda_{\rm tgt}$ are the prescribed integral coordinate lattices in the large spaces. A lift $r$ belongs to the first parabolic and its conjugate $h^{-1}rh$ or $h'^{-1}rh'$ belongs to the corresponding local level group. This conjugate preserves the prescribed coordinate lattice, so the resulting precomposition or postcomposition preserves $H$. At a type prime the prescribed lattice has weight $j+1$ on the $j$-th extra coordinate, and the conjugating matrices preserve that lattice. Thus an adjacent entry in $C$ has denominator at most $q$, which is the depth there. At a twist prime the unshifted coordinates are standard. The source inverse and the target matrix scaled by $q^{i+1}$ preserve those lattices by the indexing hypotheses. Hence every entry of a supported large map lies in $q^{-(i+1)}\mathcal O$, and the depth lower bound $D\ge 2(m-1)+1$ gives $C(H)\subseteq q^{-D}\mathcal O$. This verifies the depth input at both kinds of place.

### Lean correspondence

- [`xx1`, `chArg` and `E1`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/FiniteSumNonzeroLargeDepth.lean#L568) specify the affine columns, character and normalized sum. [`E1at` and `XiAt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/FiniteSumNonzeroLargeDepth.lean#L943) specify the local test function and relative volume.
- [`affine_action`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/UnipotentRadicalsActAffineUnfoldingSpaces.lean#L81) proves the affine bijection. [`characterArgument_first_parabolic_shift`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/CharacterArgumentFirstParabolicShift.lean#L105) and [`chArg_right`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsMoveRight.lean#L18) prove the two shifts.
- [`valsQ_reps`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/RationalFractionsRepresentPrimeNormQuotient.lean#L61) verifies the rational representatives. [`sum_reps_equiv`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/CharacterArgumentFirstParabolicShift.lean#L23) proves invariance of the finite sum. [`unfold_change`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsMoveRight.lean#L53) applies it to these free parameters.
- [`chArg_depth`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/CharacterArgumentFirstParabolicShift.lean#L372) verifies the depth bound. [`xiAt_change`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsMoveRight.lean#L165) applies the calculation to the local stabilized coefficient.

Status. Source-based reconstruction draft. The local test-function transformation, support and congruence properties are inputs to this finite-sum argument. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
