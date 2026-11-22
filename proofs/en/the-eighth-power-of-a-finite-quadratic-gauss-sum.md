# The eighth power of a finite quadratic Gauss sum

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $A$ be a finite abelian group written additively. Let $\phi:A\to\mathbb C^\times$ and $b:A\times A\to\mathbb C^\times$ satisfy
$$
\phi(x+y)=\phi(x)\phi(y)b(x,y),\quad
b(x+x',y)=b(x,y)b(x',y),\quad
\phi(kx)=\phi(x)^{k^2}\quad(k\ge0).
$$
The first formula implies that $b$ is symmetric, so also multiplicative in its second argument. Assume first that $b$ is nondegenerate, meaning that $b(x,y)=1$ for every $y$ implies $x=0$. Then
$$
\left(\sum_{x\in A}\phi(x)\right)^8=|A|^4 .
$$
With no nondegeneracy assumption, if the sum is nonzero its eighth power is a positive real. These are the finite Gauss sum statements used in the unitary and triple theta comparisons.

**An inverse phase map.** For any finite abelian group $P$ with a nondegenerate phase $\Phi$ and polarization $B$ satisfying the same identities, suppose there is an additive map $T:P\to P$ such that $\Phi(Tx)=\Phi(x)^{-1}$. Comparing $\Phi(T(x+y))$ gives $B(Tx,Ty)=B(x,y)^{-1}$. Nondegeneracy implies $T$ is injective and hence bijective. For each $x$,
$$
\Phi(x)\sum_y\Phi(y)=\sum_y\Phi(y)B(y,Tx),
$$
by translating $y$ by $Tx$ in the sum and using $\Phi(Tx)=\Phi(x)^{-1}$. Sum over $x$. For $y\ne0$, the character $B(y,Tx)$ is nontrivial by bijectivity and nondegeneracy, so it sums to zero (translate by an element on which it is not $1$). For $y=0$, it sums to $|P|$. Since $\Phi(0)=1$, we obtain $(\sum_{x\in P}\Phi(x))^2=|P|$.

**Four copies supply the map.** Take $P=A^4$, with $\Phi(v)=\prod_i\phi(v_i)$ and $B(v,w)=\prod_i b(v_i,w_i)$. This is nondegenerate because we can test one coordinate at a time. The identity $\phi(-x)=\phi(x)$ follows from $\phi(2x)=\phi(x)^4$, which gives $b(x,x)=\phi(x)^2$, and then from $\phi(x+(-x))=1$. Define the signed permutations
$$
Iv=(-v_1,v_0,-v_3,v_2),\quad
Jv=(-v_2,v_3,v_0,-v_1),\quad
Kv=(-v_3,-v_2,v_1,v_0).
$$
Each preserves $\Phi$. For any $v$, its four images under $1,I,J,K$, including $v$ itself, are pairwise $B$-orthogonal. Indeed the matrices $L^tL'$ for distinct $L,L'$ from $1,I,J,K$ are skew: this is immediate from the quaternion identities $I^2=J^2=K^2=-1$ and $IJ=-JI=K$, and their cyclic versions. For a skew integer matrix $C$, $B(v,Cv)=\prod_{i,j}b(v_i,v_j)^{C_{ij}}=1$ by symmetry and cancellation. This gives the required orthogonality for the four images.

Let $M=|P|$. Lagrange's four-square theorem gives nonnegative integers $a,c,d,e$ with $a^2+c^2+d^2+e^2=M^2-1$. Take $T=a\,1+cI+dJ+eK$. Orthogonality and homogeneity show $\Phi(Tv)=\Phi(v)^{M^2-1}$, and $Mv=0$ gives $\Phi(v)^{M^2}=1$. Hence $T$ inverts the phase. The preceding result gives $(\sum_{v\in P}\Phi(v))^2=M$. Since $\sum_{v\in P}\Phi(v)=(\sum_{x\in A}\phi(x))^4$, this proves the eighth-power formula. [Lagrange's four-square theorem](https://github.com/leanprover-community/mathlib4/blob/master/Mathlib/NumberTheory/SumFourSquares.lean)

**A degenerate phase.** Let $R=\{x:b(x,y)=1\ \forall y\}$ be the radical. If the sum is nonzero, translating it by $r\in R$ multiplies it by $\phi(r)$, so $\phi(r)=1$. Thus $\phi$ and $b$ descend to $A/R$, and the latter is nondegenerate there. The original sum is $|R|$ times the quotient sum. Its eighth power is $|R|^8 |A/R|^4>0$. In particular the normalized nondegenerate Gauss sum, divided by $\sqrt{|A|}$, is an eighth root of unity.

**Lean correspondence.** Orthogonality of the character sum with an inverse phase map is [`sum_sq_of_anti`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/QuadraticSemicharacters/CayleyGaussianIntegrals/GaussSumEighthPower.lean#L79). The four-copy phase and quaternion argument are [`pow4`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/QuadraticSemicharacters/CayleyGaussianIntegrals/GaussSumEighthPower.lean#L134) and [`gaussSumEighthPower`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/QuadraticSemicharacters/CayleyGaussianIntegrals/GaussSumEighthPower.lean#L179). The degenerate statement used on the finite group of triples is [`GaussDegenerate`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/QuadraticSemicharacters/GaussDegenerate.lean#L64).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
