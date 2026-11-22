# The terminal hyperplane test has the required two level characters

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

### Statement

Take the field, prime, character and class level data of the sharp true column chain. Fix its length $m\ge2$ and write $j=m-1$. The source dimension of the terminal step is $a=N_j=r+(m-1)t$. The terminal dimension is $N_m=r+mt+1$, and the target of the projected map in this note is the hyperplane of dimension $b=N_m-1=r+mt$. Both enlarged spaces used by this test have zero extra coordinates. At a bad place $P$, let $A=\mathcal O_{E,P}$, let $\kappa$ be its residue field and let $q=|\kappa|$. Write $\Phi_{\rm top}$ for the test on $b$ by $a$ matrices. It is the [sharp type test](the-type-local-test-transforms-by-its-flag-character.md) with $i=m-1$ at a type place, and the [twist test](the-twist-local-test-transforms-by-the-quotient-determinant.md) with cut $r$ at a twist place. Set
$$
\eta_P(d)=
\begin{cases}
\chi_{m-1}(\bar d),&P\text{ a type place},\\
\xi(\bar d)^{-1},&P\text{ a twist place},
\end{cases}
\qquad d\in A^\times .
$$

At the source choose an integral matrix $G$ with integral inverse in the class level at layer $j$. At a type place membership means that $\bar G$ belongs to the prescribed residue subgroup. At a twist place it means that $G$ itself belongs to the prescribed integral subgroup. Let $c_{\rm src}$ be its class level character. Assume the level realization and character agreements in `ChIdx.Ok`, including its identity conjugator at layer $j$, and assume $q$ has valuation one at the type primes as in the prime data. For every $b$ by $a$ matrix $X$,
$$
\Phi_{\rm top}(XG)\eta_P(\det G)=c_{\rm src}\Phi_{\rm top}(X).
$$

At the target assume $q$ has valuation one at $P$. Let $H\in\mathrm{GL}_b(A)$. At a type place require $\bar H$ to belong to the sharp hyperplane residue level `rowTyG`, namely block upper triangular for the initial size $r$ and $m$ blocks of size $t$, with the initial block in the ordered unipotent group `HPsymF`. Let $c_{\rm tgt}$ be its level character, the initial additive character times each of the side-block determinant characters. At a twist place require $\bar H$ to preserve the initial $r$ coordinates, the level `rowTyQ`, and let $c_{\rm tgt}$ be the inverse $\xi$-value of the quotient determinant. Then
$$
\Phi_{\rm top}(HX)\eta_P(\det H)=c_{\rm tgt}\Phi_{\rm top}(X).
$$

### Source level and the disappearance of the extra-coordinate factor

The source ordinary dimension is already its entire enlarged dimension, since $c(j)=m-1-j=0$. Thus in the first-parabolic lifting description the projection to the source original block is the identity. Also the coordinate term `n1Arg`, which is the contribution of the first extra vector, is zero. These are the two simplifications special to this source.

At a type place the residue-level realization gives a projected lift $G_0$ with $\overline{G_0}=\bar G$. Its inverse and $G$ are integral, so $G_0^{-1}G$ is an integral automorphism reducing to the identity. Since $q$ generates the maximal ideal in $A$, that automorphism is the identity modulo $qA$. It preserves the original lattice and satisfies all the flag and column congruences: applied to any lattice vector its difference from the identity lies in $q$ times the reference lattice, which is contained in all the one-step scaled flag lattices. Hence it belongs to the projected level as well. Multiplying with $G_0$ shows $G$ admits the required lift. At a twist place the integral-level realization provides a lift directly. Because the projection is the identity, in both cases the lift on the enlarged space is the same matrix $G$.

The level realization uses the character $\lambda_{j,P}$ of the locally conjugated level group multiplied by the inverse additive character of the extra-coordinate term. At layer $j$ the conjugating matrix is $1$ and that term is $0$, so $c_{\rm src}=\lambda_{j,P}(G)$. Its formula is $\Lambda_{m-1}(\bar G)$ in the type case and the inverse quotient determinant character in the twist case. Applying the source laws for the type and twist tests with the displayed dimensions proves the assertion. The function `rhoS` in the source is exactly $\eta_P$ on units.

### Target level and the identification of its character

For a type place there are no scaling factors or inserted coordinates at the target. The standard chart therefore reduces every entry of $H$ to the corresponding entry of $\bar H$. The initial-residue subgroup imposes the triangular pattern and the extra zero of the [sharp flag calculation](the-type-level-phase-is-multiplicative-on-flag-matrices.md). The outer residue level says the matrix is upper block triangular. Hence all entries below any boundary $r+lt$ in columns before it reduce to zero. Since the entries are integral and $q$ generates the maximal ideal, they belong to $qA$. The same applies to $H^{-1}$ since the residue level is a subgroup. Thus $H$ satisfies the divisibility assumptions of the type target law.

It remains to compare the two expressions for the character. In the reordered flag, the source definition of the initial additive character sums the adjacent entries except at the two cuts, whose second indices are $s$ and $s+k$. It adds the entry from the last index of the first interval to the first index of the third interval, when those indices exist. Undoing the permutation, the terms within each interval are the natural adjacent terms there. The extra entry is the pair with second index $k+s$ in the original order. The pair with second index $k$ is absent. Hence the total is the natural superdiagonal sum with the break at $k$ removed, as in $\Lambda_m$. The determinant of every side block is a unit since the whole residue matrix is invertible and block triangular. The other factors of the level character are $\chi_l$ of those determinants, giving $c_{\rm tgt}=\Lambda_m(\bar H)$. The type target law now proves the desired identity.

For a twist place the lower-left block of $H$ reduces to zero. Its entries are in $qA$, again because $q$ generates the maximal ideal. Each component of $H(x,y)$ for $(x,y)\in A^r\oplus qA^{b-r}$ lies in the corresponding component lattice, by block multiplication. The same reasoning for $H^{-1}$ gives equality of lattices. Thus $H$ belongs to `JQ` in the twist test. The last diagonal block gives exactly the determinant on the residue quotient. The twist target law gives the second identity with the stated $c_{\rm tgt}$.

### Lean correspondence

- [`PhiTop` and `rhoS`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/FiniteSumNonzeroLargeDepth.lean#L1142) define the matrix test and the [determinant factor](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/FiniteSumNonzeroLargeDepth.lean#L1246). [`rank_X'_eq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/RowForms.lean#L184) gives the projected dimension.
- [`of_zero`, `phiTop_source` and `phiTop_level`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/PhiTopSource.lean#L17) remove the extra-coordinate term, apply the matrix law and identify it with the source class character.
- [`chiSymF_val`, `lamPar_val` and `levG_of_HPar`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/PhiTopTargetSym.lean#L35) translate the residue character and subgroup conditions. [`phiTop_target_sym`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/PhiTopTargetSym.lean#L192) gives the target type law.
- [`mem_JQ_of_red`, `lamQB_eq_red` and `phiTop_target_twist`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/PhiTopTargetTwist.lean#L49) give the integral subgroup, its character and the target twist law.

Status. Source-based reconstruction draft. The terminal kernel applies these projected laws together with its [Fourier factor](why-the-terminal-fourier-factor-descends-to-a-coset.md) and principal-level invariance. See the [Lean verification record](../../STATUS.md#lean-verification--lean-核验).
