# The split-prime part of the Heisenberg cosets

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## The split lattice calculation

Let $p$ be an odd prime not dividing the discriminant of the quadratic CM field. Let $E$ be the host CM field, and let $\pi,\bar\pi\in\mathcal O_E$ come from the quadratic field with $\pi\bar\pi=p$. They are coprime. In fact writing $\pi=(x+y\sqrt{-d})/2$ with integers $x,y$ gives $x^2+dy^2=4p$. If $p\mid x$, the assumptions imply $p\mid y$, which would give $p^2\mid4p$. Thus $\pi+\bar\pi=x$ is coprime to $p=\pi\bar\pi$, proving coprimality of the two factors in $\mathcal O_E$.

Let $M$ be the full arithmetic period lattice in the homomorphism space. Its image under the complex embedding of the matrix entries, including the common nonzero period factor, is a full lattice $\Lambda\subset\mathbb C^n$, with $n=fab$ for source and target ranks $a,b$ and $f$ CM embeddings. The embeddings give the same complex values on $\pi,\bar\pi$, so scalar multiplication by either acts on every complex coordinate by this value. For $c=p c'$ with $c'>0$ and $p\nmid c'$, let $B$ be the image of the twisted period lattice whose localization at $P$ is $c^{e_P}M_P$, where $e_P=1$ on $S$, $-1$ on its conjugate, and zero elsewhere. The sets $S,\bar S$ are disjoint. At places over $p$, $S$ contains exactly the places dividing $\bar\pi$. The subgroup appearing below consists of cosets with representatives in $B$, taken modulo the intersection with $\Lambda$.

Consider
$$
B[p]=\{y\in B:py\in\Lambda\}.
$$
On the arithmetic lattice, a vector in this set belongs at each $P$ to the intersection $c^{e_P}M_P\cap p^{-1}M_P$. At $P\mid\bar\pi$ this is $pM_P=\bar\pi M_P$, since $\pi,c'$ are units. At $P\mid\pi$ it is $p^{-1}M_P=\pi^{-1}M_P$. At $P\nmid p$, the intersection is contained in $M_P$. These three computations imply $B[p]\subset(\bar\pi/\pi)\Lambda$, using the characterization of a full lattice by its localizations.

Conversely for any $y\in(\bar\pi/\pi)\Lambda$, choose integers $u,k$ with $u c'+k p=1$. At places over $p$, $u c'y$ has the required localization just computed. At places away from $p$ it lies in $M_P$, and multiplication by $c'$ ensures inclusion in $c M_P$ at the places in $S$ away from $p$, where $p$ is a unit. At the remaining places it satisfies the weaker inclusions $M_P\subseteq c^{-1}M_P$ or $M_P\subseteq M_P$. Also $p(\bar\pi/\pi)=\bar\pi^2$, so $pu c'y\in\Lambda$. We have $y-u c'y= k p y\in\bar\pi\Lambda$. Finally
$$
(\bar\pi/\pi)\Lambda\cap\Lambda=\bar\pi\Lambda.
$$
For example, if both $z$ and $(\pi/\bar\pi)z$ are integral in the module, a Bézout relation $r\pi+s\bar\pi=1$ expresses $z/\bar\pi=r(\pi/\bar\pi)z+sz$ in it. The quotient of $B[p]$ by $B[p]\cap\Lambda$ is therefore represented by the same representatives as $(\bar\pi/\pi)\Lambda/\bar\pi\Lambda$.

Multiplication by $\pi/\bar\pi$ identifies this quotient with $\Lambda/\pi\Lambda$. Since $\Lambda$ has real dimension $2n$, the index is the real determinant of scalar multiplication, $|\pi|^{2n}=p^n$. This computes the order of the $p$-part of the finite Heisenberg quotient.

## The other part and the normalization

Every element of $B/(B\cap\Lambda)$ is killed by $p c'$, by the defining local powers of $c$. Bézout expresses this finite group as the direct sum of its $p$-killed and $c'$-killed parts. Let $S_2,S_1$ be their representative sets in $B$, respectively. Because multiplication by $c'$ kills the second group, Cauchy's theorem implies that the order $h=|S_1|$ is prime to $p$. It follows that
$$
[B:B\cap\Lambda]=h p^n.
\tag{1}
$$

In the Heisenberg formula the volume normalization counts the classes in $(\Lambda\cap A)/(B\cap\Lambda\cap A)$, where $A$ is the other lattice of the split level. The split Heisenberg hypotheses used here give self-duality of $B$ for the alternating form $e$, integrality of $e$ on $\Lambda$, and the following separation. If $y\in B$ satisfies $e(x,y)\in\mathbb Z$ for every $x\in\Lambda\cap A$, then $y\in\Lambda$. The two finite groups pair by
$$
(x,y)\longmapsto \exp(2\pi i e(x,y)).
$$
It is well defined by integrality and self-duality, and separates the nonzero classes in the two groups. For the first group this follows from self-duality of $B$; for the second use the stated separation. The sum of a nontrivial character over either group is zero, since translating it by an element where the character differs from one multiplies the sum by that character value. Counting the double character sum in both orders leaves precisely the size of the other group in each order. Therefore their sizes agree. In particular the normalizing number of cosets in the induced theta function is the same $h p^n$ as in (1).

## Lean correspondence

- [`killIn`, the representatives and their hypotheses](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/AlgebraicTheory/DefsKer.lean#L9) defines both killed parts.
- [`p_torsion_represents_quotient`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/AlgebraicTheory/AlgebraicTheoryProofs/KerHalf.lean#L367) gives the first quotient comparison, including the coprimality of the two prime factors.
- [`index_product_formula`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/AlgebraicTheory/AlgebraicTheoryProofs/LinearSubstitutionDiagonal.lean#L162) evaluates the index by the scalar determinant. [`representatives_split`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/AlgebraicTheory/AlgebraicTheoryProofs/LinearSubstitutionDiagonal.lean#L257) splits the representative sets and removes $p$ from $h$.
- [`card_SA_SB`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/AlgebraicTheory/AlgebraicTheoryProofs/CardTwoSidedQuotient.lean#L91) uses the character pairing to compare the two indices, with [`card_two_sided_quotient`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/AlgebraicTheory/AlgebraicTheoryProofs/CardTwoSidedQuotient.lean#L220) applying it to the actual induced kernel.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
