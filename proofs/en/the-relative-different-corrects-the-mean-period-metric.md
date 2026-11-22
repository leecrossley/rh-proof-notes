# The relative different corrects the mean period metric

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Let $K$ be an imaginary quadratic field of discriminant $-d<-4$, with its fixed embedding in $\mathbb C$, and let $E/K$ be a CM extension of degree $f$. Write $\overline{\,\cdot\,}$ for the CM involution of $E$ and $\mathfrak D$ for the different of $E/K$. Take a nonzero integral ideal $\mathfrak b\subset\mathcal O_E$ with $\mathfrak D=\mathfrak b\overline{\mathfrak b}$. Put $I=\mathfrak b^{-1}$, and put $rd_E=|\operatorname{disc}(E)|^{1/[E:\mathbb Q]}$. Let $\Lambda$ be the CM ideal lattice normalized to discriminant one. Let $M\subset\mathbb C$ be a number field containing the images of all $f$ embeddings $\tau:E\hookrightarrow\mathbb C$ extending the fixed embedding of $K$, and the Weierstrass invariants of $\Lambda$. Let $d_M=[M:\mathbb Q]$ and $A_\rho=\operatorname{area}(\Lambda_\rho)>0$, where $\Lambda_\rho$ has the invariants obtained by applying $\rho:M\hookrightarrow\mathbb C$.

In $M^f$, let $P_I$ be the $\mathcal O_M$-span of all vectors $(\tau(a))_\tau$ with $a\in I$. At each label $\tau$, let $\ell_\tau(M)=\{x\in M:x e_\tau\in P_I\}$, where $e_\tau$ is the coordinate vector. This is the integral eigenline in the split CM coordinates. For $s\in\ell_\tau(M)\setminus\{0\}$, define its corrected mean metric by
$$
 \mathcal P_\tau(M)=\frac{2\log[\ell_\tau(M):\mathcal O_M s]
       -\sum_\rho\log(\pi|\rho(s)|^2/A_\rho)}{d_M}.
$$
Then this expression is independent of $s$ and of $\tau$, and
$$
 \mathcal P_\tau(M)=
 \gamma_{\!E}+\log\frac{2\pi}{rd_E}
       -\frac{L'(1,\chi_K)}{L(1,\chi_K)}.
\tag{1}
$$
Suppose $c_\tau\in M$ lies in a number field $M_0$ containing all the same embedded copies of $E$, and $c_\tau$ generates $\ell_\tau(M_0)$ over $\mathcal O_{M_0}$. Then $c_\tau\ne0$, it also generates $\ell_\tau(M)$, and its negative metric has mean (1) without an index correction. The common field $M$ need not contain $M_0$. This is the period input of [the infinite-place kernel-chain estimate](the-scalar-theta-mean-enters-the-kernel-chain-at-every-place.md). [Mean period theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/DivisorProofs/MeanLogPeriodChowlaSelberg.lean#L59) · [Generator statement `mean_logMet_eq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/DivisorProofs/MeanLogMetricGeneratorEqMeanPeriod.lean#L45) · [Integral line and corrected metric](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/GeneralLinearActions/IsDiscriminantTwelfthRootOfIdealLattice.lean#L149)

## Proof

### The integral eigenline

Fix the indicated embedding $K\subset M$. Over $M$ the map $a\otimes z\mapsto(\tau(a)z)_\tau$ identifies $E\otimes_K M$ with $M^f$. Indeed $E/K$ is finite separable and the minimal polynomial of a primitive element has distinct linear factors in $M$. Under this identification the relative trace pairing $(a,b)\mapsto\operatorname{Tr}_{E/K}(ab)$ extends to the dot product $\sum_\tau x_\tau y_\tau$. No complex conjugation enters that pairing.

For a nonzero fractional ideal $I$ of $E$, its dual over $\mathcal O_K$ under relative trace is $I^\vee=(I\mathfrak D)^{-1}$. To verify this, a trace test $\operatorname{Tr}_{E/K}(bI)\subseteq\mathcal O_K$ gives $\operatorname{Tr}_{E/K}(ba\mathcal O_E)\subseteq\mathcal O_K$ for every $a\in I$ because $I$ is an $\mathcal O_E$-module. Hence $bI\subseteq\mathfrak D^{-1}$, by the definition of the inverse different. That containment also implies the trace test, and invertibility of $I$ gives the formula. The $\mathcal O_K$-modules $I$ and $\mathcal O_M$ are finite torsion-free over a Dedekind domain, hence projective and flat. Extension of scalars identifies the trace-dual module with the dual of the extended lattice. For example, localize $\mathcal O_K$ at every prime and choose a basis of $I$ and its trace-dual basis. Those bases exhibit this identity after extension and localization. Thus $P_I$ is exactly the dot-product dual of the $\mathcal O_M$-span of the vectors $(\tau(b))_\tau$ for $b\in I^\vee$. The equivalence $x e_\tau\in P_I$ if and only if $x\tau(b)\in\mathcal O_M$ for every $b\in I^\vee$ follows, and inverting the extended fractional ideal gives
$$
 \ell_\tau(M)=\tau(I\mathfrak D)\mathcal O_M.
\tag{2}
$$
In particular this line has positive rank over $\mathcal O_M$. [Different and dual ideal](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/GL3/CubicFields/DifferentIdeal/CoeIdealDifferentNeZero.lean#L14) · [Coordinate line `lineR_eq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/GL3/CubicFields/DifferentIdeal/CoeIdealDifferentNeZero.lean#L25)

### The fractional-ideal index and its logarithm

Put $J=I\mathfrak D$. If $s\ne0$ lies in the line, then by (2), $(s)\subseteq\tau(J)\mathcal O_M$, and
$$
 [\ell_\tau(M):\mathcal O_M s]
  =\frac{|N_{M/\mathbb Q}(s)|}{N_{E/\mathbb Q}(J)^{[M:\tau(E)]}}.
\tag{3}
$$
Here $N(J)>0$ is the absolute fractional-ideal norm. To see (3), multiply the two fractional ideals by a common positive integer to make them integral. The additive index is the ratio of the two absolute norms of the integral ideals, with the common scaling canceling. The extension norm $N_M(\tau(J)\mathcal O_M)=N_E(J)^{[M:\tau(E)]}$ follows prime by prime from $\sum_{w\mid\mathfrak p}e(w/\mathfrak p)f(w/\mathfrak p)=[M:\tau(E)]$. The numerator for $(s)$ is the absolute field norm. Raising (3) to $[E:\mathbb Q]$ gives the index identity of the Lean proof. [Index identity `index_lineR`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/GL3/CubicFields/DifferentIdeal/CoeIdealDifferentNeZero.lean#L62) · [Mean from index `br_meanLogOm_eq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/GL3/CubicFields/PeriodRelations/Period.lean#L39)

Every embedding $\rho$ has $\rho(s)\ne0$. Summing $2\log|\rho(s)|$ gives $2\log|N_{M/\mathbb Q}(s)|$. It cancels the norm of $s$ contributed by $2\log[\ell_\tau(M):\mathcal O_M s]$ in (3). Consequently
$$
 \mathcal P_\tau(M)=\frac{1}{d_M}\sum_\rho\log(A_\rho/\pi)
       -\frac{2}{[E:\mathbb Q]}\log N_E(J).
\tag{4}
$$
The first term is the mean for the elliptic lattice. In the host case $J=\mathfrak b^{-1}\mathfrak D=\overline{\mathfrak b}$, so $N_E(J)^2=N_E(\mathfrak D)$. By the discriminant tower formula,
$$
 |\operatorname{disc}(E)|=d^{[E:K]}N_E(\mathfrak D),
 \qquad
 \frac{2}{[E:\mathbb Q]}\log N_E(J)=\log rd_E-\log\sqrt d.
\tag{5}
$$
The mean of $\log A_\rho$ is
$$
 \gamma_{\!E}+\log(2\pi^2/\sqrt d)-L'(1,\chi_K)/L(1,\chi_K)
$$
by [the CM class mean of the normalized period area](the-cm-class-mean-of-the-normalized-period-area.md). Subtracting $\log\pi$ in (4) and then the term in (5) yields (1). [Discriminant normalization `two_log_brN`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/DivisorProofs/MeanLogPeriodChowlaSelberg.lean#L19) · [Mean period `meanPeriodAt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/DivisorProofs/MeanLogPeriodChowlaSelberg.lean#L59)

### Passing a chosen generator to the field of the theta coefficients

By (2), upon extending $M_0$ to the compositum $MM_0$, the equality $\ell_\tau(M_0)=\mathcal O_{M_0}c_\tau$ gives $\ell_\tau(MM_0)=\mathcal O_{MM_0}c_\tau$. The line is nonzero, so $c_\tau\ne0$. Membership $c_\tau\in\ell_\tau(M)$ can be checked by $c_\tau\tau(I^\vee)\subseteq\mathcal O_M$, using the trace-dual test. This test holds because the products are algebraic integers in the compositum and belong to $M$. For any $x\in\ell_\tau(M)$, its image in the compositum is in the extended line, so $x/c_\tau\in\mathcal O_{MM_0}$. As $x/c_\tau\in M$, it is in $\mathcal O_M$. Thus the line over $M$ is generated by $c_\tau$. Its index over $\mathcal O_M c_\tau$ is $1$, and (1) is the mean of
$$
       -\log(\pi|\rho(c_\tau)|^2/A_\rho)
$$
as claimed. [Generator transfer `ellT_eq_span`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/DivisorProofs/MeanLogMetricGeneratorEqMeanPeriod.lean#L12) · [Use of the generator mean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/DivisorProofs/MeanLogMetricGeneratorEqMeanPeriodStatement.lean#L7)

## Source and verification

The eigenline identification, norm and discriminant calculation, and transfer of the chosen generators were checked against the pinned source. The CM class mean is supplied by the linked proof. The host conditions supply $\mathfrak b$ and the hypothesis on $c_\tau$ supplies a generator over an initial coefficient field. This calculation then identifies its metric over the common field used in the kernel chain. No Lean replay or axiom check was performed for this note.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
