# The ordinary point kernel transforms with the level characters

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix the project's Hermitian field data, admissible primes and characters, a selection of one prime over each split base prime, and a twist tuple avoiding the word prime $T=T(u)$ and both type primes. Work with a sharp chain of length $m$ and a step $0\le i<m-2$. At every layer a class label specifies local matrix groups and their level characters. For one source label $\alpha$ and target label $\beta$, take decorated lattice points $p,p'$ and frame group elements $g,g'$ at those labels. Write $k_i(p,p')$ for the coefficient-field kernel, and let $\rho_i,\rho_{i+1}$ denote the corresponding frame representations on the true weight spaces. Then
$$
k_i(gp,g'p')=\rho_{i+1}(g')\,k_i(p,p')\,\rho_i(g^{-1}).
$$

The formal hypotheses are `Fields.Ok`, `Primes.Ok`, `Chars.Ok`, `IsSel`, membership of $T(u)$ and the two type primes in the twist avoidance set, `ChIdx.Ok` for the chosen class data, the sharp condition, and `ChTh.Ok` for the adjacent true theta distribution. The use of `ChIdx.Ok` here is through the local level realizations and their characters, the translation period and stabilization of the scalar weights, and the ties identifying the normalized theta distribution with the actual coefficient kernel. All symbols used in the proof are described below.

### The local frame change

Write $\mathcal G$ for the chosen type places over the two type primes, $\mathcal Q$ for the selected twist places and $\mathcal B=\mathcal G\sqcup\mathcal Q$. This disjointness follows from twist avoidance. Write $q_P=\operatorname{Norm}(P)$ for $P\in\mathcal B$. These are degree-one, unramified places for the rational primes $q_P$. At each of them the frame $F_P$ of a decorated lattice $N$ identifies $\mathcal O_{E,P}^{N_i}$ with $N_P$. The frame group at a label consists of a rational unitary component $\gamma$, a residue matrix at each type place, and an integral matrix at each twist place.

There are integral automorphisms $\kappa_P$ for $g$ such that the new frames equal
$$
F^{\rm new}_P=\gamma F_P\kappa_P^{-1}.
$$
At a type place take $\kappa_P=(F_P^{\rm new})^{-1}\gamma F_P$. Both frames identify the same standard lattice with the moved lattice, so this change is integral with integral inverse. On reducing to the residue field, the definition of the action on the residue frame gives exactly the residue matrix of $g$. At a twist place take the indicated integral component of $g$, since the action uses its inverse on the right of the frame. Thus the local character $a_P$ of $\kappa_P$ is the level character of the corresponding component of $g$. Its product over $\mathcal B$ is the level character of $g$. The same argument at the target gives $\kappa'_P,a'_P$ and $F_P'{}^{\rm new}=\gamma'F'_P(\kappa'_P)^{-1}$.

We also need to lift each $\kappa_P$ to the local group of the larger matrix space used in the unfolding. At a label in layer $j$, let $h$ be its local conjugating matrix. The relevant group consists of first-parabolic elements $r$ with $h^{-1}rh$ in the prescribed level subgroup $J_{j,P}$. The first parabolic preserves the extra-coordinate flag, acts identically on its one-dimensional quotients above the original block and fixes the first extra vector. At a twist place the integral-frame level group is the projection of this group to the original coordinate block. It gives the required lift directly. At a type place the residue-frame level group is the reduction of that projection. Choose one element of the projection whose reduction is $\bar\kappa_P$. Dividing $\kappa_P$ by that element leaves a principal-congruence matrix $k$ on the original block. Its extension by the identity on the extra coordinates preserves the prescribed local lattice. Since $q_P$ is a uniformizer, the extension is the identity modulo $q_P$ on that lattice. The matrix $h$ preserves the lattice, so conjugation by $h$ preserves this congruence. The result belongs to $J_{j,P}$ because that group imposes only preservation of the lattice and unipotent flag conditions on its reduction at a type place. Thus $k$ also belongs to the projection. Multiplying in the projection gives the required lift of $\kappa_P$. The level-character compatibility in `ChIdx.Ok` assigns to any such lift the value
$$
a_P=\psi_P\!\bigl(n(r)\bigr)^{-1}\lambda_{j,P}(h^{-1}rh),
$$
where $\lambda_{j,P}$ is the level character on the larger matrix space, $n(r)$ is the adjacent superdiagonal sum on the extra block and $\psi_P$ is the additive character. The same compatibility assigns $a_P^{-1}$ to a lift of $\kappa_P^{-1}$.

### Periodicity of the arithmetic weight

The scalar weight $\Xi(x)$ in $k_i$ is a word-prime indicator $\phi_T(x)$ times a product of the ordinary local unfolded coefficients $\Xi_P(X_P)$, where $X_P=(F'_P)^{-1}xF_P$. The indicator requires $x$ to send each selected source lattice at $T$ into the selected target lattice and preserve its designated residue functional. Put
$$
\mathcal S=\mathcal B\cup\{P:P\mid\pi_T(u)\},\qquad
c_A=\Bigl(\prod_{P\in\mathcal B}q_P\Bigr)^A,\qquad
c_B=T\Bigl(\prod_{P\in\mathcal B}q_P\Bigr)^B.
$$
If $y\in H(N,N')$ for the local Hom module over $\mathcal S$, addition of $c_B y$ preserves $\phi_T$. At a selected prime of $T$ the perturbation maps to the target lattice, and its target residue functional is zero because $T=\pi_T\overline{\pi_T}$ lies in that prime. For $P\in\mathcal B$, the matrix of $y$ in the two lattice frames is integral. Multiplication by $c_B$ makes it divisible by $q_P^B$. The defining period of the unfolded coefficient $\Xi_P$ is addition by $q_P^B$ times any integral matrix, so that coefficient is preserved. This gives $\Xi(x+c_B y)=\Xi(x)$ on the entire ambient Hom space.

### Comparison of the transformed coefficients

Under the global change $x\mapsto\gamma'x\gamma^{-1}$, its new local matrix is $\kappa'_P X_P\kappa_P^{-1}$ by the frame formula. Also the selected lattices and their residue functionals at $T$ are carried by $\gamma,\gamma'$, so the word-prime indicator takes the same value. At $P$ use a source lift of $\kappa_P^{-1}$ and a target lift of $\kappa'_P$. Membership of their conjugates in $J_{i,P}$ and $J_{i+1,P}$ gives the two local test-function laws of `phiAt_source` and `phiAt_target`. For either side the transformed test function multiplied by $\mu_{i,P}(\det r)$ is the original test function multiplied by $\lambda_{j,P}(h^{-1}rh)$, with the determinant unchanged under conjugation. The determinant of a first-parabolic matrix equals that of its original block, because its extra block is upper triangular with diagonal ones.

Use [the finite unfolding calculation](reindexing-the-ordinary-local-unfolding-sum.md) with $x\mapsto x\kappa_P^{-1}$ and then $x\mapsto\kappa'_P x$. The change in the additive character supplies exactly the inverse $\psi_P(n(r))^{-1}$ in the level value. Since the determinants are local units, $\mu_{i,P}$ on them equals the source determinant character $s_{S,P}$. The target determinant character $s_{T,P}$ is inverse to $s_{S,P}$ on units. The resulting two identities give
$$
\Xi_P(\kappa'_P X_P\kappa_P^{-1})
s_{S,P}(\det\kappa_P^{-1})\,s_{T,P}(\det(\kappa'_P)^{-1})
=a'_P a_P^{-1}\Xi_P(X_P).
$$
Taking the product of these equalities gives the scalar hypothesis of [the finite kernel-sum covariance proof](changing-frames-in-the-finite-kernel-sum.md). The theta distribution satisfies its congruence, unitary and determinant laws by `ChTh.Ok`, the lattice points are self-dual, and the preceding period makes the weighted sum independent of representatives. That proof yields covariance with the full frame representations. The ordinary definition of $k_i$ has the weight $\Xi$ just used and the same adjacent distribution, by the equality of the tied character normalizations. Hence it obeys the displayed identity.

### Lean correspondence

- [`ChIdx.Ok`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/FiniteSumNonzeroLargeDepth.lean#L993) specifies the class and local weight hypotheses. [`XiEntry`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/FiniteSumNonzeroLargeDepth.lean#L1116) is the product weight.
- [`passFr` and `redGL_passFr`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GlobalTwisting/RedPEqZeroOfDiv.lean#L502) establish the integral passage between chosen lifts, and [`exists_pass`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/SmulCompSmul.lean#L108) includes the twist components and product character. [`cong_mem_prCat`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/MemParahoricOfTrivialReduction.lean#L225) lifts the principal-congruence error. [`exists_lift`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/XiEntryInvariant.lean#L18) lifts the full move with the prescribed character.
- [`phiAt_source` and `phiAt_target`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/PhiMapsAndOmegaLaw.lean#L819) give the local large-matrix character laws. [`xiAt_left`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsMoveRight.lean#L218) and [`xiAt_right`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsMoveRight.lean#L248) prove their unfolded versions.
- [`xiEntry_invariant`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/XiEntryInvariant.lean#L53) and [`xiEntry_law`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/XiEntryInvariant.lean#L95) check the two scalar inputs. [`matEquiv` and `kAt_equiv`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/XiEntryInvariant.lean#L129) apply them to the ordinary kernel. [`stepC_eq_stepT`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/KernelLocalFactors/ThDistC.lean#L483) identifies the two normalizations.

Status. Source-based reconstruction draft. The local large-matrix character laws are separate inputs to the unfolding argument. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
