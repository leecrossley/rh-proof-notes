# Self-dual refinements control the period-lattice indices

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E$ be the column CM field and $\mathcal O=\mathcal O_E$. Use the standard Hermitian pairing on $E^n$. Let $S$ be a finite set of nonzero prime ideals of $\mathcal O$ with $S\cap\overline S=\varnothing$. For full $\mathcal O$-modules $M,M'$ in a finite-dimensional $E$-space write $M_Q$ for localization at $Q$, and write $M\preceq_S M'$ when
$$
M'_P\subseteq M_P\quad(P\in S),\qquad M_Q\subseteq M'_Q\quad(Q\notin S).
\tag{1}
$$
Here a full module absorbs every vector after multiplication by some positive integer. In particular any full lattice, meaning a finitely generated module spanning the $E$-space, is full. To see this, express the vector in a spanning set from the lattice and clear the denominators of the field coefficients by positive integers. The relation (1) is `Dom` in the source. It reverses the direction of the local inclusion at the selected primes.

### Approximation and relative indices

A vector is in an $\mathcal O$-module $M$ if it lies in all $M_Q$. Indeed if $x\notin M$, the proper ideal of $r\in\mathcal O$ for which $rx\in M$ is contained in some maximal ideal $Q$, which precludes $x\in M_Q$. Localization also preserves intersections: denominators outside $Q$ for two given memberships can be multiplied to give one denominator for both.

For a full module $M$, a vector $x$, and a finite set $S_0$ of primes, choose $d>0$ with $dx\in M$. Choose $a\in\mathcal O$ by the Chinese remainder theorem so that $a-1\in P^{v_P(d)}$ for $P\in S_0$ dividing $d$, and $a\in Q^{v_Q(d)}$ for $Q\mid d$ outside $S_0$. Then $t=ax$ satisfies
$$
t-x\in M_P\quad(P\in S_0),\qquad t\in M_Q\quad(Q\notin S_0).
\tag{2}
$$
At a prime not dividing $d$, $x$ is already in the localization. At a prime dividing $d$, the chosen divisibility makes $(a-1)/d$ or $a/d$, respectively, integral there. This proves the approximation used below. Intersections of finitely many full modules are full because their denominators can be multiplied.

If $B\preceq_S L_1\preceq_S L_2$, then $B\cap L_2\subseteq L_1$, by the $L_2$-inclusion at selected primes and the $B$-inclusion elsewhere. Moreover
$$
L_1=(L_1\cap B)+(L_1\cap L_2).
\tag{3}
$$
For $x\in L_1$, use (2) for $B\cap L_1\cap L_2$ and $S_0=S$. At $P\in S$, $x$ is in $B_P$ and $(L_1)_P$, so $t$ is in both; also $x-t\in(L_2)_P$. At $Q\notin S$, $t$ is in the three local modules, while $x\in(L_2)_Q$, giving $x-t\in(L_2)_Q$. Thus $t\in L_1\cap B$ and $x-t\in L_1\cap L_2$, proving (3).

For full modules $L_1\preceq_S L_2$, the natural map
$$
L_1/(L_1\cap L_2)\longrightarrow
\prod_{P\in S}(L_1)_P/(L_2)_P
\tag{4}
$$
is an isomorphism. Injectivity follows from local membership at all primes and the inclusion outside $S$. For surjectivity, take a representative $x_P\in(L_1)_P$ of the prescribed $P$-component. Use (2) with $S_0=\{P\}$ and module $L_1\cap L_2$ to get $t_P$ with $t_P-x_P\in(L_2)_P$ and all its other localizations in $L_1\cap L_2$. In particular $t_P\in L_1$. The sum $\sum_{P\in S}t_P$ maps to the prescribed tuple. For lattices the right-hand quotients are finite, so (4) computes the index as their product.

### A common refinement with its conjugate constraints

Put $\varepsilon_Q=1$ for $Q\in S$, $\varepsilon_Q=-1$ for $\bar Q\in S$, and $\varepsilon_Q=0$ otherwise. For a full lattice $M$ and positive integer $c$, let $M^{(c,\pm\varepsilon)}$ be the lattice with localizations $c^{\pm\varepsilon_Q}M_Q$. It can be defined by imposing these conditions at all primes. The resulting module lies between $cM$ and $c^{-1}M$, so it spans and is finitely generated. These conditions give the stated localizations: to recover a vector in the prescribed module at $Q$, multiply it by an element outside $Q$ clearing the finitely many other conditions. Such an element is obtained by taking at each of those primes a sufficiently high power of an element of that prime outside $Q$, then multiplying. Only finitely many conditions need clearing, because the vector is in $M$ up to an integer denominator and only primes dividing $c$ change the conditions.

Suppose $M$ is self-dual for the standard Hermitian form. The Hermitian dual at $Q$ is obtained by testing against the lattice at $\bar Q$, with conjugation of the latter's coordinates. The dual of $c^{\pm\varepsilon_{\bar Q}}M_{\bar Q}$, computed at $Q$, is $c^{\mp\varepsilon_{\bar Q}}M_Q=c^{\pm\varepsilon_Q}M_Q$. Hence both twists remain self-dual. This uses $S\cap\overline S=\varnothing$.

Now let $M_1,M_2$ be self-dual of the same rank and agree at every prime outside $S\cup\overline S$. Take $d>0$ with $dM_2\subset M_1$ and $dM_1\subset M_2$, by clearing denominators for a finite generating set in each direction. Then
$$
M_j\preceq_S F,\quad G\preceq_S M_j\quad(j=1,2),
\qquad F=M_2^{(d,\varepsilon)},\quad G=M_2^{(d,-\varepsilon)} .
\tag{5}
$$
At a selected prime this follows from the two inclusions just chosen. At its conjugate the roles of $d$ and $d^{-1}$ exchange, giving exactly the opposite inclusions required by (1). Away from both, the localizations are equal. The same argument with $M_1=M_2$ gives $M^{(c,-\varepsilon)}\preceq_S M\preceq_S M^{(c,\varepsilon)}$.

### The index on the linear maps

For lattices $N\subset E^a,N'\subset E^b$, let $L(N,N')=\mathfrak a\,\operatorname{Hom}_{\mathcal O}(N,N')$, viewed in $\operatorname{Hom}_E(E^a,E^b)$, where $\mathfrak a$ is the nonzero fractional ideal of period scalars. At $P$, localization of this module gives the local Hom lattice times $\mathfrak a_P$. For one inclusion, localize the globally integral maps. For the other, clear denominators outside $P$ for the images of a finite set of generators of $N$, using that an image is in $N'_P$ exactly when such a denominator sends it into $N'$. A nonzero scalar in $\mathfrak a$ times the Hom lattice already spans, by clearing denominators against those same generators, so the period lattice is full. It is finitely generated, for evaluation on the generators embeds the Hom lattice into a finite direct sum of copies of $N'$.

This description gives contravariance in $N$, covariance in $N'$, and commutation with twisting $N'$ by the local scalar $c^{\pm\varepsilon_Q}$. In particular $N_2\preceq_S N_1$ and $N'_1\preceq_S N'_2$ imply $L(N_1,N'_1)\preceq_S L(N_2,N'_2)$. At $P\in S$, where $\mathfrak a_P=\mathcal O_P$, choose local bases $B_P,B'_P$ for $N,N'$. The period lattice consists of the matrices $B'_P Y B_P^{-1}$ with $Y$ integral. Left multiplication acts on the $a$ columns, and right multiplication on the $b$ rows. Thus the determinant order of this lattice in the matrix space is
$$
a\,v_P(\det B'_P)-b\,v_P(\det B_P)=-v_P^{\rm pair}(N,N'),
\qquad
v_P^{\rm pair}(N,N')=b\,o_P(N)-a\,o_P(N').
$$
For an inclusion of local full lattices the quotient size is $q_P$ to the difference of their determinant orders, with the smaller lattice's order first. Indeed the elementary divisors of the smaller lattice in a basis of the larger are powers of a uniformizer, and their exponents add to the determinant order of the change of basis. Here $q_P=|\mathcal O/P|$. Combining this with (4), for $L_j=L(N_j,N'_j)$ with $L_1\preceq_S L_2$,
$$
[L_1:L_1\cap L_2]=\prod_{P\in S}q_P^{\,v_P^{\rm pair}(N_1,N'_1)-v_P^{\rm pair}(N_2,N'_2)}.
\tag{6}
$$
All factors are positive, and the sign in (6) follows from the minus sign in the determinant order of the Hom lattice.

### Lean correspondence

- [`Dom`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/EmbHInjective.lean#L17) fixes the order (1). [`Full.approx`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/EmbHInjective.lean#L103) gives (2). The intersection and sum conclusions are [`Dom.inf_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MemMulLatIff.lean#L44) and [`Dom.le_sup`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MemMulLatIff.lean#L51). The localization map in (4) is [`relIndex_eq_prod_locP`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/RelIndexEqProdLocP.lean#L10).
- [`isSdLat_twO`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/IsSdLatTwOExpS.lean#L54) gives the conjugate-dual calculation for a scalar twist, and [`common_refinement`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsNatMulIntegral.lean#L116) uses it to prove (5).
- [`perO_components`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/PerOComponents.lean#L155) computes the localized period lattice, and [`twO_perO`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SmulMemLocPPerO.lean#L35) commutes the twist with it. [`det_chg`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/CrdSurjective.lean#L58) computes the determinant on the matrix space. [`relIndex_homAt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/CrdSurjective.lean#L102) gives the local index, and [`idx_formula`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MemMulLatIff.lean#L143) proves (6).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
