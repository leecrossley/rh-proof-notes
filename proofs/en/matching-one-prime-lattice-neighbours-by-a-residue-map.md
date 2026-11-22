# Matching one-prime lattice neighbours by a residue map

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E$ be the Hermitian field of the chain, with ring of integers $\mathcal O_E$, and let $P$ be a selected prime over a word prime $T$. Assume $T$ is a uniformizer at $P$, $P\ne\overline P$, and $\overline P$ is outside the selected set. At the places of the residue-frame decorations, neither $P$ nor $\overline P$ occurs. These are the hypotheses `MoveHyp` for the source and target ranks, together with the uniformizer property. A decorated lattice $d$ consists here of a self-dual global lattice $N$ and a nonzero linear residue functional $f_Q:N_Q\to k_Q=\mathcal O_E/Q$ at each selected $Q$, together with residue frames away from $P,\overline P$. The functional is given on the localization $N_Q$ and is linear over $\mathcal O_{E,Q}$ through reduction to $k_Q$. Let $d'$ be another such point with lattice $N'$ and functionals $f'_Q$. The ranks may differ.

For a fixed $E$-linear map $x$ between the ambient spaces, call a pair of decorated lattices compatible if $x$ sends each selected source localization into the target localization and preserves its residue functional. Then
$$
\#\{d_1:\ d_1 \text{ is above }d',\ (d,d_1)\text{ is compatible with }x\}
=
\#\{d_0:\ d_0 \text{ is below }d,\ (d_0,d')\text{ is compatible with }x\}.
$$
Both counts are zero or one. The neighbour relations are the following elementary moves at $P$, with the Hermitian correction at $\overline P$.

### The elementary moves

Write $\mathcal O=\mathcal O_{E,P}$, $q=T$, $L=N_P$, $L'=N'_P$, $f=f_P$ and $h=f'_P$. For a decorated localization $(M,F)$, an upper neighbour at $P$ is obtained by choosing $e\in M$ with $F(e)=1$ and taking
$$
M^+=M+\mathcal O q^{-1}e,\qquad
F^+(v)=F(qv)\quad(v\in M^+).
$$
The inclusion $qM^+\subset M$ makes this formula meaningful. Also $F^+(q^{-1}e)=1$, $F^+$ vanishes on $M$, and reduction of the coefficient of $q^{-1}e$ identifies $M^+/M$ with $k_P$. In particular $\ker F^+=M$.

To pass from this local description to the global upper move, start with $A=N+P^{-1}\mathcal O_E e$ for a choice $e\in N$ with the indicated reduction. The global upper lattice in Lean is $A^\# + \overline P A$, where $\#$ denotes the Hermitian dual. Localization of a Hermitian dual at a prime is the dual for the pairing with the localized lattice at the conjugate prime. This follows by writing the pairing against a finite generating set and localizing the resulting integrality conditions. Hence at $P$ this sum gives $N_P+A_P=A_P$. At $\overline P$ it gives $A^\#_{\overline P}$, since $q A_P\subset N_P$ makes $\overline P N_{\overline P}\subseteq A^\#_{\overline P}$. At every other prime the lattice is unchanged. These localizations are dual in pairs, so the global lattice is self-dual. Equality of all localizations gives equality of global lattices, since a nonzero quotient of two distinct lattices is detected at a prime. This also shows uniqueness of the global lattice with these localizations. Every local choice $e\bmod qM$ has a global representative: after expressing $e$ with an integral numerator and a denominator prime to $P$, multiply the numerator by an integer of $\mathcal O_E$ representing the inverse denominator in $k_P$. Changing $e$ by $qM$ preserves $M^+$ and $F^+$.

For a lower neighbour of $(L,f)$, the calculation $\ker F^+=M$ forces the local lattice $L_0=\ker f$. Globally the lower lattice is $B+PB^\#$ with $B=\{v\in N:f(v)=0\}$. At $P$ it is $B_P+PN_P=B_P$, since $qL\subseteq\ker f$. At $\overline P$ the localization is $B^\#_{\overline P}$ and all other localizations are unchanged. The residue functional $f_0$ of the lower neighbour is any linear functional on $L_0/qL_0$ satisfying
$$
f_0(qv)=f(v)\quad(v\in L).
$$
In fact this is precisely the condition for the upper move from $L_0$ to recover $(L,f)$. Choose $e\in L$ with $f(e)=1$. Then $L=L_0+\mathcal O e$, and $qe$ is nonzero in $L_0/qL_0$. A functional on this quotient satisfying $f_0(qe)=1$ obeys the displayed condition, because $qL_0$ is killed. The vector $qe$ can be used to enlarge $L_0$ back to $L$. Both sets of neighbours are finite and nonempty because they are specified by residue vectors or residue functionals over the finite field $k_P$. The functionals at other selected primes and the residue frames outside $P,\overline P$ retain their original values.

### Matching the compatible neighbours

Suppose $(d,d_1)$ is compatible with $x$ and $d_1$ is above $d'$. Choose $e\in L$ with $f(e)=1$. The image $xe$ belongs to the upper lattice at $P$ and has upper functional value one. Thus its class generates the one-dimensional quotient by $L'$. The upper lattice is necessarily $L'+\mathcal O xe$, and its functional has to be $v\mapsto h(qv)$. This determines the compatible upper neighbour uniquely. For $v\in L_0=\ker f$, compatibility implies $xv\in L'$ because the upper functional has kernel $L'$. Define $f_0(v)=h(xv)$ on $L_0$. It is a residue functional and $f_0(qe)=h(qxe)=1$, so it defines a lower neighbour of $d$. The other selected-prime conditions for compatibility stay the same. This gives a lower neighbour with $(d_0,d')$ compatible.

Conversely, suppose $(d_0,d')$ is compatible and $d_0$ is below $d$. The lower lattice is necessarily $L_0$. Its functional is forced by compatibility to be $h\circ x$ there, so the lower neighbour is unique. Taking $e$ as above, $x(qe)$ belongs to $L'$ and $h(x(qe))=1$. Enlarge the target by $q^{-1}x(qe)$ to get the upper neighbour with local lattice $L'+\mathcal O xe$. A global lift of the class of $x(qe)$ in $L'/qL'$ gives the same upper neighbour. Since $L=L_0+\mathcal O e$ and $xL_0\subseteq L'$, the image of $L$ is in this upper lattice. Its new functional on $xv$ is $h(qxv)=f_0(qv)=f(v)$ for every $v\in L$. This verifies compatibility at $P$ and leaves the other conditions intact. The two indicator sums are therefore equal.

Finally a lower move replaces $L$ by $\ker f$ at $P$, of index $\# k_P$. The elementary divisor exponent is one. This can also be seen by choosing a local basis in which $f$ is the reduction of the first coordinate, where the new basis scales that coordinate by one uniformizer. The determinant exponent at every other selected prime is zero because its localization is unchanged.

### Lean correspondence

- [`upA`, `upN`, `Deco.up`, `Deco.dnN` and `Deco.IsUp`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/StdLatUnimodular.lean#L139) give the global moves. [`MoveHyp` and `Deco.Ok.dnN_spec`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/DecoFin.lean#L648) specify the disjoint places and the lower-lattice localizations. [`Deco.IsDn.isUp`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/DecoFin.lean#L1557) recognizes the inverse move from its functional.
- [`above_finite_nonempty` and `below_finite_nonempty`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GlobalTwisting/BelowFiniteNonempty.lean#L126) give the two finite fibres. [`up_at` and `up_f`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/UkTermOfMoveStep.lean#L202) express the inverse lattice relation and the functional.
- [`up_unique`, `dn_unique`, `exists_dn_of_up` and `exists_up_of_dn`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/UkTermOfMoveStep.lean#L256) prove uniqueness and existence on the two sides. [`sum_phiT`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/UkTermOfMoveStep.lean#L374) deduces the equality of the sums of residue indicators.
- [`idxExp_dnN`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/UkTermOfMoveStep.lean#L103) proves the determinant exponent using a rank-one linear modification.

Status. Source-based reconstruction draft. The localization proof describes the global lattice moves by their elementary divisors. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
