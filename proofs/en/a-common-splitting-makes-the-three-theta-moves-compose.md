# A common splitting makes the three theta moves compose

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $\Lambda_1,\Lambda_2,\Lambda_3$ be commensurable full lattices in a finite-dimensional positive definite Hermitian space $V$, each self-dual for $E(x,y)=\operatorname{Im}H(x,y)$. Assume that the same phase $\alpha$ is a $\{\pm1\}$-valued semicharacter on each lattice, so $\alpha(x+y)=\alpha(x)\alpha(y)e^{\pi iE(x,y)}$ for $x,y$ in the same lattice. Suppose there are additive subgroups $A,A'\subset V$ with the following properties.

- $A\cap A'$ is contained in all three lattices.
- Each $\Lambda_i=(\Lambda_i\cap A)+(\Lambda_i\cap A')$.
- If $x,y\in A$, or if $x,y\in A'$, and $x\in\Lambda_i,\ y\in\Lambda_j,\ x+y\in\Lambda_k$ for any $i,j,k$, then $\alpha(x+y)=\alpha(x)\alpha(y)e^{\pi iE(x,y)}$.

Write $I_{ij}$ for the normalized average from $\Lambda_i$ to $\Lambda_j$ of [the triple average formula](three-theta-averages-differ-by-an-eighth-root.md). For every entire $F$ fixed by the normalized translations of $\Lambda_1$, one has
$$
I_{23}I_{12}F=I_{13}F .
\tag{1}
$$
These assumptions follow for every triple of corners of a host square from one common splitting of the family, i.e. the same subgroup and phase conditions for all four period lattices.

### Representatives from each subgroup

If $a\in A,\ b\in A'$ and $a+b\in\Lambda_i$, then $a,b\in\Lambda_i$ separately. Indeed, decompose $a+b=u+v$ with $u\in A\cap\Lambda_i,v\in A'\cap\Lambda_i$. Then $a-u=v-b\in A\cap A'\subset\Lambda_i$. This also proves the same assertion with $\Lambda_i$ replaced by the intersection of any two lattices.

Let $R_2,R'_2$ be representative sets for $\Lambda_2\cap A,\Lambda_2\cap A'$ modulo their respective intersections with $\Lambda_1$. Let $R_3,R'_3$ represent $\Lambda_3\cap A,\Lambda_3\cap A'$ modulo their respective intersections with $\Lambda_2$. These sets are finite, since the quotients inject into quotients of the original commensurable lattices. By the two-subgroup decomposition, the sums $s+s'$ with $s\in R_2,s'\in R'_2$ give representatives for $\Lambda_2/(\Lambda_1\cap\Lambda_2)$. Two such sums are in the same coset only if the differences in $A$ and $A'$ are separately in $\Lambda_1$, by the preceding argument. Thus the $s,s'$ are unique. In the same way, the sums $q+q'$ with $q\in R_3,q'\in R'_3$ represent $\Lambda_3/(\Lambda_2\cap\Lambda_3)$.

### The finite phase is a nonnegative character sum

If $F=0$, (1) is immediate, so assume $F\ne0$. The triple formula says that $I_{23}I_{12}F$ differs from $I_{13}F$ by the scalar
$$
\mu=\sqrt{\frac{n_{13}}{n_{12}n_{23}}}\sum_{\substack{z\in R_3+R'_3,\ y\in R_2+R'_2\\z+y\in\Lambda_1}}\psi(z,y),
\quad
\psi(z,y)=\alpha(z)\alpha(y)\alpha(z+y)e^{-\pi iE(z,y)},\quad
n_{ij}=[\Lambda_j:\Lambda_j\cap\Lambda_i].
$$
It also gives $\mu^8=1$. Substituting $z=q+q'$ and $y=s+s'$, the condition $z+y\in\Lambda_1$ is equivalent to $q+s,q'+s'\in\Lambda_1$ separately. For these pairs, the cross-lattice semicharacter law on $A$ gives $\psi(q,s)=1$. The law on $A'$ gives $\psi(q',s')=1$. By the polarization identity in the triple formula, the complete phase is then just
$$
\psi(q+q',s+s')=\exp\bigl(2\pi iE(s,q')\bigr).
$$
The phase therefore does not depend on $s'$. Fix $s$ and $q$ with $q+s\in\Lambda_1$. For each $q'\in R'_3$, at most one $s'\in R'_2$ gives $q'+s'\in\Lambda_1$. Such an $s'$ exists exactly when $q'$ lies in the subgroup
$$
G=(\Lambda_3\cap A')\cap\bigl(\Lambda_1+(\Lambda_2\cap A')\bigr).
$$
The sign in the sum inside the parenthesis is immaterial as it is a subgroup. Indeed a witness in $\Lambda_2\cap A'$ can be replaced by its representative in $R'_2$, changing the sum only by an element in $\Lambda_1$. Similarly, taking a representative $q'\in R'_3$ of an element of $G$ changes that element by $\Lambda_2\cap\Lambda_3\cap A'$, so membership in $G$ is unchanged.

It follows that the inner sum over $q',s'$ is the sum over $G/(G\cap\Lambda_2)$ of the character $v\mapsto e^{2\pi iE(s,v)}$. The character is well defined since $s\in\Lambda_2$ and the alternating form on $\Lambda_2$ is integral. It sums to the group's order if trivial and to zero otherwise: translating the sum by a point where the character is not $1$ proves the vanishing. Thus every surviving inner sum is a nonnegative real. Summing these inner sums over $q,s$ shows $\mu\ge0$. The eighth-root identity forces $\mu=1$, proving (1).

### The two paths around a square

For a base corner $X=(L,L')$ of a square, put $\Lambda_1=\Lambda_X,\ \Lambda_3=\Lambda_{(M,M')}$, and use successively $\Lambda_2=\Lambda_{(M,L')}$ and $\Lambda_2=\Lambda_{(L,M')}$. The common splitting of the four lattices gives the three hypotheses for each triple and forces both path operators to equal the direct average from $\Lambda_1$ to $\Lambda_3$. This proves the square identity used in [the host equations](square-and-triangle-paths-give-the-host-theta-equations.md).

### Lean correspondence

- [`PolFam`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/SplitTripleEquations/SplitTriOf.lean#L15) gives the common splitting and phase law. [`psiT_one`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/SplitTripleEquations/SplitTriOf.lean#L23) makes the same-side phases $1$, and [`splitTri_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/SplitTripleEquations/SplitTriOf.lean#L39) restricts the family to one triple.
- [`sep`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/SplitTripleEquations/MuOneOfSplit.lean#L22) separates membership by the two subgroups. [`reps_sum`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/SplitTripleEquations/MuOneOfSplit.lean#L37) proves representative uniqueness. [`char_sum`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/SplitTripleEquations/MuOneOfSplit.lean#L75) is the orthogonality argument, and [`mu_one_of_split`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/SplitTripleEquations/MuOneOfSplit.lean#L146) proves the scalar equals $1$.
- [`tripleFormula` and `tripleEighth`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/QuadraticSemicharacters/SelfDualCovolume.lean#L29) supply the composition formula and eighth-root property. [`sqP_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/SplitTripleEquations/EqPOfSplit.lean#L13) compares the two paths around the host square.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
