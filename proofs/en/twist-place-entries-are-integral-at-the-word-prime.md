# Twist-place entries are integral at the word prime

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

### Statement

Fix a word prime $T$ and a coefficient prime $w$ above it. Let $P$ be an auxiliary twist place in the host field $E$ with prime norm $q\ne T$, and put $A=\mathcal O_{E,P}$. Fix the data of the true column chain of length $m\ge2$, with $m_2=m-2$, as in `ChIdx.Ok`. In particular the local phase is a character $\psi:q^{-D}A\to K^\times$ trivial on $A$, $B\ge1$ is the matrix period exponent, and $D\ge 2(m-1)+1$ at twist places. The local determinant normalization scalar `muq` is a unit in $\mathcal O_{K,w}$, as proved in [Hecke character normalizations](hecke-character-normalizations-are-units-away-from-their-prime.md).

On ordinary steps $i<m_2$, let $\Xi_{i,P}$ be the unfolded local function `XiAt` for fixed choices of source and target chart. On the penultimate step $i=m_2$, let $\Psi_P(X,y)$ be `PsiAt`, where $X$ is a matrix between the original dimensions and $y$ is a fixed column in the target space. On the terminal step let $\Omega_P(X,\ell;y)$ be `locTop`, where $X$ is the hyperplane projection, $\ell$ the last row, and the fixed source vector $y$ satisfies $q^M y\in A^a$ with $a$ the source dimension and $D\ge2M$, $B\ge M$. Then each function of the matrix argument takes values in $\mathcal O_{K,w}$ and is invariant under adding $q^B$ times any integral matrix of the same size. This pair of conclusions is the predicate `AwayAt` in the standard local frames.

### The ordinary and penultimate summands

At a twist place the reference lattices in the enlarged source and target are both standard. Let $g$ and $h$ be the respective chart automorphisms for an ordinary step $i$. The box bounds `boundQ` say that $g^{-1}$ sends the standard lattice into itself and $q^{i+1}h$ sends the target standard lattice into itself. For any enlarged matrix $Y$ the normalized factor before unfolding is
$$
\mathcal A(Y)=\mu(\det g)\,\mu(\det h)^{-1}\,
s^{-v(\det g)b+v(\det h)a}\,\Phi_Q(h^{-1}Yg).
$$
Here $a,b$ are the enlarged dimensions, $s^2=q$ in $K$, and $v$ is the exponent function in the local character. The factor $\mu(u)$ is $\operatorname{muq}(i+1,P)^{v(u)}$ times the zero-extended inverse residue character of $u/q^{v(u)}$. The extended residue character and its field inverse both take values either zero or roots of unity. Because `muq` is a $w$-unit, both $\mu$ and its field inverse take integral values at $w$. Also $q$ is a $w$-unit, and $s^2=q$ implies $s$ is a $w$-unit, so any integer power of $s$ is integral there. The test $\Phi_Q$ takes values zero or roots of unity. Thus $\mathcal A(Y)\in\mathcal O_{K,w}$ for every $Y$.

In an ordinary unfolded summand there is also the additive factor $\psi(-\operatorname{chArg}(Y))$. Its argument is the negative of a sum of selected entries between adjacent extra coordinates of $Y$. If $\mathcal A(Y)\ne0$, the matrix $h^{-1}Yg$ is integral by the support of $\Phi_Q$. Therefore
$$
q^{i+1}Y=(q^{i+1}h)(h^{-1}Yg)g^{-1}
$$
is integral by the stated chart bounds. Consequently $q^{i+1}\operatorname{chArg}(Y)$ is integral at $P$. Since $D\ge i+1$, the phase argument is in $q^{-D}A$. Any value of the phase on this group is a root of unity: adding its argument to itself $q^D$ times gives an integral argument, so multiplicativity and triviality on $A$ give the $q^D$th power $1$. The summand is therefore integral at $w$. A summand with $\mathcal A(Y)=0$ also has this property.

The ordinary sum has finite boxes of parameters. Their normalization is a power of $q^{-1}$, a $w$-unit. The other normalization is the inverse relative volume, [integral at $w$ by its prime-power denominator](the-unipotent-volume-denominator-is-a-power-of-the-local-prime.md). Finite sums and products of integral elements are integral, so $\Xi_{i,P}$ has integral values. The penultimate function applies just $\mathcal A$ to the enlarged matrix made by adjoining the column $y$, with no parameter sum and with $h=1$. Thus the same determinant and support calculation proves integrality of $\Psi_P(X,y)$ for all $y$.

For periodicity on these two steps, the exact hypotheses supplied by the chart construction are `xiInv` and `psiInvX`. They assert that the respective functions agree at $X$ and $X+Z$ whenever every entry of $q^{-B}Z$ is in $A$, with the penultimate column held fixed. An integral linear map between the standard lattices has integral matrix entries. Therefore these hypotheses apply to every perturbation by $q^B$ times such a map.

### The terminal product

The projected factor is again $\Phi_Q$, which takes values zero or roots of unity. The last-row Fourier factor vanishes unless $q^M\ell$ has integral entries. On its support, $\ell y$ lies in $q^{-2M}A\subseteq q^{-D}A$, so its phase is a root of unity by the same power argument. The remaining coefficient is $q^{-Ma}$, a unit at $w$. Hence the product is integral at $w$.

If the matrix changes by $q^B Z$ with integral $Z$, its hyperplane entries change by multiples of $q$. This does not change integrality, the lower-block divisibility by $q$, or the determinant character of the reduction. The Fourier row changes by a row in $q^B A^{1\times a}$. In the terminal chain $B\ge M$, so this row pairs integrally with $y$. Both the Fourier support and the phase stay the same. This gives the terminal matrix period.

### Lean correspondence

- [`AwayAt` and `EntryAtQ`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/JetOpIntegral.lean#L25) give the required valuation and matrix period. [`om` and `E1`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/FiniteSumNonzeroLargeDepth.lean#L553) define the normalized factor and finite unfolding. [`depthQ'`, `boundQ`, `xiInv` and `psiInvX`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/FiniteSumNonzeroLargeDepth.lean#L1042) specify the chart bounds and congruence assumptions used here.
- [`val_locChar` and `val_om`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/IntOfHomAt.lean#L33) treat the determinant factors. [`int_of_PhiQ` and `intAt_chArg`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/IntOfHomAt.lean#L66) put the phase argument in its domain. [`entryAtQ`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/IntOfHomAt.lean#L106) assembles the ordinary and penultimate estimates.
- [`valuation_PhiQ`, `psi_pow`, `valuation_ftY` and `ftY_add`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ValuationLeOneOfPow.lean#L36) handle the two terminal factors. [`awayAt_locTop`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/BadPrimeNormPrimeNeLevelPrime.lean#L88) uses these terminal estimates in the comparison at the word prime.

Status. Source-based reconstruction draft. The ordinary and penultimate periodicity invokes the stated chart assumptions `xiInv` and `psiInvX`. The terminal periodicity is proved from the support and phase formulas. See the [Lean verification record](../../STATUS.md#lean-verification--lean-核验).
