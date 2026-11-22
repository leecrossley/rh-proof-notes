# A hyperplane companion pays one residue factor per source column

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E$ be the CM coefficient field with its conjugation and the standard Hermitian pairing. Fix a nonzero $\pi\in\mathcal O_E$ with $(\pi)$ coprime to $(\bar\pi)$, and a self-dual target lattice $N'\subset E^b$. At each prime $P\mid\pi$, take a nonzero residue-linear functional $f_P$ of the localized target lattice, and let $L\subseteq N'$ be the lattice satisfying all those kernel conditions. Thus $L_P=\ker f_P$ for $P\mid\pi$ and $L_Q=N'_Q$ elsewhere. There exists a self-dual target lattice $N''$ satisfying
$$
\pi N'\subseteq N'',\qquad \bar\pi N''\subseteq N',\qquad N''_P=L_P\quad(P\mid\pi).
$$
With the word-prime hypotheses below, changing $N'$ to this $N''$ has the following finite index bound on the period lattices:
$$
[M:M\cap M'']\;\mid\;p^{fa},\qquad f=\#\{P:P\mid\pi\}.
$$
Here $\pi\bar\pi=p$, every $P\mid\pi$ has norm $p$, $N\subset E^a$ is a self-dual source lattice standard at these primes, $M=\operatorname{per}(N,N')$ and $M''=\operatorname{per}(N,N'')$. The period lattice is the lattice of homomorphisms carrying source into target, multiplied by the fixed nonzero period ideal. This ideal is finitely generated and locally the unit ideal at each $P\mid\pi$.

### Construction of the companion

Since $f_P$ is defined modulo $P$ and $\pi\in P$, one has $\pi N'\subseteq L\subseteq N'$. Write $L^\sharp$ for its Hermitian dual. Set $N''=L+\pi L^\sharp$. Hermitian duality reverses inclusions, conjugates the scalar in a homothety, and commutes with localization after conjugating the relevant prime. Thus at $P\mid\pi$, $L^\sharp_P=N'_P$ since $L_{\bar P}=N'_{\bar P}$. Hence $N''_P=L_P$. At a conjugate prime $\bar P\mid\bar\pi$, $\pi$ is a unit and $L_{\bar P}=N'_{\bar P}\subseteq L^\sharp_{\bar P}$, so $N''_{\bar P}=L^\sharp_{\bar P}$. Elsewhere both lattices equal the unimodular $N'$ locally. It follows place by place that $N''=(N'')^\sharp$. These are lattices since they lie between two nonzero scalar multiples of $N'$. The first inclusion follows from $\pi N'\subseteq L$; the second follows from $\bar\pi L\subseteq N'$ and $\bar\pi L^\sharp\subseteq N'$, the latter by dualizing $\pi N'\subseteq L$.

### The period index

At each $P\mid\pi$, the unit period ideal means that $x\in M$ acts locally as a lattice homomorphism. The standard source basis vectors $e_1,\ldots,e_a$ are integral directions at that place. Define the additive map
$$
M\longrightarrow\prod_{P\mid\pi}(\mathcal O_E/P)^a,\qquad x\longmapsto(f_P(xe_i))_{P,i}.
$$
For $x$ in its kernel, $x e_i$ lies in $N''_P$ for every $i$ at every such $P$, so $x$ is in $M''_P$. At every other prime $\pi$ is a unit and the inclusion $\pi N'\subseteq N''$ gives $\pi x\in M''$. Thus $x\in M''$ after checking local membership everywhere. The kernel is contained in $M\cap M''$. Its index in $M$ equals the size of the image, which divides the size $p^{fa}$ of the target group. This proves the claimed divisibility. It is the index used in the normalization of the selected-side theta moment sum.

### Lean correspondence

- [`companion_gen`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MomentCompanion.lean#L7) gives the self-dual sum construction and the local inclusions.
- [`relIndex_per_dvd`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/RelIndexPerDvd.lean#L91) uses the finite reduction map, with [`mem_localization_perO`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/RelIndexPerDvd.lean#L46) for membership in the localized period lattice.
- [`chi_move`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/RelDetCompanion.lean#L258) computes the character change for this companion, an additional input to the moment sum.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
