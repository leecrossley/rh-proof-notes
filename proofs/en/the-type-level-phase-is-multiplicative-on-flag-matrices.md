# The type-level phase is multiplicative on flag matrices

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

### Statement

Let $\kappa$ and $K$ be fields, $\psi:(\kappa,+)\to K^\times$ an additive character in multiplicative notation, and $\chi_j:\kappa^\times\to K^\times$ multiplicative characters for $j\ge 0$. Extend each $\chi_j$ to $\chi_{j,0}:\kappa\to K$ by setting $\chi_{j,0}(0)=0$. Fix nonnegative integers $k,s,r$ with $k+s\le r$, a positive block size $t$, and a matrix size $a$ with $a\ge r$.

Number the indices from $0$ to $a-1$. On the initial indices $0,\ldots,r-1$ use the order obtained by listing the three intervals $[k,k+s)$, $[0,k)$, $[k+s,r)$ in that order and keeping the natural order within each. Require that a matrix $A$ have these properties:

- The first $r$ columns have zero entries below the initial $r$ rows. Their initial square is upper triangular in the specified order, with all diagonal entries $1$.
- If $k+s<r$, the entries $A_{p,k+s}$ for $p<k$ vanish as well.
- The part on the remaining indices is upper block triangular in consecutive blocks of size $t$, with a possibly incomplete final block.

These are the conditions called `Pat`. The earlier order can be ordinary, taking $k=r$ and $s=0$. For $r+jt\le a$, write $B_l(A)$ for the square block of size $t$ beginning at $r+lt$, and define
$$
\Lambda_j(A)
=\psi\!\left(\sum_{\substack{0\le p,\ p+1<r\\p+1\ne k}} A_{p,p+1}\right)
 \prod_{l=0}^{j-1}\chi_{l,0}\bigl(\det B_l(A)\bigr).
$$
If $A,B$ obey the conditions at size $a$, then $AB$ obeys them and
$$
\Lambda_j(AB)=\Lambda_j(A)\Lambda_j(B).
$$
The additive part of this law is the same for every $j$. No invertibility hypothesis is needed on the side blocks, since their characters have been extended by zero.

### Proof

The zero rectangle under the first $r$ columns stays zero on multiplication. In the initial square, order the rows and columns as specified. The product of the two upper triangular squares is upper triangular with diagonal entries $1$. We check the extra prescribed zeros in column $q=k+s$ when $q<r$. For a row $p<k$, a nonzero term $A_{pu}B_{uq}$ would require $u$ between $p$ and $q$ in the specified order, inclusive. The entire portion of the order from $p$ up to but excluding $q$ lies in $[0,k)$. For such $u$ the factor $B_{uq}$ vanishes by the extra condition. At $u=q$ the factor $A_{pq}$ vanishes. Thus the required zero persists.

On the remaining blocks, every summand for an entry below a block diagonal must have a zero factor. An intermediate index in the first $r$ columns gives a zero in the first factor. An intermediate index in a later block can contribute only when its block is weakly later than the output row block and weakly earlier than the input column block, which is impossible strictly below the block diagonal. For an entry in a diagonal block, the same reasoning leaves exactly the intermediate indices within that block. Consequently
$$
B_l(AB)=B_l(A)B_l(B)
$$
for each full block. Determinants multiply, and so do their extended character values: a product of two field elements is zero exactly when one factor is zero. This handles the whole determinant product.

For the additive part consider any $p$ with $0\le p$, $p+1<r$ and $p+1\ne k$. We claim
$$
(AB)_{p,p+1}=A_{p,p+1}+B_{p,p+1}.
$$
If the two adjacent indices in the natural order are within the same listed interval, they are consecutive in the specified order too. Only the intermediate indices $p,p+1$ can then contribute, and each diagonal entry is $1$. There is one other possible transition with $p+1\ne k$: for $s>0$, $p=k+s-1$ lies at the end of the first listed interval and $p+1=k+s$ starts the third. The indices between them in the specified order all lie in $[0,k)$. Their contributions vanish by the extra condition in column $k+s$. Again the only contributions come from $p,p+1$. Thus the sum inside $\psi$ is additive under matrix multiplication. The additive character turns this sum into a product, proving the claimed formula.

### Lean correspondence

- [`symIdx`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/LevGSym.lean#L11) gives the order. [`Zs` and `Pat`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/PhiMapsAndOmegaLaw.lean#L72) give its vanishing conditions.
- [`Pat.mul`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/PhiMapsAndOmegaLaw.lean#L105) proves preservation of the conditions. [`Pat.superdiag` and `Pat.block`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/PhiMapsAndOmegaLaw.lean#L137) give the entry addition and block determinant multiplication.
- [`ext0` and `matrixExtendByZero_mul`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/PhiMapsAndOmegaLaw.lean#L164) define the extended characters and prove multiplicativity. [`lamF` and `Pat.lamF_mul`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/PhiMapsAndOmegaLaw.lean#L187) give the combined formula.

Status. Source-based reconstruction draft. This is the residue-field calculation for the type part of the local kernel. See the [Lean verification record](../../STATUS.md#lean-verification--lean-核验).
