# Determinants stay in the Hecke ring without division by integers

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E5%9C%A8%E4%B8%8D%E9%99%A4%E4%BB%A5%E6%95%B4%E6%95%B0%E6%97%B6%E6%8A%8A%E7%9F%A9%E9%98%B5%E8%A1%8C%E5%88%97%E5%BC%8F%E7%95%99%E5%9C%A8Hecke%E7%8E%AF.md)

**Proposition.** Let $R$ be commutative, $S\subseteq R$ a unital subring, $\rho:G\to\mathrm{GL}_d(R)$ a representation, and $A$ the $S$-span of $\rho(G)$. Assume $\det(1-z\rho(g))\in S[z]$ for every $g$. Then $\det(\sum_{i=1}^m u_i a_i)\in S[u_1,\ldots,u_m]$ for all $m\ge0$, $a_i\in A$. For every square matrix $\Theta$ over $A$, its expanded block determinant lies in $S$.

First let $M$ be a sum of terms $a z^n\rho(g)$ with $a\in S$, $n\ge1$. Work modulo $z^{N+1}$ for arbitrary $N$. Choose a term $B=a z^n\rho(g)$ of lowest remaining degree and let $C=M-B$. The finite inverse of $1-B$ gives
$$
1-M=(1-B)\left(1-\sum_{k=0}^N B^kC\right).
$$
The first determinant belongs to $S[z]$ by substitution. In the second, $k=0$ retains the existing terms of $C$, and $k\ge1$ gives new terms of degree strictly greater than $n$ with coefficients in $S$ and matrices from $\rho(G)$. Thus we can eliminate all terms of the current lowest degree, then proceed to higher degrees. Only finitely many steps remain modulo $z^{N+1}$ because each fixed degree is reached after finitely many operations and no terms are added there during its elimination. The determinant modulo $z^{N+1}$ is a product of polynomials over $S$. Arbitrary $N$ gives $\det(1-M)\in S[z]$.

Apply this after adjoining the variables $u_i$ to both rings, with $M=z\sum_i u_i a_i$. Its $z^d$ coefficient is $(-1)^d\det(\sum_i u_i a_i)$. It follows also that every coefficient of the determinant of one $d\times d$ series in $A[[z]]$ belongs to $S$, by applying the result to finite truncations and substituting powers of $z$ for the variables.

Now consider a block matrix of series with coefficients in $A$ and identity constant term. Split off the first block row and column, writing the matrix as $\begin{pmatrix}U&B\\ C&D\end{pmatrix}$. Since $U(0)=1$, all coefficients of $U^{-1}$ lie in $A$ by the series inverse recursion. Block elimination of determinant one gives determinant $\det U\cdot\det(D-CU^{-1}B)$. The second matrix still has identity constant term and coefficients in $A$. Induction on the number of blocks and the single-block result give all coefficients in $S$. For $1-z\Theta_{\rm big}$ take the highest coefficient, up to sign $\det\Theta_{\rm big}$. The corner polynomial $\det(Te_B-X_0+(1-e_B))$ uses the single-block result over $S[T]\subset R[T]$.

## Lean correspondence

- `alg_identity`, `stepD` and `core` eliminate terms by degree, and `det_poly_statement` gives the multivariable statement. [Factorization](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/TruncatedSeriesCounting/TruncatedSeriesProofs/LemmaDetPoly.lean#L107) · [Polynomial result](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/TruncatedSeriesCounting/TruncatedSeriesProofs/LemmaDetPoly.lean#L393)
- `detGood`, `invGood`, `schur` and `blockDet` give the formal series argument. `blockPolyT` and `eta_determinant_comparison` apply it. [Block determinant](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CharacterColumnKernels/IdempotentNormalForms/IsUnitDetOfConst.lean#L447) · [Corner polynomial](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/RamifiedBlockRings/RamifiedBlockProofs/CMemPolyT.lean#L114) · [Relations](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/TruncatedSeriesCounting/TruncatedSeriesProofs/BridgeDet.lean#L9)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
