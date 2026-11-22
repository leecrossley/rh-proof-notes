# The analytic theta sums have a common lattice refinement

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix a column CM field $E$ with ring of integers $\mathcal O$, two ranks $a,b$, and the matrix space $U=\operatorname{Hom}_E(E^a,E^b)$. The complex matrix space $V$ contains one block for each chosen embedding. Send a matrix $x$ to $j(x)$, obtained by applying the chosen embeddings and multiplying by a fixed period $\delta\ne0$. Assume there is at least one block, so $j$ is injective. For the fixed nonzero fractional period ideal $\mathfrak a$, write
$$
L(N,N')=\mathfrak a\,\operatorname{Hom}_{\mathcal O}(N,N')
$$
for the period module of a full self-dual source lattice $N\subset E^a$ and target lattice $N'\subset E^b$. We use the [opposite local orders](self-dual-refinements-control-the-period-lattice-indices.md) $\preceq_S$ for a finite set $S$ of $E$-primes disjoint from its conjugate. Assume $\mathfrak a_P=\mathcal O_P$ for $P\in S$, and put $\varepsilon_Q=1$ on $S$, $-1$ on $\overline S$, and $0$ elsewhere.

Assume the following theta movement data for every self-dual pair in these ranks.

1. The analytic family $e(N,N')$ has a nonzero determinant-character factor $\chi_F(N,N')$. The normalized theta $\theta(N,N')=e(N,N')/\chi_F(N,N')$ is entire and fixed by the normalized translations $W(j(l))$ for $l\in L(N,N')$.
2. The image $j(L(N,N'))$ is self-dual for the imaginary part of the fixed Hermitian form $H$, and the fixed phase $\alpha$ is a semicharacter there. Here $H,\alpha,W$ are as in [the finite intertwiner identity](a-theta-intertwiner-refines-the-weighted-coset-sum.md).
3. When just one of the lattices changes, its new $\theta$ is the intertwiner $\mathcal I_{L_{\rm old}\to L_{\rm new}}$ applied to its old $\theta$, with inverse square root of $[L_{\rm new}:L_{\rm new}\cap L_{\rm old}]$.

These are the `Moves` hypotheses. Let $c_A,c>0$ be integers. For each pair define
$$
H_S(N,N')=\{x\in U:x(N_P)\subseteq N'_P\text{ for all }P\in S\},
\qquad D=c_A^{-1}H_S(N,N'),\qquad C=cH_S(N,N').
$$
Let $\Xi:U\to\mathbb C$ be supported on $D$ and satisfy $\Xi(x+y)=\Xi(x)$ for every $x\in U,y\in C$. This pair of conditions is the box hypothesis for $N,N'$. It will be required for both of the pairs in the comparison. The quotient $D/C$ is finite, since its map into $\prod_{P\in S}c_A^{-1}\operatorname{Hom}(N_P,N'_P)/c\operatorname{Hom}(N_P,N'_P)$ is injective. Write $\Theta_x$ for the induced theta of level $c$ obtained from $e(N,N')$ and a rational lift of $x$, and set
$$
F_{N,N'}(z)=\sum_{x\in D/C}\Xi(x)\chi_F(N,N')^{-1}\Theta_x(z).
\tag{1}
$$
Each term uses a representative of its class. The proof below also shows that the summand is independent of that choice.

Let two source lattices $N_1,N_2$ and two target lattices $N'_1,N'_2$ be self-dual and have identical localizations outside $S\cup\overline S$, in their respective ranks. Suppose $\Xi$ satisfies the box hypothesis for $(N_1,N'_1)$ and for $(N_2,N'_2)$, with the same $c_A,c$. With $o_P$ the determinant order of a local basis and $v_P^{\rm pair}(N,N')=b\,o_P(N)-a\,o_P(N')$, set
$$
\rho=\left(\prod_{P\in S}q_P^{\,v_P^{\rm pair}(N_2,N'_2)-v_P^{\rm pair}(N_1,N'_1)}\right)^{1/2}>0,
\qquad q_P=|\mathcal O/P|.
$$
Then for every $z\in V$,
$$
F_{N_1,N'_1}(z)=\rho F_{N_2,N'_2}(z).
\tag{2}
$$

### The induced theta at a common representative

For one pair write $L=L(N,N')$. Put $A_k=L(N,(N')^{(k,-\varepsilon)})$, $B_k=L(N,(N')^{(k,\varepsilon)})$ for every positive integer $k$. The two are the half-lattices at level $k$; the twist superscripts specify the multiplier $k^{\pm\varepsilon_Q}$ at $Q$. The order is $A_c\preceq_S L\preceq_S B_c$. In particular $L=(L\cap A_c)+(L\cap B_c)$. Every coset of $L/(L\cap B_c)$ has a representative in $L\cap A_c$.

The induced theta is defined using some rational lift $s$ of $x$. Its conditions are $s\in A_k$ for some $k>0$ and $s-x\in C$. Such a lift exists. Choose $k>0$ with $kx\in L$, using fullness. At each $P\in S$, $x\in (A_k)_P=k^{-1}L_P$. Apply the [approximation for full modules](self-dual-refinements-control-the-period-lattice-indices.md#approximation-and-relative-indices) to $A_k\cap B_c$, with the selected set $S$ and vector $x$. The resulting $s$ belongs to $A_k$ at every prime, and $s-x\in(B_c)_P=cL_P$ at every $P\in S$. Hence $s-x\in C$.

Use the [indicator Fourier calculation](the-induced-theta-is-a-finite-period-translate-sum.md#the-fourier-coefficient-and-the-volume-factors), now on the normalized $\theta(N,N')$; the induction is linear in that function. Its inverse-index coefficient is
$$
[L\cap A_c:L\cap A_c\cap B_c]^{-1}
=[L:L\cap B_c]^{-1}.
$$
The equality follows from the decomposition of $L$ just proved. To verify the required Fourier normalization, the source volume is the product, over selected $P$, of the quotient of the two relative indices of $L_P$ and the standard period module at $P$. These are positive finite numbers for full local lattices. The Fourier sum of the indicator at $y\in B_c$ has one surviving representative in $B_c$, from the zero coset. Its phase is $1$ by integrality of the alternating pairing on $j(B_c)$. The inner factor $\mathrm{vol}^{1/2}/[L:L\cap B_c]$ and outer factor $\mathrm{vol}^{-1/2}$ therefore leave precisely this inverse index.

The index $[L:L\cap B_c]$ equals $[B_c:L\cap B_c]$. The two finite quotients pair by $e^{2\pi i\operatorname{Im}H(j(-),j(-))}$. Self-duality of $j(L)$ and $j(B_c)$ makes this pairing nondegenerate on both quotients and well defined. Each finite abelian group injects into the character group of the other, so their cardinalities are equal. Expressing the finite sum as the intertwiner from $L$ to $B_c$ now gives
$$
\chi_F(N,N')^{-1}\Theta_x
=[B_c:L\cap B_c]^{-1/2}\,W(-j(s))\,\theta\bigl(N,(N')^{(c,\varepsilon)}\bigr).
\tag{3}
$$
The new vector in (3) is precisely the one-target movement in hypothesis 3.

Suppose a full period module $G_0=L(G,G')$ for a self-dual pair satisfies $G_0\preceq_S B_c$, and suppose $t\in G_0$, $t-x\in C$. One may use $t$ in place of $s$ on the right of (3), even if $t$ has not been chosen in a first half-lattice. To prove this, use the approximation (over $S$) to $A_k\cap G_0\cap B_c$ on the vector $s$ to obtain $v$. At selected primes $v-s\in (A_k)_P\cap(B_c)_P$, and elsewhere $v$ belongs to all three modules locally. Thus $v\in A_k$. At selected primes, $v-t\in(B_c)_P$ because $v-s$, $s-x$, $t-x$ all lie there. Since $t\in G_0$ and $(B_c)_P\subseteq(G_0)_P$, this also puts $v$ in $(G_0)_P$, hence $v\in G_0$.

Both $v-s$ and $v-t$ are in $B_c$ globally. For the first difference, at $Q\notin S$ both $s,v$ are already in $(B_c)_Q$, since $(A_k)_Q\subseteq(B_c)_Q$. For the second, use $G_0\preceq_S B_c$ off $S$. Now apply the translation law on $j(A_k)$ to $v,s$, and the one on $j(G_0)$ to $v,t$. The theta vector in (3) is fixed by $W(j(B_c))$, so these laws give
$$
W(-j(s))\theta\bigl(N,(N')^{(c,\varepsilon)}\bigr)
=W(-j(v))\theta\bigl(N,(N')^{(c,\varepsilon)}\bigr)
=W(-j(t))\theta\bigl(N,(N')^{(c,\varepsilon)}\bigr).
\tag{4}
$$
This proof compares the phases while using a single self-dual subgroup in each application of the translation law.

### Reducing one box to a common sum

The common-refinement lemma gives a common **successor** $G$ and common **predecessor** $F$ for $N_1,N_2$ under $\preceq_S$. On the target side choose a common predecessor $G'$ for the two negatively twisted targets $(N'_j)^{(c_A,-\varepsilon)}$, and a common successor $F'$ for the two positively twisted targets $(N'_j)^{(c,\varepsilon)}$. All are full self-dual lattices. The conjugate support assumption gives agreement away from $S\cup\overline S$ also for each of the twisted pairs. Because the source argument of $L(-,-)$ is contravariant and the target covariant, for either pair $(N,N')=(N_j,N'_j)$ the following common endpoints work:
$$
G_0=L(G,G')\preceq_S A_{c_A}\preceq_S L\preceq_S B_c
\preceq_S L_1=L(N,F')\preceq_S L_2=L(F,F').
\tag{5}
$$
In particular $B_c$ can be used as the period module in (3), while the sum over $G_0$ uses (4).

For $x\in D$, membership means $x\in(A_{c_A})_P$ for all $P\in S$ since $\mathfrak a_P=\mathcal O_P$. Use approximation with $G_0\cap B_c$ to get $t\in G_0$ with $t-x\in C$: at selected primes $(A_{c_A})_P\subseteq(G_0)_P$ and $t-x\in(B_c)_P\subseteq(G_0)_P$; elsewhere $t\in(G_0)_Q$. This proves $D\subseteq G_0+C$. Also $G_0\cap C=G_0\cap B_c$. At the selected primes, the two conditions are the same by definition of $C$; at other primes $G_0\subseteq B_c$ after localization.

Consequently $D/C$ injects into $G_0/(G_0\cap B_c)$ by assigning $x$ the class of $t$. It is independent of the choice of $t$ just made, and a class outside the image has representatives outside $D$, where $\Xi=0$. The equality $\Xi(t)=\Xi(x)$ holds on the image. Formula (4) shows agreement of the signed translates and gives their independence for different choices of $x$ in its class. Thus (1) becomes
$$
F_{N,N'}=[B_c:B_c\cap L]^{-1/2}\,
  C_{G_0}\bigl(B_c,\theta(N,(N')^{(c,\varepsilon)})\bigr),
\tag{6}
$$
where $C_{G_0}$ is the [weighted coset sum](a-theta-intertwiner-refines-the-weighted-coset-sum.md). The quotient with $G_0$ is finite since the period lattices are full.

Now use the finite intertwiner identity on the triple $G_0,B_c,L_1$, then on the triple $G_0,L_1,L_2$. For each triple the order (5) gives the intersection and decomposition needed in that identity, by (3) of the refinement proof. If $y\in G_0\cap B_c$, then $y\in C$. The same holds when $y\in G_0\cap L_1$, since $(L_1)_P\subseteq(B_c)_P$ on $S$. Hence the periodicity needed for each application is the original periodicity of $\Xi$. The moving vectors are obtained by changing the target in the first step and the source in the second. Therefore (6) becomes
$$
F_{N,N'}=
\bigl([B_c:B_c\cap L]\,[B_c:B_c\cap L_1]\,[L_1:L_1\cap L_2]\bigr)^{-1/2}
 C_{G_0}(L_2,\theta(F,F')) .
\tag{7}
$$
The first index in (7) also equals $[L:L\cap B_c]$. By the index formula for Hom lattices, the three factors telescope in their exponents. Their product equals
$$
\prod_{P\in S}q_P^{\,v_P^{\rm pair}(N,N')-v_P^{\rm pair}(F,F')}.
$$
The function on the right of (7) is common to both pairs, with exactly the same $G_0,F,F',\Xi$. Taking the quotient of the positive scalar normalizations gives (2), regardless of whether the common function vanishes.

### Lean correspondence

- [`vac`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/EmbHInjective.lean#L191) and [`Moves`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/EmbHInjective.lean#L196) give the normalized theta and its hypotheses. [`Amb.IsLift`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/ThDistC.lean#L85) and [`Amb.thInd`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/ThDistC.lean#L90) give the induction.
- [`xiInd_eq_inter`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/XiIndEqInter.lean#L66) evaluates the indicator. [`signed_liftW_eq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SignedLiftWEq.lean#L73) constructs the intermediary in (4). [`thInd_eq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MemMulLatIff.lean#L234) combines this comparison with the target move.
- [`latSum_reindex_of_le_sup`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LatSumReindexOfLeSup.lean#L9) performs the reindexing in (6). [`pair_eq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MemMulLatIff.lean#L291) applies the two finite intertwiners and telescopes the indices. [`core`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MemMulLatIff.lean#L365) constructs common endpoints and concludes (2).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
